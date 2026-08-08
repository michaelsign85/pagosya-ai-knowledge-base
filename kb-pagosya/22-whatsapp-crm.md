# WhatsApp CRM — Documentação Completa de Funcionalidades
> **Uso:** Material de referência para Landing Page e para o assistente responder dúvidas de lojistas
> **Atualizado:** agosto/2026

---

## 🎯 O QUE É O WHATSAPP CRM?

O **WhatsApp CRM** é uma plataforma completa de gestão de relacionamento com clientes via WhatsApp. Em vez de usar o WhatsApp normal, sua equipe opera a partir de uma bandeja compartilhada com histórico, automações, IA e relatórios — tudo em um só lugar.

**Para quem é:**
- Negócios que recebem muitas mensagens no WhatsApp
- Equipes com múltiplos atendentes em um mesmo número
- Empreendedores que querem automatizar respostas e promoções
- Empresas que precisam rastrear pipeline de vendas via mensagens
- Clínicas, salões e oficinas que trabalham com hora marcada

---

# ⚠️ ANTES DE TUDO: OS DOIS TIPOS DE CONEXÃO

**Esta é a informação mais importante do documento.** Várias funcionalidades se comportam de forma diferente conforme o tipo de conexão do lojista. Ao responder qualquer dúvida sobre limites, envio em massa ou automação, **pergunte primeiro qual conexão ele usa**.

| | 🟢 **API Oficial (Meta Cloud API)** | 🟡 **Evolution (não oficial)** |
|---|---|---|
| **O que é** | Conexão oficial do WhatsApp Business, via Meta | Conexão por leitura de QR Code, como o WhatsApp Web |
| **Como conecta** | Vinculação guiada com a Meta (Embedded Signup) | QR Code ou código de pareamento |
| **Risco de bloqueio** | Nenhum por volume | **Real** — o WhatsApp pode banir o número |
| **Custo** | Paga por conversa iniciada (tabela da Meta) | Sem custo por mensagem |
| **Mensagem para contato novo** | Só com **plantilla aprovada** | Texto livre, sem restrição |
| **Velocidade de envio em massa** | ~1 segundo entre mensagens | 8 a 45 segundos entre mensagens |
| **Verificação/selo** | Possível conta verificada | Não |

**Resumo prático:** a API oficial é mais rápida, mais segura e permite escala — mas exige plantillas aprovadas para falar com quem não escreveu antes. A Evolution é livre para escrever para qualquer um, mas é lenta de propósito e tem risco de banimento.

O PagosYa é **Meta Tech Provider oficial**, o que permite conectar o número do lojista à API oficial direto pelo sistema, sem burocracia.

> ⚠️ **A Evolution não é mais oferecida a contas novas.** Quem já está nela continua funcionando normalmente e pode reconectar quando precisar, mas na tela de conexão só aparece a API oficial. **Não ofereça Evolution a um cliente novo.** Se ele insistir por causa do texto livre, explique a janela de 24 horas e as plantillas — é a mesma necessidade resolvida do jeito que não corre risco de banimento.

---

# 🛑 REQUISITOS QUE PRECISAM SER DITOS **ANTES** DE VENDER

> **Leia esta seção antes de fechar qualquer venda de WhatsApp CRM.**
> Estes quatro pontos são a causa nº 1 de cliente frustrado na segunda semana. Todos são fáceis de resolver **antes** de pagar, e todos viram reclamação se descobertos depois.

## 1. 📱 O número não pode estar em uso no WhatsApp comum

Para conectar na API oficial, o número **não pode ter WhatsApp ou WhatsApp Business instalado**. Se tiver, é preciso **apagar a conta pelo próprio aplicativo** antes de conectar (Configurações → Conta → Apagar minha conta).

- É o motivo nº 1 de onboarding que trava no meio
- Apagar a conta **apaga as conversas antigas daquele número** — avise antes
- Muitos lojistas preferem um **chip novo** só para o atendimento

**Pergunte sempre:** *"Esse número tem WhatsApp instalado hoje?"*

## 2. 💳 A Meta cobra à parte e pede cartão de crédito

Isto **não** está incluído na mensalidade do PagosYa. São duas contas diferentes.

| O que o lojista faz | Quem cobra | Custo |
|---|---|---|
| Mensalidade do CRM | **PagosYa** | Bs 249 / 449 / 699 |
| **Responder** cliente dentro de 24h | ninguém | **grátis** |
| **Enviar plantilla** (promoção, lembrete, aviso) | **Meta** | por mensagem, tabela da Meta |
| Tokens de IA | **provedor de IA** (Gemini/OpenAI/Claude) | conforme uso |

- O lojista precisa **cadastrar um cartão na conta de Meta Business dele**
- Sem cartão, as plantillas **param de sair** quando o crédito inicial gratuito acaba
- A cobrança da Meta vai direto para o cartão dele — o PagosYa não intermedeia, não repassa e não vê essa fatura
- **Responder cliente nunca custa.** Só custa iniciar conversa

**Frase pronta:** *"A mensalidade do PagosYa é o sistema. Responder seus clientes é grátis. Quando você quiser mandar promoção para quem não te escreveu, a Meta cobra por mensagem e debita do cartão que você cadastrar com eles."*

## 3. 📋 Plantillas precisam de aprovação da Meta

Para escrever a quem **não** falou nas últimas 24 horas, só com plantilla aprovada.

- A aprovação leva de **minutos a algumas horas**
- A Meta **pode recusar** — texto que parece propaganda enganosa, promessa exagerada ou erro de formatação
- O lojista cria a plantilla dentro do próprio CRM e acompanha o status ali
- **Não dá para improvisar:** quem só descobre isso na hora da campanha perde o dia

**Pergunte:** *"Você vai mandar promoção para lista antiga? Então vamos deixar as plantillas aprovadas já na primeira semana."*

## 4. 🤖 A IA usa a chave do próprio lojista

- O PagosYa **não vende tokens** e não os inclui na mensalidade
- O lojista escolhe o provedor (Gemini, OpenAI ou Claude) e cria a chave
- O consumo é faturado pelo provedor, direto para ele
- Chatbot e IA estão **nos três planos** — não é diferencial de plano caro

**Frase pronta:** *"A inteligência artificial vem em todos os planos. Você usa sua própria chave, e paga o consumo direto ao provedor — a gente não cobra por isso."*

---

## ✅ Checklist de qualificação (antes de fechar)

- [ ] Tem número disponível **sem WhatsApp instalado**?
- [ ] Aceita cadastrar **cartão na Meta** para as plantillas?
- [ ] Entendeu que **responder é grátis** e só iniciar conversa custa?
- [ ] Vai usar IA? Sabe que precisa de **chave própria**?
- [ ] Quantas pessoas vão atender? *(define o plano: 3, 5 ou 10 agentes)*

---

## 📋 A REGRA DA JANELA DE 24 HORAS (só API Oficial)

Esta regra explica a maioria das dúvidas dos lojistas na API oficial:

- Quando um cliente **escreve para você**, abre-se uma **janela de 24 horas**
- Dentro dessa janela: você responde com **texto livre**, o que quiser, sem custo adicional
- Passadas 24 horas sem ele escrever: só chega **plantilla aprovada pela Meta**

**Por que isso existe:** a Meta protege o usuário de receber mensagem de empresa que ele não contatou.

**O que isso significa na prática:**
- Responder cliente = sempre livre
- Campanha para lista antiga = precisa de plantilla
- Lembrete de consulta para amanhã = precisa de plantilla

---

## 📊 LIMITE DE ENVIOS (só API Oficial)

A Meta limita **quantos clientes NOVOS** você pode contatar a cada 24 horas. É o "nível" da conta:

| Nível | Clientes novos / 24h |
|---|---|
| Inicial | 250 |
| Negócio verificado | **1.000** |
| Seguintes | 10.000 → 100.000 → ilimitado |

**Três coisas que o lojista precisa entender:**

1. **Responder não conta.** Só conta conversa que **você** inicia.
2. **Falar 5 vezes com a mesma pessoa conta como 1.** O limite é de pessoas, não de mensagens.
3. **Não é corte à meia-noite.** A cota se libera sozinha, 24h após cada envio.

**Estourar o limite NÃO bloqueia a conta.** A Meta apenas recusa a mensagem, sem cobrar. O que realmente derruba a conta é outra coisa — ver abaixo.

**Observação:** desde outubro/2025 o limite é do **portfólio**, não do número. Dois números da mesma empresa dividem a mesma cota.

---

## 🚦 QUALIDADE DO NÚMERO — o que de fato derruba a conta

O CRM mostra a qualidade do número ao lado do status de conexão, e avisa quando ela cai.

| Estado | Significado | O que fazer |
|---|---|---|
| 🟢 **Buena** | Clientes recebem bem suas mensagens | Manter o ritmo |
| 🟡 **En riesgo** | Alguns bloquearam ou denunciaram | Pausar campanhas, escrever só para quem espera contato |
| 🔴 **Crítica** | Meta marcou o número | Parar envios em massa **imediatamente** |

A Meta calcula isso pelo comportamento de **quem recebe**: bloqueios e denúncias derrubam; respostas e cliques sustentam.

**Se cair para crítica e não melhorar em 7 dias, o limite diário desce um nível.** Ou seja: o risco não é volume, é mandar mensagem para quem não quer receber.

---

# 📦 MÓDULOS DO SISTEMA

## 1. 💬 Chat em Tempo Real — Bandeja Compartilhada
*Funciona igual nos dois provedores*

Central de atendimento onde toda a equipe vê e responde mensagens de um único número.

- Lista única de contatos com preview da última mensagem e badge de não lidas
- Histórico completo ao clicar no contato
- Registro de qual atendente respondeu
- Texto, imagens, vídeos, áudios, documentos, stickers e localização
- Atribuição de contatos a atendentes específicos
- Status de leitura (✓ enviado · ✓✓ entregue · ✓✓ lido)
- Suporte a grupos
- Histórico persistido — nunca se perde

---

## 2. 🏷️ Etiquetas e Filtros
*Igual nos dois provedores*

Organizar contatos por categorias visuais (leads quentes, VIPs, pagamento pendente).

- Etiquetas com nome e cor (10 cores)
- Múltiplas etiquetas por contato
- Filtro da lista de conversas por etiqueta
- Distribuição visível nas métricas

---

## 3. 🗂️ Pipeline Kanban de Vendas
*Igual nos dois provedores*

Acompanhar leads por etapa comercial, arrastando cartões.

- Etapas customizáveis (padrão: Prospectos → Contactado → Propuesta → Negociación → Ganado)
- Arrastar e soltar entre etapas
- Valor monetário e prioridade por negócio
- Um negócio por contato
- Movimentação automática por palavra-chave do cliente

---

## 4. 👤 CRM de Contatos
*Igual nos dois provedores*

Ficha completa: empresa, e-mail, cargo, notas, histórico de compras.

---

## 5. 📤 Envio em Massa
**⚠️ Este módulo funciona de forma MUITO diferente conforme a conexão**

### 🟢 Na API Oficial (Meta)

**Duas formas de enviar:**

| Formato | Chega a quem | Quando usar |
|---|---|---|
| **Plantilla aprovada** | **Todos os contatos** | Campanhas, promoções, avisos |
| **Mensagem rápida** (texto livre) | Só quem escreveu nas últimas 24h | Continuar conversas em andamento |

**O sistema protege o lojista automaticamente:** ao escolher "mensagem rápida", os contatos fora da janela de 24h aparecem **bloqueados na lista, com o motivo à mostra** — não somem, para o lojista entender que precisa de plantilla.

**Ritmo:** ~1 segundo entre envios (o limite da Meta é 80 mensagens por segundo). Uma campanha de 200 contatos leva cerca de **3 minutos**.

**Painel de capacidade** mostra: quantos clientes novos já foram contatados nas 24h, quanto resta, e a qualidade do número.

### 🟡 Na Evolution

**Modo anti-ban, com ritmo humano simulado:**

| Cenário | Frequência | Delay |
|---|---|---|
| Ritmo normal | 60% das msgs | 8 – 20 segundos |
| Pausa média | 30% das msgs | 20 – 35 segundos |
| Micro-pausa | 10% das msgs | 35 – 45 segundos |
| Pausa de lote | A cada 10 msgs | 3 minutos |

- **200 mensagens/dia** — limite de segurança
- 200 contatos levam cerca de **2 horas**
- Só texto livre (não existe plantilla)

**Por que a diferença:** na Evolution o ritmo lento evita banimento. Na API oficial isso não protege de nada — só faria a campanha demorar horas sem motivo.

### Comum aos dois
- Seleção individual, por grupos ou importação de CSV/TXT
- Validação de números antes do envio
- Progresso em tempo real, com pausa e cancelamento
- Variáveis dinâmicas (`{{nombre}}`, `{{telefono}}`)
- Relatório de falhas com **motivo explicado em linguagem clara**

---

## 6. ⚡ Respostas Rápidas
*Igual nos dois provedores*

Biblioteca de mensagens predefinidas com atalhos (`/ola`, `/preco`).

- Texto, imagem, vídeo, áudio, documento ou sticker
- Upload até **16 MB**
- **12 variáveis** + customizadas
- Uso digitando `/` no chat
- 6 categorias organizadoras
- Duplicar, ativar/desativar, buscar

**Variáveis:** `{{nombre}}` · `{{telefono}}` · `{{empresa}}` · `{{email}}` · `{{ciudad}}` · `{{pais}}` · `{{cargo}}` · `{{producto}}` · `{{agente}}` · `{{fecha}}` · `{{hora}}` · `{{tienda}}`

⚠️ **Na API oficial**, respostas rápidas só chegam a quem está na janela de 24h.

---

## 7. 📋 Plantillas da Meta *(só API Oficial)*

**Não confundir com Respostas Rápidas.** São coisas diferentes:

| | Resposta Rápida | Plantilla Meta |
|---|---|---|
| Aprovação | Nenhuma, usa na hora | **Precisa de aprovação da Meta** |
| Alcance | Só janela de 24h | **Qualquer contato, sempre** |
| Variáveis | `{{nombre}}`, `{{empresa}}` | `{{1}}`, `{{2}}`, `{{3}}` |
| Onde criar | Menu Respostas Rápidas | Menu Plantillas |

**Como funciona:**
- Criar com nome, categoria (Marketing/Utilidade) e corpo
- Enviar para aprovação da Meta — costuma levar de minutos a poucas horas
- Aprovada, fica disponível no envio em massa e no agendamento

**Regras da Meta que o sistema valida antes de enviar:**
- Corpo **não pode começar nem terminar com variável**
- Cada variável precisa de um valor de exemplo
- Nome só com minúsculas, números e sublinhado

**Cabeçalho com imagem:** ao salvar uma promoção criada com IA como plantilla, a imagem gerada vira o cabeçalho automaticamente.

---

## 8. 📅 Agendamento de Mensagens

Programar mensagens para data e hora específicas.

**✅ Funciona com o navegador fechado.** O envio roda no servidor, verificado a cada 5 minutos — não depende do lojista estar com o sistema aberto.

**Três formas de escolher o destinatário:**
1. **Um contato** — com busca por nome ou número (funciona com milhares de contatos)
2. **Etapa do pipeline** — envia para todos que estiverem naquela etapa **no momento do envio**; quem entrar depois também recebe
3. Digitar um número manualmente

**Formatos:**
- Texto, imagem, vídeo, áudio, documento
- 🟢 **Plantilla aprovada** (só API oficial) — o único formato que garante entrega

⚠️ **Aviso importante na API oficial:** como o envio acontece no futuro, a janela de 24h provavelmente estará fechada. O sistema avisa isso no formulário e recomenda plantilla.

**Recorrência:** diária, semanal ou mensal, com data final opcional.

**Estados:** Pendente · Enviado · Falhou · Cancelado — com motivo da falha em linguagem clara.

**Relatório de envio para etapa:** quantos receberam, quantos falharam e por quê.

---

## 9. 🤖 Chatbot com IA — Respostas 24/7

Automatizar respostas usando regras ou inteligência artificial.

### Configuração guiada (para quem está começando)
1. **Vincular a chave de IA** (obrigatório antes de tudo)
2. **Ensinar o negócio ao bot** — três formas:
   - Subir um **PDF** (catálogo, cardápio, tabela de preços)
   - Informar o **endereço de um site**
   - **Escrever à mão** sobre o negócio (para quem não tem material pronto)
3. **Quiz de personalidade** — nome do bot, tom de voz, objetivos, o que nunca dizer, quando chamar um humano

O sistema compila tudo num "manual" que o bot consulta a cada resposta.

### Regras por palavra-chave

| Tipo | Funcionamento |
|---|---|
| **Keyword** | Dispara quando a mensagem contém a palavra |
| **Contains** | Qualquer parte do texto |
| **Exact** | Mensagem exatamente igual |
| **Regex** | Padrão avançado |
| **Menu** | Responde com lista de opções |

### Inteligência Artificial

**Três provedores:** Google Gemini · OpenAI (ChatGPT) · **Claude (Anthropic)**

- Modo fallback: a IA só responde quando nenhuma regra bate (recomendado)
- Memória da conversa configurável
- Movimentação automática no pipeline por palavra-chave
- Registro de todas as respostas automáticas
- Horário de funcionamento com mensagem fora de hora

**⚠️ Diferença entre provedores:**
- 🟢 **API Oficial** — todos os três provedores, incluindo Claude
- 🟡 **Evolution** — Gemini e OpenAI (Claude ainda não disponível)

### Sobre a chave de IA
Cada lojista usa **sua própria chave** — o PagosYa não cobra por mensagem de IA nem revende tokens. As chaves ficam guardadas no servidor e **nunca passam pelo navegador**.

---

## 10. 🎨 Promoções com IA
*Igual nos dois provedores*

Gerar imagem e texto de promoção automaticamente.

**Passo 1 — Imagem:** descrever o que quer, ou subir a foto do produto para a IA criar a versão promocional.

**Modelos de imagem disponíveis (família Nano Banana, do Gemini):**

| Modelo | Uso |
|---|---|
| Nano Banana 2 | Equilíbrio (padrão) |
| Nano Banana 2 Lite | Mais rápido e barato — bom para volume |
| Nano Banana Pro | Máxima qualidade — peças caprichadas |

Também suporta GPT Image 1 e DALL·E 3 (OpenAI).

**Passo 2 — Texto:** a IA gera copy de conversão, editável.

**Passo 3 — Onde salvar:** o lojista escolhe um ou os dois:
- **Resposta Rápida** — disponível na hora
- 🟢 **Plantilla de WhatsApp** (só API oficial) — passa por aprovação da Meta, depois alcança qualquer contato

⚠️ **Claude não gera imagens.** Quem usa Claude precisa configurar um provedor de imagem separado (Gemini ou OpenAI). O sistema avisa isso na tela.

---

## 11. 📆 Agenda de Citas *(módulo novo)*
*Funciona nos dois provedores; os avisos automáticos dependem da conexão*

Sistema de hora marcada para **clínicas, consultórios, salões, barbearias e oficinas**.

### Como funciona

**1. Cadastrar profissionais** — cada um recebe um **link próprio de agenda**

**2. Definir horário de trabalho** por dia da semana
   - Intervalo de almoço = dois blocos no mesmo dia (ex: 08:00–12:00 e 14:00–18:00)

**3. Cadastrar serviços** com duração e preço
   - **Tempo de preparo** opcional (limpeza entre atendimentos) — bloqueia a agenda mas não aparece para o cliente

**4. O cliente agenda sozinho pelo link**
   - Abre sem login, vê os horários **realmente livres** e escolhe
   - O mesmo link serve para enviar por WhatsApp, colar na bio do Instagram ou no Google Meu Negócio

### Por que o link (e não o bot perguntando tudo)

O bot pergunta com qual profissional e **envia o link**. O cliente escolhe o horário na tela.

**Motivo:** o horário vem direto do banco de dados. O bot nunca fala uma data — então **não tem como inventar disponibilidade**, que é o pior erro possível numa agenda de clínica.

### Proteções

- **Dois clientes nunca pegam o mesmo horário**, mesmo clicando ao mesmo tempo — garantido pelo banco de dados
- Antecedência mínima (não dá para agendar para daqui a 10 minutos)
- Limite de dias à frente
- Bloqueio de férias e feriados
- Arquivar profissional **preserva o histórico** de atendimentos

### Confirmação — dois modos
- **Automático** (padrão): o cliente escolhe e está agendado — bom para salão, barbearia, oficina
- **Com aprovação**: a solicitação fica pendente até alguém aprovar — bom para clínica que faz triagem

Nos dois casos **o horário fica bloqueado** enquanto aguarda.

### Avisos automáticos
- **Lembrete ao cliente** antes da consulta (tempo configurável)
- **Aviso ao profissional** quando entra uma cita nova
- Remarcar **atualiza** o lembrete; cancelar **cancela** o lembrete

⚠️ **Na API oficial**, o lembrete precisa de uma plantilla aprovada — porque 24h antes da consulta a janela quase sempre está fechada.

---

## 12. 📥 Importação de Contatos
*Igual nos dois provedores*

Carregar lista de CSV ou TXT.

- Detecção automática de separador (`,` `;` `tab` `|`) e cabeçalhos
- Limpeza de prefixos (`tel:`, `whatsapp:`, `+55`)
- Validação de 7 a 16 dígitos
- Deduplicação (atualiza sem duplicar)
- Preview de 50 registros antes de confirmar
- Log de erros com a linha problemática

**Campos:** Telefone (obrigatório) · Nome · E-mail · Empresa · Notas

---

## 13. 📊 Métricas e Dashboard
*Igual nos dois provedores*

**KPIs:** Contatos · Enviados · Recebidos · Não lidas · Respostas do chatbot (30d) · Taxa de leitura

**Períodos:** Hoje · 7 dias · 30 dias — **os cartões e a taxa de leitura seguem o período escolhido**

**Gráficos:**
- Mensagens por dia (7 dias): enviados vs. recebidos
- Tipos de mensagem
- Ranking de atendentes 🥇🥈🥉
- Regras de chatbot mais acionadas
- Distribuição de etiquetas
- Pipeline: valor total e quantidade
- Chatbot por tipo de resposta

Os números refletem a **base completa**, sem corte por volume.

---

## 14. 🔍 Histórico e Exportação
*Igual nos dois provedores*

Busca global em mensagens antigas, exportação em CSV ou TXT.

---

## 15. ⭐ Pesquisa de Satisfação (CSAT)
*Igual nos dois provedores*

Avaliação de 1 a 5 estrelas enviada após o atendimento, com NPS calculado e período de carência configurável (padrão 7 dias).

---

# 🔗 TECNOLOGIA E SEGURANÇA

### Conexão WhatsApp
- **API Oficial:** WhatsApp Cloud API — PagosYa é **Meta Tech Provider** aprovado, com vinculação guiada
- **Evolution API v2.x:** conexão por QR Code ou código de pareamento
- Webhooks em tempo real para mensagens, status e reações
- Validação de números antes do envio
- Multi-instância: uma empresa pode ter mais de um número

### Inteligência Artificial
- **Google Gemini** · **OpenAI** · **Claude (Anthropic)**
- Imagens: família **Nano Banana** (Gemini) e GPT Image / DALL·E (OpenAI)
- **Modelo de chave própria:** cada lojista usa sua conta de IA. O PagosYa não revende tokens.
- **As chaves nunca chegam ao navegador** — ficam no servidor, usadas apenas por funções protegidas

### Banco de Dados
- **Supabase (PostgreSQL)** com atualizações instantâneas
- **Row Level Security:** isolamento total por empresa
- Storage para mídias

### Segurança
- 🔒 Autenticação em todas as funções de servidor
- 🔒 Isolamento por empresa e usuário
- 🔒 Chaves de API guardadas no servidor, nunca expostas
- 🔒 Agendamentos e envios processados no servidor

---

# 📱 PLANOS

São **três níveis**. Todos incluem 1 número de WhatsApp.

| | **CRM** | **Ventas** ⭐ | **Commerce** |
|---|---|---|---|
| **Mensal** | Bs 249 | Bs 449 | Bs 699 |
| **Anual** | Bs 2.490 | Bs 4.490 | Bs 6.990 |
| **Agentes** | 3 | 5 | 10 |

O anual equivale a **10 meses** — dois meses grátis.

## O que cada um entrega

### 🟩 Nos três (inclusive o mais barato)
- Bandeja compartilhada, histórico e atribuição de conversas
- Contatos, etiquetas, filtros e respostas rápidas
- Plantillas oficiais da Meta · importação CSV · mensagens programadas
- **Chatbot completo** — palavra-chave, menus, horários, fora de horário, handoff
- **Inteligência artificial** com a chave do lojista
- **Agenda de citas completa**, incluindo o bot enviando o link sozinho
- **Link de cobro no chat** com aviso de pagamento
- Métricas básicas de atendimento

### 🟦 A partir do Ventas
- **Pipeline Kanban** de oportunidades
- **Mensagens em bloco** (campanhas com plantilla)
- Segmentação por etiqueta e por etapa
- **CSAT**, ranking de atendentes e métricas de equipe

### 🟪 Só no Commerce
- **Tienda Online** e catálogo público
- **Produtos, categorias e inventário**
- Checkout com pagamento automático
- **Botão de compartilhar a tienda** dentro da conversa
- Relatórios de vendas por produto e categoria

## ➕ Agente adicional — Bs 20 por 30 dias

Precisa de mais um atendente sem trocar de plano? **Um crédito de Bs 20 adiciona 1 agente por 30 dias.** É o mesmo crédito de expansão que já existe no PagosYa, comprado pelo menu de créditos.

Quando o crédito expira, o agente extra é bloqueado — **as conversas já atribuídas a ele não se perdem**.

## ⚠️ Pontos de atenção do atendente

**O plano de WhatsApp SOMA ao plano PagosYa, não substitui.**
Quem já tem ExpandeYa ou ConquistaYa **não perde nada** ao contratar o WhatsApp CRM. A Tienda Online que ele já tem continua funcionando — o nível de WhatsApp só acrescenta.

**Por isso, cuidado ao oferecer o Commerce.** Se o lojista **já tem Tienda Online pelo plano dele**, o Commerce não acrescenta loja nenhuma — nesse caso o certo é o **Ventas**. O Commerce é para quem **não** tem plano com loja e quer tudo junto.

**O limite de agentes é de quem atende, não de quem está cadastrado.** Um funcionário cadastrado que nunca recebeu conversa não ocupa vaga.

**Segundo número de WhatsApp ainda não está disponível.** Está no roteiro. Não prometa.

---

# 🏆 RESUMO DE CAPACIDADES

### Envio em massa — a diferença que mais importa

| | 🟢 API Oficial | 🟡 Evolution |
|---|---|---|
| Intervalo entre mensagens | ~1 segundo | 8 a 45 segundos |
| 200 contatos levam | ~3 minutos | ~2 horas |
| Limite | Clientes novos/24h do nível (250 a ilimitado) | 200 mensagens/dia |
| Contato fora da janela 24h | Só plantilla | Texto livre |
| Risco de banimento por volume | Nenhum | Real |

### Demais capacidades

| Funcionalidade | Capacidade |
|---|---|
| Upload de arquivo | **16 MB** |
| Variáveis predefinidas | **12** |
| Recorrência de agendamento | **3 tipos** |
| Tipos de gatilho do chatbot | **5** |
| Provedores de IA | **3** (Gemini, OpenAI, Claude) |
| Modelos de imagem | **5** (3 Nano Banana + 2 OpenAI) |
| Destino do agendamento | **3** (contato, etapa do pipeline, número avulso) |
| Busca no histórico | **200 resultados** |
| CSAT | **1 a 5 estrelas**, NPS de -100 a +100 |
| Cores de etiqueta | **10** |
| Formatos de exportação | **2** (CSV, TXT) |
| Períodos de métricas | **3** (Hoje, 7d, 30d) |

---

# 💡 CASOS DE USO REAIS

### 🏥 Clínica / Consultório
1. **Agenda:** cadastrar médicos, horários e serviços
2. Enviar o **link da agenda** por WhatsApp ou colar no Instagram
3. Paciente escolhe o horário sozinho — sem ligação, sem ida e volta
4. **Lembrete automático** 24h antes (plantilla aprovada)
5. **Aviso ao médico** a cada nova consulta
6. **Chatbot** responde endereço, convênios e horários
7. **CSAT** após o atendimento

### 💇 Salão / Barbearia
1. Cada profissional com **seu link de agenda**
2. Link na bio do Instagram — cliente agenda a qualquer hora
3. **Tempo de preparo** entre atendimentos, invisível para o cliente
4. **Promoções com IA** para dias parados
5. Envio para a etapa "Clientes recorrentes" do pipeline

### 🛍️ Varejo / E-commerce
1. **Importar** lista de clientes (CSV)
2. **Promoção com IA:** foto do produto → imagem → copy
3. Salvar como **plantilla** e enviar para todos
4. **Chatbot** responde rastreamento, horário e preços
5. **Métricas** de engajamento

### 💼 Equipe Comercial
1. **Kanban:** Lead → Proposta → Negociação → Fechado
2. **Agendar** follow-up para uma etapa inteira do pipeline
3. **Ranking** de atendentes
4. Prospecção com plantilla aprovada

### 🤝 Suporte
1. **Chatbot** com regras para as dúvidas frequentes
2. **IA** para o que não tem regra
3. Equipe atende só os casos complexos
4. **Histórico** e exportação para auditoria

---

# ❓ PERGUNTAS FREQUENTES

**"Por que minha mensagem não chegou?"**
Na API oficial, texto livre só chega a quem escreveu nas últimas 24h. Use uma plantilla aprovada.

**"Estourei o limite. Minha conta foi bloqueada?"**
Não. A Meta só recusa a mensagem, sem cobrar. A cota se libera sozinha ao longo das horas.

**"O que pode bloquear minha conta então?"**
A qualidade do número. Se muitos clientes bloquearem ou denunciarem, a Meta reduz seu limite. Envie só para quem espera seu contato.

**"Recebi o erro 131049."**
A pessoa já recebeu muitas promoções naquele dia — de **qualquer** empresa, não só a sua. Não há nada errado com sua conta e você não foi cobrado.

**"Posso agendar mensagem e fechar o navegador?"**
Sim. O envio roda no servidor.

**"Preciso pagar IA à parte?"**
A chave de IA é sua. O PagosYa não cobra por mensagem de IA. Chatbot e IA vêm nos três planos.

**"Quanto custa mandar mensagem? A mensalidade cobre tudo?"**
Não. São duas contas. A mensalidade do PagosYa é o sistema. **Responder um cliente dentro de 24h é grátis.** Enviar plantilla (promoção, lembrete, aviso) é cobrado pela **Meta**, por mensagem, direto no cartão que você cadastrar com eles.

**"Preciso mesmo de cartão de crédito?"**
Sim, na sua conta de Meta Business. Sem cartão, as plantillas param de sair quando o crédito inicial gratuito acabar. Responder cliente continua funcionando.

**"Meu número já tem WhatsApp. Posso usar?"**
Só depois de apagar a conta pelo aplicativo (Configurações → Conta → Apagar minha conta). Isso apaga as conversas antigas daquele número, então muita gente prefere usar um chip novo só para o atendimento.

**"Por que preciso de plantilla? Não posso escrever o que eu quero?"**
Pode — para quem te escreveu nas últimas 24 horas. Fora disso a Meta só entrega plantilla aprovada, para proteger o usuário de empresa que ele não contatou. A aprovação leva de minutos a algumas horas.

**"Posso ter dois números de WhatsApp?"**
Ainda não. Está no roteiro, mas hoje é um número por conta.

**"Já tenho o plano ConquistaYa. Vou perder minha Tienda Online se contratar o WhatsApp?"**
Não. O plano de WhatsApp **soma** ao que você já tem, nunca tira. Nesse caso o indicado é o **Ventas** — o Commerce só faz sentido para quem ainda não tem loja.

**"Preciso de mais um atendente, mas não quero trocar de plano."**
Um crédito de **Bs 20 adiciona 1 agente por 30 dias**. Quando expira, o agente extra é bloqueado, mas as conversas dele não se perdem.

**"O bot pode marcar consultas?"**
Ele envia o link da agenda, e o cliente escolhe o horário. Isso garante que o horário oferecido é real.

**"Qual conexão devo usar?"**
API oficial — é a única oferecida para contas novas. Quem já está na Evolution continua funcionando e pode reconectar, mas não indicamos mais essa via: o risco de banimento do número é real e a Meta oficial resolve a mesma necessidade com plantillas.

---

*Atualizado em: agosto/2026*
*Sistema: PagosYa WhatsApp CRM*
*PagosYa é Meta Tech Provider oficial*
