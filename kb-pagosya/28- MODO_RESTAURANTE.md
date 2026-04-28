# Modo Restaurante — PagosYa

## Visão Geral

O **Modo Restaurante** é um módulo adicional pago que se ativa por cima de qualquer plano existente do PagosYa (EmprendeYa, ExpandeYa ou ConquistaYa). Ele transforma o POS padrão em um sistema completo para negócios de alimentação: restaurantes, cafeterias, bares, hamburgueiras, pizzarias, padarias e food trucks.

Funciona tanto na **versão web** quanto no **app Android nativo**.

---

## Licenciamento e Preços

| Tipo | Valor | Observação |
|---|---|---|
| Trial | Grátis | 15 dias, 1 por usuário, sem cartão |
| Mensal | Bs 79/mês | Renovação automática |
| Anual | Bs 790/ano | Equivale a Bs 65,8/mês — economia de 17% |

**Regras do trial:**
- Apenas 1 trial por usuário (anti-abuso via RPC `activate_restaurant_trial`)
- Dados, recetas e insumos são mantidos mesmo após expirar — não são apagados
- Após expirar, o módulo desativa mas o histórico permanece

**Ativação de licença paga:**
- Acionada via webhook após confirmação de pagamento
- RPC `activate_restaurant_license` registra plano, data de início, data de expiração e transaction ID
- Status possíveis: `trial`, `active`, `expired`, `cancelled`

**Tabela de controle:** `restaurant_licenses`

---

## Acesso e Navegação

- Menu lateral (sidebar): ícone de chef (`ChefHat`) → rota `/restaurante`
- **Com licença ativa (trial ou paga):** exibe diretamente a página de configuração (`ThermalPrinterConfig`)
- **Sem licença (none, expired, cancelled):** exibe a landing page informativa com os planos e botão de trial
- O card "Restaurante" que existia em **Configuraciones Avanzadas** foi removido — toda a gestão passa pelo menu lateral dedicado

---

## Funcionalidades

### 1. Ativação e Tipo de Operação

O proprietário escolhe como o negócio opera:

| Tipo | Descrição | Ideal para |
|---|---|---|
| **Servicio en Mesa** | Garçom salva comanda no POS e envia itens para produção por estação | Restaurantes com atendimento de mesa |
| **Atención en Caja** | Fluxo normal de venda com opção de enviar para produção após cobrar | Lanchonetes, padarias, fast-food |

**Configuração:**
- Toggle "Modo Restaurante" liga/desliga o módulo no POS
- Seleção de tipo de operação via botões visuais
- Armazenado localmente com `Capacitor Preferences` (chave: `restaurant_mode_config_v1`)
- Quando desativado, o POS volta ao fluxo normal sem nenhuma alteração visual ou de dados

---

### 2. Estações de Produção

Define os pontos físicos de impressão dentro do estabelecimento. Exemplos: **Cocina**, **Bar**, **Postres**, **Caja**.

**Atributos de cada estação:**
- Nome livre (ex: "Cocina Caliente", "Bar 1")
- Tipo de conexão:
  - `bluetooth` — impressora via Bluetooth (somente Android)
  - `tcp_ip` — impressora de rede Wi-Fi/IP com host e porta (padrão: 9100) (somente Android)
  - `browser` — diálogo de impressão do navegador (web)
- Largura do papel: `58mm` ou `80mm`

**Comportamento por plataforma:**

| Recurso | Web | Android |
|---|---|---|
| Criar/editar estações | ✅ | ✅ |
| Impressão por Bluetooth | ❌ | ✅ |
| Impressão por Wi-Fi/IP | ❌ | ✅ |
| Impressão via navegador | ✅ | — |
| Teste de conexão direto | ❌ | ✅ |

**Armazenamento:** `Capacitor Preferences` (chave: `saved_production_printer_stations_v1`)

**Formato do ticket de produção:**
- Cabeçalho: nome da estação em destaque
- Mesa/comanda, garçom responsável, data e hora
- Lista de itens com quantidade
- Observações gerais e por item
- Texto monoespaçado com wrap automático (58mm = 30 chars, 80mm = 42 chars)

---

### 3. Impressora de Recibos (Android)

Separada das estações de produção, usada para o recibo final do cliente e relatórios de turno.

- Configurada via scan Bluetooth
- Armazenada com chave `saved_thermal_printer`
- Largura de papel configurável: 58mm ou 80mm
- Botão de impressão de teste disponível

---

### 4. Comandas Digitais no POS

Ao usar o modo restaurante, o fluxo do POS é expandido com o `SaveOrderModal`:

**Fluxo com Servicio en Mesa:**
1. Garçom adiciona itens ao carrinho
2. Clica em "Guardar" → abre o modal de comanda
3. Define nome da comanda: "Mesa 02", "Juan", "Pedido #5"
4. Adiciona observações gerais (ex: "alergia a frutos secos")
5. Seleciona estação de destino (Cocina, Bar, etc.)
6. Seleciona quais itens enviar agora (checkboxes por item)
7. Adiciona observação específica para este envio (ex: "sin hielo, urgente")
8. Clica em "Enviar a Producción" → imprime o ticket na estação
9. A comanda fica aberta para novos itens ou fechamento posterior

**Envio incremental:**
- Cada item rastreia `sent_to_station_qty` (quantidade já enviada acumulada)
- Itens com `quantidade > sent_to_station_qty` aparecem como "pendentes"
- Garçom pode enviar parte agora, outros depois
- Diferentes itens da mesma comanda podem ir para estações diferentes

**Exemplo prático:**
> Mesa pede 2 cervejas + 3 pratos. Garçom envia as cervejas para o Bar e os pratos para a Cocina. Cliente adiciona mais 1 cerveja. Garçom reabre a comanda, vê 1 cerveja pendente e envia só ela para o Bar.

---

### 5. Gestão de Insumos (Ingredientes)

Controle completo de estoque de matéria-prima:

**Cadastro por insumo:**
- Nome, categoria/tags
- Unidade base: `g`, `kg`, `ml`, `l`, `unidad`
- Estoque atual e estoque mínimo
- Custo unitário base (calculado automaticamente via média ponderada)
- Status ativo/inativo

**Registro de compras:**
- Quantidade comprada + custo total da compra
- Cálculo automático de **custo médio ponderado**:
  ```
  novoCustoUnit = (stockAtual × custoAtual + custoTotalCompra) / (stockAtual + qtdComprada)
  ```
- Normalização automática de unidades (kg → g, l → ml)
- Registra movimento de "entrada" com origem "compra"

**Histórico de movimentos (`restaurant_ingredient_movements`):**

| Tipo | Origem | Gerado quando |
|---|---|---|
| `entrada` | `compra` | Registro de compra manual |
| `salida` | `venta` | Venda fechada (desconto automático por receita) |
| `salida` | `receta` | Consumo via receita |
| `ajuste` | `ajuste_manual` | Correção manual de estoque |

Cada movimento registra: quem criou, quando, motivo, quantidade, custo unitário, custo total e `reference_id` (ex: ID da venda).

**Tabela principal:** `restaurant_ingredients`

---

### 6. Fichas Técnicas (Receitas)

Define os insumos necessários para preparar cada produto:

**Por receita:**
- Vinculada a um produto (`product_id`) e loja (`tienda_id`)
- Array de linhas, cada uma com:
  - Insumo, quantidade usada, unidade, notas técnicas, ordem de exibição
  - Custo calculado por linha: `quantidade × costo_unitario_base do insumo`

**Cálculo automático de rentabilidade:**
- Custo total de produção = soma dos custos das linhas da receita
- Margem bruta = `preço de venda − custo de produção`
- Margem % = `(preço − custo) / preço × 100`
- Quando o custo de um insumo muda (nova compra), os cálculos atualizam automaticamente

**Onde aparece:** Aba de produtos (`/products`) quando modo restaurante está ativo — exibe coluna extra com custo, lucro e margem por produto.

**Tabela principal:** `restaurant_product_recipes`

---

### 7. Alertas de Estoque Baixo

Sistema de notificações automáticas:

- Acionado quando: `stock_atual <= stock_minimo`
- Destinatários: proprietário + todos os funcionários ativos da loja
- Tipo de notificação no sistema: `stock_alert`, ícone ⚠️, link para `/products`
- Campos ativados no insumo: `low_stock_alert_active = true`, `low_stock_notified_at = now()`
- Quando estoque volta acima do mínimo: alerta é desativado automaticamente

---

### 8. Sistema de Autoatendimento (Tablet/PWA)

Tela pública de self-service em qualquer tablet ou monitor touchscreen.

**Rota:** `/autoatencion/:tiendaId` (pública, sem autenticação)

#### Fluxo do cliente:
1. **Portada** — banners promocionais em carrossel, categorias e produtos destacados
2. **Catálogo** — navegação por categoria, busca por nome
3. **Carrinho** — quantidades, total, botão de pagamento
4. **QR de pagamento** — aguarda confirmação via Supabase Realtime (BNB ou Red Enlace)
5. **Sucesso** — exibe número do pedido ("Pedido #12, pase al mostrador")
6. **Falha** — opção de tentar novamente ou cancelar

#### Configurações pelo proprietário:

**Identidade visual:**
- Logo personalizado (PNG transparente, recomendado 600×180 px)
- Cor primária e secundária (hex) para botões e acentos
- Ocultar/exibir branding "Impulsado por PagosYa"
- Mensagem final pós-pagamento personalizada

**Catálogo:**
- Por produto: visível/oculto no tablet, destaque na portada, ordem de exibição
- Operações em massa: "ativar todos", "desativar todos"
- Ordem das categorias configurável

**Banners publicitários:**
- Imagem (recomendado 1600×1000 px, relação 16:10), título e subtítulo opcionais
- Rotação automática a cada 5 segundos quando há mais de 1 banner
- Upload via Supabase Storage em `autoatencion-assets/{tiendaId}/`

**Impressão:**
- `customer_printer_id` — ticket do cliente (mostrador/caja)
- `kitchen_printer_id`, `bar_printer_id`, `dessert_printer_id` — estações por setor
- Reutiliza as estações já configuradas em Estações de Produção

**Operação:**
- Timeout configurável (minutos): cancela pedido sem pagamento automaticamente
- PIN de 4–8 dígitos para sair do modo quiosque (5 toques no logo para acionar)

**Tabelas:** `restaurant_autoatencion_settings`, `restaurant_autoatencion_catalog`, `restaurant_autoatencion_banners`

---

### 9. Auditoria de Comandas

- Comanda registra `employee_id` / `employee_name` — quem atendeu a mesa
- Venda final registra quem fechou a conta (`closed_by`)
- Recibo e cupão mostram "Atendido por"
- Cada envio para produção fica registrado com estação, itens e observação

---

## Arquitetura Técnica

### Arquivos principais

| Arquivo | Responsabilidade |
|---|---|
| `pages/RestaurantePage.tsx` | Rota `/restaurante` — verifica licença e decide o que renderizar |
| `pages/RestauranteLandingPage.tsx` | Landing page informativa com planos e botão de trial |
| `components/printer/ThermalPrinterConfig.tsx` | Configuração completa: modo, tipo operação, estações, impressoras |
| `components/printer/AutoatencionSettingsSection.tsx` | Configuração do autoatendimento (dentro do ThermalPrinterConfig) |
| `pages/AutoatencionPage.tsx` | Interface pública do tablet (sem autenticação) |
| `components/pos/SaveOrderModal.tsx` | Modal de comanda no POS com envio a produção |
| `services/restaurantModeService.ts` | Leitura/escrita da configuração do modo restaurante |
| `services/printerStationService.ts` | CRUD de estações de produção (Preferences) |
| `services/productionPrinterService.ts` | Formatação e envio de tickets para impressoras |
| `services/restaurantIngredientsService.ts` | CRUD de insumos, compras, movimentos |

### Tabelas no banco de dados

| Tabela | Uso |
|---|---|
| `restaurant_licenses` | Licenciamento (trial, mensal, anual) |
| `restaurant_ingredients` | Cadastro de insumos com estoque |
| `restaurant_ingredient_movements` | Histórico de movimentos de estoque |
| `restaurant_product_recipes` | Fichas técnicas dos produtos |
| `restaurant_autoatencion_settings` | Configurações visuais e operacionais do tablet |
| `restaurant_autoatencion_catalog` | Produtos visíveis/destaque no tablet |
| `restaurant_autoatencion_banners` | Banners promocionais do tablet |

### RPCs disponíveis

| Função | Quem chama | O que faz |
|---|---|---|
| `activate_restaurant_trial(p_user_id)` | Frontend autenticado | Ativa 15 dias de trial (1 por usuário) |
| `activate_restaurant_license(p_user_id, p_plan_type, p_payment_transaction_id)` | Webhook de pagamento | Ativa licença paga mensal ou anual |

### Armazenamento local (Capacitor Preferences)

| Chave | Conteúdo |
|---|---|
| `restaurant_mode_config_v1` | `{ enabled, operationType }` |
| `saved_production_printer_stations_v1` | Array de estações de produção |
| `saved_thermal_printer` | Impressora de recibos (Android) |

---

## Compatibilidade por Plataforma

| Funcionalidade | Web | Android App |
|---|---|---|
| Ativar modo restaurante | ✅ | ✅ |
| Configurar tipo de operação | ✅ | ✅ |
| Estações de produção | ✅ | ✅ |
| Impressão por Bluetooth | ❌ | ✅ |
| Impressão por Wi-Fi/IP | ❌ | ✅ |
| Impressão via navegador | ✅ | — |
| Teste direto de impressora | ❌ | ✅ |
| Gestão de insumos | ✅ | ✅ |
| Fichas técnicas | ✅ | ✅ |
| Comandas no POS | ✅ | ✅ |
| Autoatendimento tablet | ✅ | ✅ |
| Alertas de estoque | ✅ | ✅ |
| Banners publicitários | ✅ | ✅ |

---

## Fluxo de Ativação (Passo a Passo)

### Para o cliente final:
1. Acessa `/restaurante` no menu lateral
2. Vê a landing page com os benefícios e planos
3. Clica em **"Probar 15 Días Gratis"** (ou escolhe um plano pago)
4. Sistema ativa a licença via RPC `activate_restaurant_trial`
5. A página atualiza automaticamente e exibe a tela de configuração

### Configuração inicial recomendada:
1. Ativar o toggle "Modo Restaurante"
2. Escolher o tipo de operação (Mesa ou Caja)
3. Criar as estações de produção (ex: "Cocina", "Bar")
4. (Android) Vincular impressora Bluetooth ou IP a cada estação
5. Cadastrar insumos
6. Criar receitas para os produtos
7. (Opcional) Configurar o tablet de autoatendimento

---

## Perguntas Frequentes (FAQ)

**O Modo Restaurante substitui o plano atual?**
Não. É um módulo adicional que se soma ao plano existente. O cliente mantém todos os recursos do plano e ganha os recursos de restaurante.

**O que acontece quando o trial expira?**
O modo restaurante desativa no POS. Os dados (insumos, receitas, histórico) são mantidos e ficam acessíveis quando o cliente adquirir um plano.

**Precisa de impressora física?**
Não obrigatoriamente. Na web, os tickets abrem pelo diálogo de impressão do sistema. No Android, é possível imprimir via Bluetooth ou rede, mas a operação funciona sem impressora — os tickets podem ser visualizados na tela.

**Quantas estações posso criar?**
Ilimitadas. Não há restrição técnica no número de estações.

**O autoatendimento funciona sem internet?**
Não. O pagamento QR e a confirmação dependem de conexão em tempo real via Supabase Realtime.

**O tablet precisa ter login no PagosYa?**
Não. A rota `/autoatencion/:tiendaId` é pública. O tablet funciona como quiosque independente sem autenticação.

**Posso usar em mais de uma loja?**
A licença está vinculada ao usuário (owner). Cada loja configurada sob o mesmo owner pode usar o modo restaurante.

**O que é o PIN de saída do tablet?**
É um código de 4–8 dígitos que o operador precisa digitar para sair do modo quiosque no tablet de autoatendimento. É acionado tocando 5 vezes no logo. Evita que clientes saiam acidentalmente da tela de pedidos.

---

## Segmento de Clientes Ideal

| Tipo de negócio | Funcionalidades mais relevantes |
|---|---|
| Restaurante com mesas | Comandas, envio incremental, Cocina + Bar |
| Cafeteria / Café | Autoatendimento tablet, Cocina, fichas técnicas |
| Bar | Estação Bar, comandas por mesa, insumos de bebidas |
| Fast food / Hamburgueria | Atención en Caja, autoatendimento, Cocina |
| Pizzaria | Cocina, fichas técnicas com insumos (massa, recheio) |
| Padaria | Atención en Caja, insumos, fichas técnicas |
| Food truck | Atención en Caja, estação única, sem impressora física (web) |

---

## Proposta de Valor

> **Controle total da cozinha, da mesa ao custo — em um único sistema.**

Sem sistemas paralelos. Sem integrações complicadas. O garçom já usa o POS do PagosYa para vender; agora a cozinha também recebe os pedidos pelo mesmo sistema, os insumos são controlados automaticamente e o cliente pode pedir sozinho pelo tablet.

**15 dias grátis, sem cartão, sem compromiso.**
