# WhatsApp CRM — Documentação Completa de Funcionalidades
> **Uso:** Material de referência para criação de Landing Page

---

## 🎯 O QUE É O WHATSAPP CRM?

O **WhatsApp CRM** é uma plataforma completa de gestão de relacionamento com clientes via WhatsApp. Em vez de usar o WhatsApp normal, sua equipe opera a partir de uma bandeja compartilhada com histórico, automações, IA e relatórios — tudo em um só lugar.

**Para quem é:**
- Negócios que recebem muitas mensagens no WhatsApp
- Equipes com múltiplos atendentes em um mesmo número
- Empreendedores que querem automatizar respostas e promoções
- Empresas que precisam rastrear pipeline de vendas via mensagens

**Resultado esperado:**
- Atender mais clientes com menos esforço
- Nunca perder uma mensagem sem resposta
- Enviar campanhas em massa sem risco de ban
- Automatizar respostas 24/7 com ou sem IA

---

## 📦 MÓDULOS DO SISTEMA

### 1. 💬 Chat em Tempo Real — Bandeja Compartilhada

**Para que serve:**  
Central de atendimento onde toda a equipe vê e responde mensagens de um único número WhatsApp.

**Como funciona:**  
- Todos os contatos aparecem numa lista única, com preview da última mensagem
- Badge de mensagens não lidas em cada conversa
- Ao clicar em um contato, abre o histórico completo da conversa
- Qualquer atendente pode responder — fica registrado quem respondeu
- Suporta texto, imagens, vídeos, áudios, documentos, stickers e localização
- URLs de mídia do WhatsApp expiram automaticamente → o sistema detecta e recarrega

**Diferenciais:**
- ✅ Atribuição de contatos a atendentes específicos
- ✅ Status de leitura visível (✓ enviado · ✓✓ entregue · ✓✓ lido)
- ✅ Busca de contatos por nome, telefone ou e-mail (com debounce)
- ✅ Suporte a grupos do WhatsApp
- ✅ Histórico persistido em banco de dados — nunca se perde

---

### 2. 🏷️ Etiquetas e Filtros de Contatos

**Para que serve:**  
Organizar contatos por categorias visuais (leads quentes, VIPs, suporte, pagamento pendente, etc.) para localizar e filtrar rapidamente.

**Como funciona:**  
- Criar etiqueta com nome e cor (10 cores disponíveis)
- Aplicar uma ou várias etiquetas a cada contato
- Filtrar a lista de conversas por etiqueta
- Ver distribuição de etiquetas no dashboard de métricas

**Diferenciais:**
- ✅ 10 cores pré-definidas e customizáveis
- ✅ Múltiplas etiquetas por contato
- ✅ Filtro instantâneo na bandeja
- ✅ Dashboard de distribuição por etiqueta nas métricas

---

### 3. 🗂️ Pipeline Kanban de Vendas

**Para que serve:**  
Visualizar em que etapa do funil de vendas cada contato está — do primeiro contato até o fechamento.

**Como funciona:**  
- Colunas padrão: Lead → Negociação → Proposta → Ganho / Perdido
- Cada card representa um contato com resumo de dados CRM
- Arraste e solte o card para mover entre etapas
- Acesso ao histórico de conversas direto do card
- Visão de valor total de deals ativos no pipeline

**Diferenciais:**
- ✅ Drag & drop intuitivo
- ✅ Valor monetário por deal trackado
- ✅ Integração direta com o chat (abrir conversa do kanban)
- ✅ Visível no dashboard de métricas (total deals + valor)

---

### 4. 👤 CRM de Contatos

**Para que serve:**  
Armazenar e visualizar dados completos de cada cliente além do telefone: empresa, cargo, e-mail, cidade, país, produtos de interesse, etc.

**Como funciona:**  
- Painel lateral no chat com todos os dados CRM do contato
- Campos: nome, empresa, e-mail, cargo, cidade, país, telefone, produtos, notas
- Dados usados automaticamente para substituir variáveis em templates e respostas rápidas
- Histórico de atribuições a atendentes

**Diferenciais:**
- ✅ Dados integrados ao envio de templates (sem copiar/colar)
- ✅ Histórico de deals associados ao contato
- ✅ Atualização automática ao importar CSV

---

### 5. 📤 Envio em Massa (Bulk Send) — Anti-Ban

**Para que serve:**  
Enviar uma mensagem para centenas de contatos de forma segura, simulando comportamento humano para não ser banido pelo WhatsApp.

**Como funciona:**  
**Passo 1 — Selecionar destinatários:**
- Modo **Individual**: selecione contatos com checkbox
- Modo **Grupos**: expanda grupos e selecione membros
- Modo **Importar**: faça upload de CSV/TXT com lista de números

**Passo 2 — Escolher mensagem:**
- Buscar nas Respostas Rápidas salvas
- Preview com substituição de variáveis (`{{nombre}}`, `{{empresa}}`, etc.)

**Passo 3 — Confirmar e enviar:**
- Valida números no WhatsApp antes de enviar
- Acompanha progresso em tempo real
- Pausa ou cancela a qualquer momento

**Proteção Anti-Ban (distribuição assimétrica):**
| Cenário | Probabilidade | Delay |
|---------|--------------|-------|
| Ritmo normal (lendo rápido) | 60% das msgs | 8 – 20 segundos |
| Pausa média (lendo com atenção) | 30% das msgs | 20 – 35 segundos |
| Micro-pausa (distraído) | 10% das msgs | 35 – 45 segundos |
| Pausa de lote | A cada 10 msgs | 3 minutos |

**Limites e capacidades:**
- 🛡️ **200 mensagens/dia** — limite seguro para contas estabelecidas
- ⏱️ **~20 segundos** de média por envio (comportamento humano simulado)
- 📦 **Exemplo:** 100 contatos = ~35-40 minutos de envio seguro
- 💾 **Jobs sobrevivem ao recarregamento** da página — salvos no navegador
- 🔁 **Variáveis dinâmicas** substituídas por dados reais de cada contato

---

### 6. ⚡ Respostas Rápidas

**Para que serve:**  
Criar uma biblioteca de mensagens predefinidas com atalhos (ex: `/ola`, `/preco`, `/horario`) para responder clientes em segundos.

**Como funciona:**  
- Criar resposta com nome, atalho (`/comando`) e categoria
- Adicionar conteúdo: texto, imagem, vídeo, áudio, documento ou sticker
- Usar variáveis para personalizar (`{{nombre}}`, `{{empresa}}`, etc.)
- Usar digitando `/` no chat ou selecionando ao criar envio em massa

**Funcionalidades:**
- ✅ 6 categorias organizadoras (texto, multimídia, docs, pagamentos, interativo, todos)
- ✅ Suporte a 10 tipos de conteúdo (text, image, video, audio, document, sticker, contact, location, buttons, list)
- ✅ Upload de arquivos até **16MB**
- ✅ **12 variáveis built-in** + variáveis customizadas
- ✅ Duplicar resposta existente para criar variações
- ✅ Ativar/desativar sem deletar
- ✅ Busca instantânea por nome ou conteúdo

**Variáveis disponíveis:**  
`{{nombre}}` · `{{telefono}}` · `{{empresa}}` · `{{email}}` · `{{ciudad}}` · `{{pais}}` · `{{cargo}}` · `{{producto}}` · `{{agente}}` · `{{fecha}}` · `{{hora}}` · `{{tienda}}`

---

### 7. 📋 Templates com Variáveis CRM

**Para que serve:**  
Criar mensagens profissionais que preenchem automaticamente dados do cliente (empresa, cargo, produto) ao enviar.

**Como funciona:**  
- Criar template com nome, categoria e conteúdo com variáveis
- Ao usar: selecionar contato → sistema busca dados CRM → substitui variáveis → envia
- Contador de uso registra quantas vezes cada template foi enviado

**Categorias:**  
Geral · Vendas · Suporte · Marketing · Follow-up · Saudação · Notificação

**Funcionalidades:**
- ✅ **12 variáveis built-in** + ilimitadas customizadas
- ✅ Variáveis custom em formato `snake_case` auto-formatado
- ✅ Marcar favoritos para destaque
- ✅ Suporte a imagem, vídeo e documento com legenda
- ✅ Rastreamento de uso por template
- ✅ Envio direto ao contato a partir do template

---

### 8. 📅 Agendamento de Mensagens

**Para que serve:**  
Programar mensagens para serem enviadas em data e hora específica — inclusive com recorrência automática.

**Como funciona:**  
- Escolher contato ou grupo
- Definir data e hora do envio
- Configurar recorrência (opcional): Diária, Semanal ou Mensal
- O sistema verifica a cada 60 segundos e envia no momento certo

**Funcionalidades:**
- ✅ **3 tipos de recorrência**: diário, semanal, mensal
- ✅ Data final de parada da recorrência
- ✅ Anotações internas por agendamento
- ✅ Gerenciamento por status: Pendente · Enviado · Falhou · Cancelado
- ✅ Edição de mensagens pendentes
- ✅ Verificação automática a cada **60 segundos**
- ✅ Suporte a texto, imagem, vídeo, áudio e documento

**Casos de uso:**
- Follow-up 3 dias após proposta enviada
- Felicitação de aniversário agendada
- Lembrete semanal de pagamento
- Promoção de fim de semana toda sexta-feira

---

### 9. 🤖 Chatbot com IA — Respostas 24/7

**Para que serve:**  
Automatizar respostas a clientes sem precisar de atendente, usando regras predefinidas ou inteligência artificial para responder qualquer pergunta.

**Como funciona:**

**Tab Configuração:**
- Ativar/desativar chatbot
- Definir horário de funcionamento
- Mensagem especial fora do horário

**Tab Regras:**
Criar regras por tipo de gatilho:

| Tipo | Funcionamento |
|------|--------------|
| **Keyword** | Dispara quando a mensagem *contém* a palavra-chave |
| **Contains** | Dispara para qualquer substring do trigger |
| **Exact** | Dispara apenas se a mensagem for *exatamente* igual |
| **Regex** | Padrão avançado para cases complexos (ex: CPF, datas) |
| **Menu** | Responde com lista de opções clicáveis |

**Tab IA (Inteligência Artificial):**
- Integração com **Google Gemini** e **OpenAI (ChatGPT)**
- Sistema de fallback: se nenhuma regra bate → IA responde
- System prompt customizável ("Você é um assistente de suporte da [empresa]...")
- Controle de criatividade (temperatura da IA)
- Teste de conexão direto na tela

**Funcionalidades:**
- ✅ Regras ilimitadas com sistema de prioridade
- ✅ Ativar/desativar cada regra individualmente
- ✅ Contador de acionamentos por regra
- ✅ Histórico de respostas automáticas com logs
- ✅ Memória de contexto da conversa
- ✅ Providers: Gemini (`gemini-2.0-flash`) e OpenAI (`gpt-4o-mini`)
- ✅ Modelos customizados suportados
- ✅ Funciona dentro e fora do horário comercial

---

### 10. 🎨 Campanhas com IA — Criação de Promoções

**Para que serve:**  
Gerar imagens e texto de promoção automaticamente com IA para enviar em campanhas em massa.

**Como funciona:**

**Passo 1 — Imagem:**
- Opção A: Descreva a imagem desejada em texto → IA gera
- Opção B: Faça upload da foto do produto → IA cria versão promocional
- Visualize e regenere quantas vezes quiser

**Passo 2 — Texto (Copy):**
- Descreva o que quer promover
- IA gera copy de conversão persuasivo
- Edite manualmente se necessário

**Passo 3 — Salvar e Usar:**
- Pré-visualize imagem + texto juntos
- Defina nome e atalho (`/promo_pizza`)
- Salva automaticamente como Resposta Rápida
- Pronto para usar em Envio em Massa

**Funcionalidades:**
- ✅ **Google Gemini** e **OpenAI** como providers
- ✅ Imagem gerada em PNG (alta qualidade)
- ✅ Copy otimizado para conversão e vendas
- ✅ Suporte a imagem de referência (foto do produto)
- ✅ Regeneração ilimitada até aprovar
- ✅ Integração direta com Respostas Rápidas e Envio em Massa

**Fluxo completo de campanha:**  
`Criar promo com IA` → `Salvar como Resposta Rápida` → `Enviar para 100+ contatos via Bulk Send`

---

### 11. 📥 Importação de Contatos

**Para que serve:**  
Carregar uma lista de clientes de um arquivo CSV ou TXT para o CRM em segundos, sem precisar cadastrar um por um.

**Como funciona:**  
- Arraste ou clique para fazer upload do arquivo (`.csv`, `.txt`, `.tsv`)
- O sistema detecta automaticamente o separador (`,` `;` `tab` `|`)
- Detecta automaticamente os cabeçalhos de coluna
- Valida e limpa os números de telefone
- Preview de até 50 registros antes de importar
- Clicar em "Importar" — duplicados são atualizados, não duplicados

**Campos suportados:**  
Telefone (obrigatório) · Nome · E-mail · Empresa · Notas

**Funcionalidades:**
- ✅ Detecção automática de separadores e cabeçalhos
- ✅ Limpeza de prefixos (`tel:`, `whatsapp:`, `cel:`, `+55`, etc.)
- ✅ Validação de comprimento (7-16 dígitos)
- ✅ Deduplicação inteligente (atualiza sem duplicar)
- ✅ Log de erros com indicação da linha problemática
- ✅ Preview de 50 registros antes de confirmar
- ✅ Template de exemplo exibido na tela

---

### 12. 📊 Métricas e Relatórios

**Para que serve:**  
Dashboard completo com indicadores de desempenho em tempo real para acompanhar o atendimento e o chatbot.

**Como funciona:**  
Escolha o período (Hoje / 7 dias / 30 dias) e o dashboard carrega automaticamente:

**KPIs Principais:**
| Indicador | O que mostra |
|-----------|-------------|
| **Total Contatos** | Número total de contatos e grupos salvos |
| **Enviados Hoje** | Mensagens enviadas pela equipe no dia |
| **Recebidos Hoje** | Mensagens recebidas no dia |
| **Não Lidas** | Total de conversas aguardando resposta |
| **Chatbot (30d)** | Quantas respostas automáticas foram dadas |
| **Taxa de Leitura** | % de mensagens lidas pelo destinatário |

**Gráficos e Visualizações:**
- 📈 **Mensagens por dia** (últimos 7 dias): enviados vs. recebidos — tendência de volume
- 🥧 **Tipos de mensagem**: distribuição entre texto, imagem, vídeo, áudio, documento, sticker
- 🏆 **Ranking de atendentes** (com medalhas 🥇🥈🥉)
- 🎯 **Top regras de chatbot**: quais triggers mais acionados
- 🏷️ **Distribuição de etiquetas**: quantos contatos em cada tag
- 💼 **Pipeline de vendas**: valor total + quantidade de deals ativos
- 🤖 **Chatbot por tipo**: breakdown por welcome, keyword, default, fora de horário

**Funcionalidades:**
- ✅ **3 períodos**: Hoje, 7 dias, 30 dias
- ✅ 6 KPI cards com ícones e tendências
- ✅ Relatório de desempenho da equipe
- ✅ Análise do chatbot por tipo de resposta
- ✅ Visão do pipeline com valor monetário

---

### 13. 🔍 Histórico e Exportação

**Para que serve:**  
Buscar mensagens antigas e exportar conversas em CSV ou TXT para auditoria, análise ou arquivo.

**Como funciona:**

**Tab Exportar:**
- Filtros: data início/fim, contato específico, tipo de mensagem, direção (enviado/recebido), palavra-chave
- Escolher formato: CSV (Excel) ou TXT (legível)
- Download automático com nome padrão: `whatsapp_mensajes_[data_inicio]_[data_fim]`

**Tab Buscar:**
- Busca global em todos os contatos simultaneamente
- Mostra previews dos resultados com contexto
- Limite de 200 resultados por busca

**Tab Estatísticas:**
- Totais de mensagens por período
- Distribuição por tipo de mensagem
- Análise do período analisado

**Funcionalidades:**
- ✅ **5 filtros combináveis** (data, contato, tipo, direção, keyword)
- ✅ **Busca global** em todas as conversas (200 resultados)
- ✅ **2 formatos de exportação** (CSV para BI, TXT para leitura)
- ✅ Nome de arquivo gerado automaticamente com datas
- ✅ Auditoria completa de quem enviou o quê e quando

---

### 14. ⭐ Pesquisa de Satisfação (CSAT)

**Para que serve:**  
Medir automaticamente o nível de satisfação dos clientes após atendimentos com nota de 1 a 5 estrelas e Score NPS.

**Como funciona:**  
- Configurar mensagem de pesquisa e mensagem de agradecimento
- Ativar envio automático: sistema envia pesquisa N minutos após conversa
- Ou enviar manualmente para contatos selecionados
- Cliente responde com número de 1 a 5
- Dashboard analisa: média, distribuição e NPS

**Configurações:**
- Delay antes de enviar (ex: 5 minutos após atendimento)
- Cooldown entre pesquisas (ex: 7 dias — não reenvia em menos tempo)
- Mensagem customizável em qualquer idioma

**Analytics:**
| Métrica | O que mostra |
|---------|-------------|
| **Média de Rating** | Nota média de 1 a 5 com emoji ⭐ |
| **Total de Respostas** | Quantos clientes responderam |
| **NPS Score** | Net Promoter Score de -100 a +100 |
| **Distribuição** | Gráfico de barras: quantos deram 1★, 2★, 3★, 4★, 5★ |

**Cálculo NPS:**  
`NPS = (% Promotores ≥ 4★) − (% Detratores < 3★) × 100`

**Funcionalidades:**
- ✅ Auto-envio com delay configurável
- ✅ Cooldown anti-spam (padrão 7 dias)
- ✅ NPS Score em tempo real
- ✅ Visualização por cor: 🟢 excelente · 🟡 médio · 🔴 crítico
- ✅ Envio manual por contato quando necessário
- ✅ Histórico de todas as respostas com timestamps

---

## 🔗 INTEGRAÇÕES E TECNOLOGIA

### WhatsApp
- **API:** Evolution API v2.x (protocolo completo)
- **Conexão:** Via QR Code ou código de pareamento
- **Webhooks:** Recebimento em tempo real de mensagens, status, reações
- **Validação:** Verifica se número está no WhatsApp antes de enviar
- **Grupos:** Suporte completo — participantes, envio em massa para grupos

### Inteligência Artificial
- **Google Gemini:** `gemini-2.0-flash`, `gemini-1.5-pro`, `gemini-1.5-flash`
- **OpenAI:** `gpt-4o`, `gpt-4o-mini`, `gpt-3.5-turbo`
- **Configuração única** compartilhada entre Chatbot, Promoções e Campanhas

### Banco de Dados
- **Supabase (PostgreSQL):** Contatos, mensagens, chatbot, templates, respostas rápidas, agendamentos, CSAT
- **Supabase Realtime:** Atualizações instantâneas sem recarregar a página
- **Row Level Security:** Isolamento total por empresa — dados de uma empresa nunca vazam para outra
- **Storage:** Arquivos de mídia armazenados em buckets com cache de 3600 segundos

### Segurança
- 🔒 Autenticação via token em todas as Edge Functions
- 🔒 RLS policies em nível de tabela
- 🔒 Isolamento por `tienda_id` e `user_id`
- 🔒 Chaves de API armazenadas de forma segura, nunca expostas no cliente

---

## 📱 PLANOS E PERMISSÕES

O sistema suporta **controle de permissões por módulo** — cada plano pode habilitar/desabilitar funcionalidades específicas:

- `whatsapp_crm_license` — Acesso ao CRM completo
- Permissões por menu por tipo de funcionário
- Multi-instância: uma empresa pode ter múltiplos números WhatsApp

---

## 🏆 RESUMO DE CAPACIDADES

| Funcionalidade | Capacidade |
|----------------|-----------|
| Mensagens em massa/dia | **200 mensagens** |
| Delay anti-ban | **8 a 45 segundos** (distribuição humana) |
| Pausa de lote | **3 minutos a cada 10 msgs** |
| Arquivo upload (Respostas) | **16 MB** |
| Variáveis predefinidas | **12 variáveis** |
| Categorias templates | **7 categorias** |
| Recorrência (Agendamento) | **3 tipos** (diário, semanal, mensal) |
| Tipos de trigger chatbot | **5 tipos** |
| Providers de IA | **2** (Google Gemini + OpenAI) |
| Busca histórico | **200 resultados** |
| CSAT rating scale | **1 a 5 estrelas** |
| NPS range | **-100 a +100** |
| Cooldown CSAT | **7 dias** (padrão) |
| Cores de etiqueta | **10 cores** |
| Campos importação | **5 campos** |
| Separadores detectados | **4 tipos** (`,` `;` `tab` `|`) |
| Formatos exportação | **2** (CSV + TXT) |
| Períodos de métricas | **3** (Hoje, 7d, 30d) |

---

## 💡 CASOS DE USO REAIS

### 🛍️ Loja de Varejo / E-commerce
1. **Importar** lista de clientes que compraram no último mês (CSV)
2. **Criar campanha** com IA: foto do produto → imagem promocional → copy de conversão
3. **Enviar em massa** para 200 clientes com delay anti-ban
4. **Chatbot** responde dúvidas de horário, rastreamento, preços automaticamente
5. **Métricas** mostram taxa de resposta e engajamento

### 🏥 Clínica / Consultório
1. **Agendar** lembretes de consulta (1 dia antes, recorrente)
2. **CSAT** automático 10 minutos após atendimento
3. **Templates**: "Dr. {{agente}} confirmou seu horário para {{fecha}} às {{hora}}"
4. **Chatbot**: horário de atendimento, endereço, convênios aceitos
5. **Kanban**: pacientes por status (agendado, confirmado, realizado)

### 💼 Equipe Comercial / Vendas
1. **Kanban** para pipeline: Lead → Proposta → Negociação → Fechado
2. **Templates** de follow-up personalizados por cargo e empresa
3. **Agendamento**: follow-up em 3, 7 e 14 dias automático
4. **Métricas** de conversão por atendente (ranking)
5. **Bulk Send**: prospecção em massa com copy gerado por IA

### 🤝 Suporte ao Cliente
1. **Chatbot** com regras para FAQs (horário, preço, segunda via, etc.)
2. **IA generativa** para perguntas que não têm regra predefinida
3. **Equipe** atende apenas casos complexos (o chatbot filtra)
4. **Respostas Rápidas** para resoluções frequentes (em segundos)
5. **Histórico** + **Exportação** para auditoria e treinamento

---

*Documentação gerada em: 2025*  
*Sistema: Pagosya WhatsApp CRM*  
*Versão: Production*
