# WhatsApp CRM — Documentação Completa de Funcionalidades
> **Uso:** Material de referência para Landing Page e para o assistente responder dúvidas de lojistas
> **Atualizado:** outubro/2026

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
- [ ] Vai cobrar pelo chat? Tem conta no **BNB ou Banco Económico**?

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
- **Vários canais na mesma bandeja:** WhatsApp e **Web** (chat da tienda online) — cada conversa mostra o ícone do canal, e há filtro por canal (*Todos los canales · WhatsApp · Web*). O chat de todos os canais tem o mesmo visual do WhatsApp *(ver módulo 17)*
- **Filtros rápidos:** No leídos · Mis chats · Sin asignar · Grupos · por etiqueta
- Histórico completo ao clicar no contato
- Registro de qual atendente respondeu
- Texto, imagens, vídeos, áudios, documentos, stickers e localização
- Atribuição de contatos a atendentes específicos
- Status de leitura (✓ enviado · ✓✓ entregue · ✓✓ lido)
- Suporte a grupos
- **Nova conversa** a partir de um número, sem esperar o cliente escrever
- **Arquivar** contatos que já não precisam de atenção
- **Bot por conversa — três estados no botão do topo do chat:**
  - **Bot ON** (verde): o bot responde esse contato
  - **Bot en pausa** (amarelo): o bot se calou sozinho — porque a conversa foi **atribuída a um atendente** (com a opção *Pausar el bot al asignar* ligada) ou porque **o próprio bot pediu um humano** (handoff)
  - **Bot OFF**: alguém silenciou à mão
  - O estado muda **na hora**, sem recarregar a página. O bot só volta a responder quando alguém clica no botão — **nunca volta sozinho**
- **Alertas para o atendente** (som + notificação do navegador):
  - quando chega mensagem numa conversa **atribuída a ele** e ele não está olhando
  - quando **lhe atribuem** uma conversa
  - quando **o bot pede um humano** — esse vai para quem tem a conversa; sem atribuição, para toda a equipe
  - O **sino 🔔** ao lado da busca liga/silencia os alertas naquele navegador. Ao abrir o CRM **não toca nada** por mensagens antigas — só pelo que chega depois
  - A notificação do navegador só aparece com a aba em segundo plano e depois de o atendente **permitir notificações** no navegador
- **Áudios recebidos:** clicar em **"Clic para cargar audio"** baixa e já toca (um clique só)
- Botão **Agendar** na barra do contato *(ver Agenda de Citas)*
- Histórico persistido — nunca se perde

### A barra de escrever (o que o atendente tem à mão)

| Botão | O que faz |
|---|---|
| 📎 **Anexar** | Documento · Fotos e vídeos · **Câmera** (tira a foto na hora, no celular) · Áudio — até 16 MB |
| 🌐 **Compartilhar tienda** | Manda o link da tienda online na conversa *(quem tem tienda pelo plano-base ou pelo Commerce)* |
| 🔗 **Link de cobro** | Cobra o cliente dentro do chat — ver módulo *Cobros no chat* |
| ✨ **Assistente de IA** | Reescreve o que o atendente digitou: melhorar, corrigir gramática, expandir, encurtar, tom amigável, tom formal, simplificar, traduzir ES/EN |
| ☁️ **Plantilla** | Envia uma plantilla aprovada direto da conversa *(só API oficial)* |
| `/` | Abre as respostas rápidas pelo atalho |
| 📝 **Nota interna** (ícone de post-it) | Troca o campo para modo nota — clicar de novo volta a escrever ao cliente. O texto **não vai para o cliente**, fica na conversa em amarelo com o aviso *"Solo la ve tu equipo"*. Serve para deixar o resumo de uma ligação, de uma reunião ou o que o próximo atendente precisa saber |

**Janela de 24h fechada:** na API oficial, quando o cliente não escreve há mais de 24h, aparece uma faixa vermelha no lugar do campo de texto. Um toque nela abre as plantillas aprovadas — o atendente não fica travado sem saber o que fazer.

### Painel do contato
Ao lado da conversa (clicar no nome do contato), quatro abas: **Info** (dados do contato) · **Etiquetas** (todas as do contato — a lista de conversas mostra só as primeiras, por falta de espaço) · **Notas** internas · **Ventas** (histórico de compras do cliente na loja).

**Notas internas aparecem também no meio da conversa**, na ordem em que foram escritas, junto com as mensagens — inclusive o **resumo que o bot deixa** quando passa a conversa para um humano (motivo, o que o cliente quer, plano sugerido). Quem assume já lê o contexto sem perguntar de novo ao cliente.

---

## 2. 🏷️ Etiquetas e Filtros
*Igual nos dois provedores*

Organizar contatos por categorias visuais (leads quentes, VIPs, pagamento pendente).

- Etiquetas com nome e cor (10 cores)
- Múltiplas etiquetas por contato
- Filtro da lista de conversas por etiqueta (barra **ETIQUETAS** no topo)
- A lista de conversas mostra as primeiras etiquetas de cada contato; **todas** ficam no painel do contato → aba **Etiquetas**
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

**Nome do cliente nas plantillas (`{{nombre}}`):**
- Ao escolher uma plantilla, a primeira variável **já vem preenchida com `{{nombre}}`** — cada contato recebe o próprio nome
- Escrever só `nombre`, `{nombre}` ou `[nombre]` também funciona
- Vai só o **primeiro nome**, sem emojis (ex.: "CRISTHIAN ✌🏽" → "Cristhian"); nome de negócio com artigo sai inteiro ("La Salvadora")
- Contato **sem nome** utilizável (vazio, só emoji, "User_67") recebe **"estimado cliente"** — nunca o número de telefone
- ⚠️ Qualquer outro texto digitado na variável vai **igual para todos** os contatos

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

**A mensagem enviada aparece na conversa** do contato, com remetente **"Programado"** e os checks de entrega (✓ enviado · ✓✓ entregue · ✓✓ azul lido). Vale também para os **lembretes da Agenda**. É assim que se confirma que o cliente recebeu: o estado "Enviado" na lista só diz que saiu do sistema.

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

### Outros ajustes do bot
- **Mensagem de boas-vindas** com intervalo configurável (padrão: 1 vez a cada 24h por contato — não repete a cada "hola")
- **Horário de atendimento** por dia da semana, com fuso horário e mensagem fora de hora
- **Pausar el bot al asignar** (aba Ajustes): quando a conversa é atribuída a um atendente, o bot **para de responder aquele contato** para não falar por cima da pessoa. Para voltar, o atendente clica no botão do bot no chat. Recomendado para quem tem equipe atendendo junto com o bot
- **Responder al texto de las fotos** (aba Ajustes): se o cliente manda foto, vídeo ou documento **com texto** ("¿tienen este?"), o bot responde ao texto. Desligado, foto não aciona o bot
- **Aba Agendamento:** quando o cliente pede hora, o bot **envia o link da agenda** ou **agenda na própria conversa** — o lojista escolhe *(ver Agenda de Citas)*
- **Aba Histórico:** tudo o que o bot respondeu, e por qual regra ou IA

### 🔌 Modo webhook externo (n8n, Make ou sistema próprio)
*Para quem já tem automação própria ou uma agência que monta fluxos.*

Em vez do bot interno, o CRM **encaminha cada mensagem recebida para uma URL** do lojista e publica no chat a resposta que o sistema dele devolver.

- Escolha na aba **Ajustes** do chatbot: "Bot de PagosYa" ou "Webhook externo"
- Autenticação por **segredo** (header `Authorization: Bearer ...`) gerado no próprio CRM
- A tela traz o passo a passo para n8n e exemplos do que chega e do que deve ser devolvido
- Proteção contra duplicado se o sistema externo reenviar
- **Áudios, fotos e documentos também chegam** ao webhook, com um link para baixar o arquivo (mesma credencial). Assim o fluxo do lojista pode, por exemplo, **transcrever áudios** com a própria chave de IA
- O sistema externo pode responder com **texto ou arquivo** (imagem, vídeo, documento, áudio)
- Pode deixar uma **nota interna** no chat (campo `note`) — ideal para o resumo do cliente ao passar para um humano
- Pode **pausar o bot** naquele contato (campo `handoff: true`) — o atendente vê "Bot en pausa" e o bot só volta quando alguém reativa no chat
- As opções *Pausar el bot al asignar* e *Responder al texto de las fotos* valem também neste modo

**Quando indicar:** cliente com fluxo já pronto em n8n/Make, ou que quer ligar o WhatsApp a um sistema interno. Para quem não tem nada, o bot interno com IA resolve sem precisar de técnico.

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

### O bot agenda de dois jeitos — o lojista escolhe
*Chatbot → aba Agendamento → "¿Cómo agenda el bot?"*

| Modo | O que acontece | Bom para |
|---|---|---|
| **Enviar el enlace** (padrão) | O bot pergunta com qual profissional e manda o **link da agenda**; o cliente escolhe o horário na página | Quem prefere que o cliente veja a agenda inteira |
| **Agendar en el chat** | O bot oferece **3 horários livres** na conversa, o cliente responde com o número ("2") e a cita fica marcada ali mesmo, com confirmação | Quem perde clientes no link ("mucho trámite") — o cliente nem sai do WhatsApp |

**Nos dois modos o bot não inventa horário:** os horários vêm da agenda, lidos na hora. No modo chat o bot só confirma depois que a cita ficou gravada; se outro cliente pegou o mesmo horário um segundo antes, ele oferece outras opções. O modo chat entende pedidos como *"mañana por la tarde"* e funciona **só no WhatsApp**.

**Reagendar pelo bot (modo chat):** o cliente escreve **"reagendar"** (ou toca o botão *Reagendar* do lembrete) e o bot oferece novos horários. Ao confirmar o novo, a **cita anterior é cancelada sozinha** — junto com o lembrete dela.

A mensagem de confirmação só diz *"Te enviamos un recordatorio antes"* quando o lembrete foi de fato programado.

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

### Reservas pela tienda online (plantilla Barbería)
Quem tem **tienda online** pode escolher a plantilla **Barbería** (Personalizar Tienda → Diseño). A página da tienda mostra os serviços, a equipe e o **próximo horário livre** — tudo tirado desta Agenda — e o cliente **reserva sem sair do site**, com o mesmo fluxo do link da agenda.

- A reserva entra na Agenda da **tienda dona da tienda online**. Se o lojista tem várias tiendas, ele precisa olhar a Agenda dessa tienda (seletor no topo da Agenda).
- Sem o WhatsApp CRM, a plantilla funciona, mas os botões viram **"Reservar por WhatsApp"**.
- Detalhes completos no documento da **Tienda Online** (seção "Plantilla Barbería").

### Agendar sem sair da conversa
O atendente marca a cita **de dentro do chat**: escolhe profissional, serviço, data e um dos horários livres, e o nome e telefone do cliente já vêm preenchidos. Os horários são os mesmos da página pública — nada é inventado.

### Painel da agenda
- Visão **Día** (lista do dia, com setas para avançar/voltar) e **Mes** (calendário)
- O calendário do mês mostra **semanas completas**: nos últimos dias do mês já aparecem os primeiros do mês seguinte, **com as citas** (mais claros). Para ver o mês inteiro seguinte, usar a seta **›**
- Clicar num dia do calendário abre esse dia na visão diária
- Filtros por profissional e por estado
- Estados da cita: **Pendiente · Confirmada · Completada · Cancelada · No asistió**. Marcar *No asistió* registra a falta do cliente
- **Editar profissional** (nome, telefone, horário) a qualquer momento
- Atualização **em tempo real**: uma reserva feita pelo link ou pelo bot aparece na hora para a equipe

### Avisos automáticos
- **Lembrete ao cliente** antes da consulta — escolhido na Agenda: **1, 2, 3, 6, 12 ou 24 horas antes**, ou *Sin recordatorio*
- **Aviso ao profissional** quando entra uma cita nova
- Remarcar **atualiza** o lembrete; cancelar **cancela** o lembrete
- O lembrete enviado **aparece na conversa** do cliente (remetente "Programado"), com os checks de entrega

⚠️ **Na API oficial**, o lembrete precisa de uma plantilla aprovada — porque horas antes da consulta a janela de 24h quase sempre está fechada. Na Agenda há o botão **"Activar recordatorio por WhatsApp"**: ele cria a plantilla e manda para a Meta. Enquanto a Meta não aprova, aparece **"Verificar aprobación"**. A plantilla traz dois botões para o cliente: **Confirmo asistencia** e **Reagendar** (este último abre o reagendamento pelo bot).

---

## 12. 💳 Cobros no Chat (Link de Cobro)
*Nos três planos · funciona nos dois provedores*

O atendente **cobra o cliente sem sair da conversa**. É a ponte entre o atendimento e o dinheiro entrando — o que um CRM genérico não faz.

> ⚠️ **Requisito:** o cobro precisa de uma **conta bancária integrada ao PagosYa** — **BNB** ou **Banco Económico (BANECO)**, em Configurações → Integrações *(ver doc de integrações bancárias)*. É o único recurso do CRM que depende de banco: bandeja, chatbot, IA e agenda funcionam sem ele. Quem compra só o WhatsApp entra no CRM sem cadastrar banco, e o sistema pede a integração quando ele tenta mandar o primeiro cobro. Quem não tem conta no BANECO pode pedir a abertura pelo próprio formulário.
>
> **Pergunte:** *"Você vai querer cobrar pelo WhatsApp? Tem conta no BNB ou no Banco Económico?"*

**Como funciona:**
1. No chat, toca no botão 🔗, digita **valor**, **motivo** e escolhe a **validade**
2. O cliente recebe **a imagem do QR de pagamento** com o valor e o motivo, pronta para escanear — ou para salvar e subir pela galeria no app do banco, que é como se paga na Bolívia
3. Na legenda vai também o **link**: se o QR vencer, abrir o link gera um novo
4. Quando o pagamento cai, **quem enviou o cobro** recebe um aviso na tela **com som**

**Validade do link:** 30 min · 1h · 3h · 12h · 1 dia · 3 dias · 7 dias

**Aviso só para quem enviou:** numa equipe de 5 atendentes, só o que mandou o cobro é avisado — os outros não se confundem sobre quem deve dar sequência.

### Tela "Links de Cobro"
Todos os cobros enviados pelo CRM, em tempo real:
- Totais: **Enviados · Pagados · Cobrado (Bs) · Pendente (Bs)** — seguem os filtros
- Busca por cliente, telefone ou motivo
- Filtro por estado (Pendente, Pagado) e **por atendente**
- Cada cobro mostra quem enviou, quando e o estado (Pendente · Pagado · Vencido · Cancelado)

**Frase pronta:** *"Você responde, manda o QR na mesma conversa e o sistema te avisa quando o cliente pagou. Sem ir ao app do banco conferir."*

---

## 13. 📥 Importação de Contatos
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

## 14. 📊 Métricas e Dashboard
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

## 15. 🔍 Histórico e Exportação
*Igual nos dois provedores*

Busca global em mensagens antigas, exportação em CSV ou TXT.

---

## 16. ⭐ Pesquisa de Satisfação (CSAT)
*Igual nos dois provedores*

Avaliação de 1 a 5 estrelas enviada após o atendimento, com NPS calculado e período de carência configurável (padrão 7 dias).

---

## 17. 🌐 Chat da Tienda Online (canal Web)
*Precisa de tienda online + WhatsApp CRM ativo*

Um **botão de chat** na tienda online do lojista. O visitante conversa com o **mesmo chatbot** do WhatsApp e a conversa entra **na mesma bandeja**, com o canal **Web** (ícone de globo roxo).

**Como ativar:** Tienda Online → Personalizar Tienda → **Integraciones** → **Chat en tu tienda** → ativar → Guardar Todo. Opcional: mensagem de boas-vindas.

**Como funciona para o visitante:**
1. Toca no botão de chat (canto inferior esquerdo da tienda)
2. Escreve o **nome** e, se quiser, o **WhatsApp**
3. Conversa: o bot responde na hora; links de agenda e pagamento são clicáveis

**Na bandeja:**
- Filtro **Web** e ícone do canal na lista
- Cabeçalho com o nome do visitante e o **WhatsApp que ele deixou** (um clique abre a conversa no WhatsApp)
- Mesmas ferramentas: atribuir atendente, etiquetas, etapa do pipeline, **Bot ON/OFF**, Agendar, respostas rápidas
- **Sem janela de 24h:** o atendente pode responder a qualquer momento

**É a mesma configuração do WhatsApp** (regra omnichannel): regras, IA, horário, agenda e pipeline são os do WhatsApp. Não existe configuração separada para o canal Web.

**Limitações atuais:**
- Se o visitante fechar a página, a resposta fica guardada e ele vê quando voltar à tienda (no mesmo navegador). Por isso o WhatsApp é pedido no início.
- Pesquisa de satisfação (CSAT) e modo **Webhook externo** (n8n) ainda não funcionam no canal Web.
- Envio de QR de cobrança direto no chat Web ainda não está disponível.

**Sem o WhatsApp CRM:** a opção aparece em Integraciones com o selo 🔒, e ao tentar ativar o lojista vê o aviso de compra com o botão **Comprar WhatsApp CRM**.

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

### Quem pode fazer o quê
| Ação | Funcionário (atendente) | Dono da conta |
|---|---|---|
| Ver conversas, responder, enviar mídia e plantillas | ✅ | ✅ |
| Conectar / desconectar o número | ❌ | ✅ |
| Criar plantillas novas na Meta | ❌ | ✅ |

O atendente trabalha normalmente, mas não consegue derrubar a conexão nem mexer na conta de Meta por engano.

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
- **Chat da tienda online (canal Web)** e **reservas pela plantilla Barbería** — para quem também tem tienda online
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

**Messenger e Instagram na mesma bandeja: ainda em piloto fechado.** Já funciona internamente (o mesmo chatbot e pipeline respondendo em todos os canais), mas **não está liberado para clientes**. Não prometa nem use em anúncio até ser liberado.

**O chat da tienda online (canal Web) JÁ está liberado** para todo cliente com WhatsApp CRM e tienda online. Esse pode ser oferecido.

**Chat Web e Agenda podem cair em tiendas diferentes.** As mensagens do chat Web vão para a tienda onde está o **WhatsApp** do dono (é lá que estão a bandeja e o bot). Já as reservas da plantilla Barbería vão para a Agenda da **tienda da tienda online**. Para o lojista com várias tiendas, o ideal é deixar profissionais e WhatsApp na mesma tienda.

**Quem compra só o WhatsApp (sem plano PagosYa)** entra direto no CRM, com um menu enxuto: WhatsApp CRM, Agenda, Empleados (para cadastrar os atendentes), Guia, Configurações e Suporte. Não passa pelo cadastro bancário.

## 🧑‍💻 WhatsApp API Gateway — produto separado, para desenvolvedores

**Não é o CRM.** É para empresa que já tem **ERP, CRM ou sistema próprio** e quer ligá-lo ao WhatsApp oficial sem passar pela burocracia da Meta.

| | Mensal | Anual |
|---|---|---|
| **API Gateway** | Bs 699 | Bs 6.990 |

- Acesso à **Meta Cloud API oficial** pelo PagosYa (Tech Provider)
- **API Keys** (Bearer) e **Webhooks** de mensagens e estados em tempo real
- Envio de texto, mídia e plantillas
- Logs de requisições e monitor de tráfego
- Sem limite de agentes — quem atende está no sistema do cliente
- Painel próprio em `/whatsapp-api`, com documentação

**Como diferenciar na conversa:** *"Sua equipe vai atender pela nossa tela?"* → CRM. *"Vocês já têm um sistema e querem que ele fale pelo WhatsApp?"* → API Gateway.

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
| Validade do link de cobro | **30 min a 7 dias** (7 opções) |
| Ações do assistente de IA no chat | **9** |
| Modos do chatbot | **2** (bot interno ou webhook externo) |
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
1. **Tienda online com a plantilla Barbería:** serviços, equipe e reserva dentro do site, mais a vitrine de produtos (pomadas, óleos)
2. **Chat na tienda** respondido pelo mesmo bot do WhatsApp
3. Cada profissional com **seu link de agenda**
4. Link na bio do Instagram — cliente agenda a qualquer hora
5. **Tempo de preparo** entre atendimentos, invisível para o cliente
6. **Promoções com IA** para dias parados
7. Envio para a etapa "Clientes recorrentes" do pipeline

### 🛍️ Varejo / E-commerce
1. Cliente pergunta preço no WhatsApp → atendente **manda o QR de cobro** na mesma conversa
2. O pagamento cai e o atendente **é avisado com som** — sem conferir o app do banco
3. **Importar** lista de clientes (CSV)
4. **Promoção com IA:** foto do produto → imagem → copy
5. Salvar como **plantilla** e enviar para todos
6. **Chatbot** responde rastreamento, horário e preços
7. **Métricas** de engajamento

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
Sim, de dois jeitos (o lojista escolhe na aba Agendamento do chatbot): **envia o link da agenda** para o cliente escolher, ou **agenda na própria conversa**, oferecendo 3 horários livres. Nos dois casos os horários vêm da agenda real — o bot não inventa disponibilidade.

**"Posso cobrar o cliente pelo WhatsApp?"**
Sim, nos três planos. No chat você digita o valor e o motivo, e o cliente recebe o QR para pagar. Quando ele paga, você é avisado na hora, com som. Para isso sua conta do **BNB ou do Banco Económico** precisa estar integrada ao PagosYa.

**"Já uso n8n / Make. Posso ligar ao CRM?"**
Sim. No chatbot, escolha o modo **Webhook externo**: cada mensagem recebida vai para o seu fluxo, e o que ele responder aparece no chat.

**"Tenho meu próprio sistema. Posso só usar a API do WhatsApp?"**
Sim, com o **WhatsApp API Gateway** (Bs 699/mês). É um produto separado do CRM, para desenvolvedores.

**"Funciona com Messenger e Instagram?"**
Ainda não para clientes — está em piloto. Hoje o CRM atende **WhatsApp** e o **chat da sua tienda online (canal Web)**.

**"Posso ter um chat no meu site que responda sozinho?"**
Sim, na sua **tienda online PagosYa**. Ative em Personalizar Tienda → Integraciones → Chat en tu tienda. O mesmo chatbot do WhatsApp responde, e as conversas aparecem na bandeja com o canal Web.

**"Ativei o chat da tienda e o bot não responde."**
O chatbot precisa estar **ligado** no WhatsApp CRM — é a mesma configuração. Mesmo com o bot desligado, as mensagens chegam na bandeja (filtro **Web**) para responder à mão.

**"Meus clientes podem marcar horário pela minha tienda online?"**
Sim, com a plantilla **Barbería** (outras profissões em breve). O cliente vê os horários livres reais e reserva sem sair do site.

**"Meu atendente pode desconectar o número sem querer?"**
Não. Só o dono da conta conecta, desconecta ou cria plantillas novas. O atendente responde e envia normalmente.

**"O bot continua respondendo enquanto eu atendo o cliente."**
Ligue **Pausar el bot al asignar** (Chatbot → Ajustes) e atribua a conversa a você: o bot se cala naquele contato. Ou clique no botão **Bot ON** do topo do chat para silenciá-lo na hora. Para o bot voltar, clique de novo — ele nunca volta sozinho.

**"O botão diz 'Bot en pausa'. O que aconteceu?"**
O bot se calou sozinho porque a conversa foi atribuída a um atendente ou porque o próprio bot pediu um humano. O motivo e o resumo do cliente ficam numa **nota amarela** na conversa. Para reativar, clique no botão.

**"Como deixo um recado para a equipe sem o cliente ver?"**
Use a **nota interna** (ícone de post-it na barra de escrever). Fica em amarelo na conversa com o aviso "Solo la ve tu equipo".

**"Não escuto os áudios dos clientes."**
Clique em **"Clic para cargar audio"** — ele baixa e toca. Se nada acontecer, recarregue a página com **Ctrl+F5** (o navegador pode estar com uma versão antiga do sistema).

**"Onde vejo todas as etiquetas de um contato?"**
A lista de conversas mostra só as primeiras. Clique no nome do contato dentro do chat → aba **Etiquetas**.

**"Toca o som de notificação toda hora."**
Os alertas tocam para mensagens de conversas **atribuídas a você**, quando lhe atribuem uma conversa e quando o bot pede um humano. Para silenciar naquele navegador, clique no **sino 🔔** ao lado da busca.

**"O lembrete da cita saiu? O estado diz 'Enviado' mas não sei se chegou."**
Abra a conversa do cliente: o lembrete aparece como mensagem com remetente "Programado" e os checks — ✓✓ cinza = entregue, ✓✓ azul = lido.

**"Não encontro a cita de amanhã no calendário."**
Na visão **Mes**, os primeiros dias do mês seguinte aparecem no fim do calendário. Para ver o mês inteiro, avance com a seta **›**. Na visão **Día**, avance os dias com a seta.

**"O cliente quer mudar o horário da cita."**
Com o bot no modo **Agendar en el chat**, o cliente escreve "reagendar" (ou toca *Reagendar* no lembrete) e escolhe outro horário — a cita antiga é cancelada sozinha. Também dá para remarcar pela própria Agenda.

**"Mandei uma plantilla em massa e saiu 'Hola, nombre'."**
A variável estava escrita como texto comum. Hoje o campo já vem preenchido com `{{nombre}}`, e `nombre` sozinho também é entendido. Qualquer outro texto digitado vai igual para todos os contatos.

**"Qual conexão devo usar?"**
API oficial — é a única oferecida para contas novas. Quem já está na Evolution continua funcionando e pode reconectar, mas não indicamos mais essa via: o risco de banimento do número é real e a Meta oficial resolve a mesma necessidade com plantillas.

---

*Atualizado em: outubro/2026*
*Sistema: PagosYa WhatsApp CRM*
*PagosYa é Meta Tech Provider oficial*
