# 💸 Fala Grana
## 💸 App de Finanças Pessoais com Vibe Coding 

### PRD refinado com Github Copilot e Lovable:

````markdown
# Fala Grana — PRD (Product Requirement Document)

**Versão:** 2.0  
**Data:** 2026-01-14  
**Autor:** pedroMADBR  
**Status:** MVP em Desenvolvimento

---

## 1. VISÃO GERAL DO PRODUTO

### 1.1 Descrição
Fala Grana é um aplicativo de gestão financeira pessoal que utiliza uma interface conversacional para tornar o controle de gastos tão natural quanto uma conversa. O diferencial é a entrada de dados por linguagem natural via chat, eliminando formulários complexos.

### 1.2 Tagline
**"Fala Grana — Suas finanças, só conversando"**

### 1.3 Proposta de Valor
- Controle financeiro em 30 segundos por dia
- Interface conversacional intuitiva (estilo WhatsApp)
- Sem necessidade de conectar bancos ou fornecer dados sensíveis
- Categorização automática baseada em contexto
- Acompanhamento de metas financeiras com progresso visual

---

## 2. PÚBLICO-ALVO (ICP)

### 2.1 Perfil Demográfico
| Característica | Valor Ideal |
|----------------|-------------|
| Idade | 28-35 anos |
| Renda Mensal | R$ 3.500 - R$ 6.000 |
| Localização | Capitais e regiões metropolitanas |
| Dispositivo | Mobile-first (smartphone) |
| Ocupação | CLT jovem, freelancers, MEI |

### 2.2 Perfil Psicográfico
- Heavy user de apps de mensagem (WhatsApp, Telegram)
- Já tentou controlar finanças e desistiu (planilhas, outros apps)
- Valoriza simplicidade sobre funcionalidades complexas
- Tem metas financeiras de curto/médio prazo

---

## 3. FUNCIONALIDADES IMPLEMENTADAS (MVP Atual)

### 3.1 Sistema de Autenticação
**Status:** ✅ Implementado

- Cadastro com email e senha
- Login com persistência de sessão
- Auto-confirmação de email habilitada
- Logout com redirecionamento
- Rotas protegidas para usuários autenticados

**Tecnologia:** Lovable Cloud (Supabase Auth)

### 3.2 Interface Conversacional (Chat)
**Status:** ✅ Implementado

| Funcionalidade | Descrição |
|----------------|-----------|
| Registro de transações | Usuário digita "Gastei R$ 50 no mercado" e o sistema interpreta automaticamente |
| Categorização automática | Parser identifica tipo (receita/despesa) e categoria baseado em palavras-chave |
| Títulos genéricos | Sistema gera descrições padronizadas ao invés de usar texto literal do usuário |
| Confirmação antes de salvar | Exibe card com detalhes da transação para confirmação ou edição |
| Depósitos em metas | Usuário digita "Depositei R$ 100 na meta viagem" e atualiza a meta correspondente |
| Criação de metas via chat | Se a meta não existe, abre dialog para criar nova meta com valor alvo |
| Personalização com nome | Usa o primeiro nome do usuário em saudações e mensagens |

**Palavras-chave reconhecidas:**
- **Despesas:** gastei, paguei, comprei, almocei, jantei, uber, taxi, mercado, etc.
- **Receitas:** recebi, ganhei, salário, freelance, vendas, etc.
- **Metas:** depositei, investi, guardei, coloquei, adicionei

**Tom de voz:** Amigável, brasileiro, sem julgamentos. Ex: "E aí, [Nome]! Bora dar uma olhada na sua grana?"

### 3.3 Dashboard (Tela Inicial)
**Status:** ✅ Implementado

- Saudação personalizada com nome do usuário
- Card de saldo total (receitas - despesas)
- Resumo de receitas e despesas do período
- Ações rápidas para adicionar transação e nova meta
- Lista das 5 últimas transações
- Cards de progresso das metas financeiras
- Dica educacional fixa

### 3.4 Histórico de Transações
**Status:** ✅ Implementado

- Lista completa de transações ordenada por data
- Filtros por tipo (todas, receitas, despesas)
- Busca por texto na descrição
- Cards com totais de receita e despesa
- Exibição de ícone e categoria de cada transação

### 3.5 Metas Financeiras
**Status:** ✅ Implementado

| Funcionalidade | Descrição |
|----------------|-----------|
| Listagem de metas | Cards com título, ícone, prazo e progresso visual |
| Barra de progresso | Mostra percentual atingido da meta |
| Valores | Exibe valor atual, valor alvo e restante |
| Prazo | Calcula e exibe dias restantes (quando definido) |
| Sugestão de depósito | Calcula valor mensal sugerido para atingir a meta |
| Criação via chat | Usuário pode criar metas conversando |
| Depósitos via chat | Usuário pode depositar em metas existentes pelo chat |

### 3.6 Gerenciamento de Categorias
**Status:** ✅ Implementado

- Categorias personalizáveis por usuário
- Categorias separadas para receitas e despesas
- CRUD completo (criar, editar, excluir)
- Seleção de ícone (emoji) para cada categoria
- Categorias padrão pré-configuradas

**Categorias padrão de despesas:**
Alimentação, Transporte, Moradia, Saúde, Lazer, Compras, Educação, Contas, Investimentos, Outros

**Categorias padrão de receitas:**
Salário, Freelance, Investimentos, Outros

### 3.7 Perfil do Usuário
**Status:** ✅ Implementado

- Exibição de email e nome do usuário
- Seletor de tema (Claro, Escuro, Sistema)
- Menu de configurações (Categorias, Notificações, Privacidade, Exportar, Ajuda)
- Botão de logout
- Acesso ao gerenciador de categorias

### 3.8 Design System
**Status:** ✅ Implementado

| Elemento | Especificação |
|----------|---------------|
| Cor primária | Verde Grana #00D98C |
| Cor secundária | Azul Confiança #2D3E50 |
| Cor de alerta | Amarelo #FFB800 |
| Cor de erro | Vermelho #E63946 |
| Tipografia | Inter (Regular, Medium, SemiBold, Bold) |
| Dark mode | Suportado com cores ajustadas |
| Logo | "Fala" (azul) + "Grana" (verde) |

---

## 4. ARQUITETURA TÉCNICA

### 4.1 Frontend
- **Framework:** React 18 + TypeScript
- **Bundler:** Vite
- **Estilização:** Tailwind CSS + shadcn/ui
- **Roteamento:** React Router DOM
- **Estado:** Context API (AuthContext, FinanceContext)
- **Formulários:** React Hook Form + Zod

### 4.2 Backend (Lovable Cloud)
- **Banco de dados:** PostgreSQL (Supabase)
- **Autenticação:** Supabase Auth
- **Segurança:** RLS (Row-Level Security) em todas as tabelas

### 4.3 Estrutura do Banco de Dados

**Tabela: transactions**
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | uuid | Identificador único |
| user_id | uuid | ID do usuário (RLS) |
| type | text | 'income' ou 'expense' |
| amount | numeric | Valor da transação |
| category | text | ID da categoria |
| description | text | Descrição da transação |
| date | date | Data da transação |
| created_at | timestamp | Data de criação |

**Tabela: goals**
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | uuid | Identificador único |
| user_id | uuid | ID do usuário (RLS) |
| title | text | Nome da meta |
| target_amount | numeric | Valor alvo |
| current_amount | numeric | Valor atual (default: 0) |
| deadline | date | Prazo (opcional) |
| color | text | Cor do card |
| icon | text | Emoji do ícone |
| created_at | timestamp | Data de criação |

**Tabela: categories**
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | uuid | Identificador único |
| user_id | uuid | ID do usuário (RLS) |
| type | text | 'income' ou 'expense' |
| label | text | Nome da categoria |
| icon | text | Emoji do ícone |
| created_at | timestamp | Data de criação |

---


## 5. REQUISITOS NÃO-FUNCIONAIS

### 5.1 Performance
- Tempo de resposta do chat: < 2 segundos
- Carregamento inicial: < 3 segundos
- Funcionamento offline: Não suportado (requer conexão)

### 5.2 Acessibilidade (WCAG 2.2 AA)
- Contraste mínimo texto/fundo: 4.5:1
- Touch targets: mínimo 44x44px
- Fonte base: 16px
- Suporte a dark mode
- Navegação por teclado
- Labels em elementos interativos

### 5.3 Segurança
- Autenticação obrigatória para acesso
- RLS em todas as tabelas (usuário só vê seus dados)
- LGPD: Não coleta dados bancários ou CPF
- Criptografia em trânsito (HTTPS)

### 5.4 Compatibilidade
- Mobile-first (design responsivo)
- Browsers: Chrome, Safari, Firefox, Edge (últimas 2 versões)
- PWA: Não implementado

---

## 6. MÉTRICAS DE SUCESSO

### 6.1 Produto
| Métrica | Meta |
|---------|------|
| Taxa de ativação (1+ transação em 7 dias) | ≥ 40% |
| Tempo médio de registro | < 30 segundos |
| Retenção D7 | ≥ 25% |
| Retenção D30 | ≥ 15% |

### 6.2 Experiência
| Métrica | Meta |
|---------|------|
| NPS (early adopters) | > 30 |
| Recomendaria para amigos | ≥ 60% |
| Menciona "simples/fácil" no feedback | ≥ 70% |

---

## 7. CONSIDERAÇÕES FINAIS

### 7.1 O que o MVP faz bem
- Interface conversacional funcional
- Registro rápido de transações por texto
- Depósitos em metas via chat
- Criação de metas com valor inicial pelo chat
- Design system alinhado com brand book
- Tom de voz consistente e amigável
- Categorização automática básica

### 7.2 Limitações conhecidas
- Parser de linguagem natural usa regex (não IA)
- Não há edição/exclusão de metas pela interface visual
- Onboarding não implementado
- Sem gráficos ou visualizações avançadas
- Sem notificações/lembretes

---
**Versão:** 2.0  
**Última atualização:** 19/01/2026  

````


### Interações de Vibe Coding:

> Criar o App no Lovable com o PRD do Github Copilot: (PRD)
> Refinamento de funções e outras correções no Lovable
> Criação de Brand Book com o Github Copilot para guiar melhor a identidade do App no Lovable
> Criação de ICP no Github Copilot 
> Ajustar identidade de marca com o Lovable: (Brand Book) (ICP)
> Ajustes finais para corrigir funcionalidades

### Resultado Final no Lovable: https://chat-fala-grana.lovable.app/

<img width="1268" height="832" alt="image" src="https://github.com/user-attachments/assets/04e7afbd-64ac-409d-b945-305468c7d860" />

## Resumo do Site:

**Fala Grana** é um aplicativo de gestão financeira pessoal com interface conversacional que torna o controle de gastos tão natural quanto uma conversa no WhatsApp.

**Tagline:** "Fala Grana — Suas finanças, só conversando"

---

## Funcionalidades Principais

### 1. Interface Conversacional (Chat)
- **Registro de transações por linguagem natural**
  - Exemplo: "Gastei R$ 50 no mercado" é interpretado automaticamente
  - Palavras-chave reconhecidas: gastei, paguei, comprei, recebi, salário, etc.
- **Categorização automática** baseada em contexto
- **Depósitos em metas via chat**
  - Exemplo: "Depositei R$ 100 na meta viagem"
- **Criação de metas conversando**
  - Se a meta não existe, o sistema abre diálogo para criar
- **Confirmação antes de salvar** qualquer operação
- **Personalização com nome** do usuário em saudações

### 2. Dashboard (Tela Inicial)
- **Saudação personalizada** ("E aí, [Nome]!")
- **Card de saldo total** em destaque
  - Resumo de receitas totais
  - Resumo de despesas totais
  - Cálculo automático do saldo (receitas - despesas)
- **Gráfico de gastos por categoria** (pizza)
  - Distribuição percentual visual
  - Legenda com cores por categoria
- **Gráfico de evolução do saldo** (linha temporal)
- **Ações rápidas**
  - Adicionar nova transação
  - Criar nova meta
- **Últimas 5 transações** listadas
- **Cards de metas financeiras** com progresso visual
- **Dica educacional** fixa

### 3. Gerenciamento de Transações
- **Histórico completo** ordenado por data (mais recente primeiro)
- **Filtros por tipo**
  - Todas as transações
  - Apenas receitas
  - Apenas despesas
- **Busca por texto** na descrição
- **Cards com totais** de receita e despesa do período
- **Exibição detalhada** de cada transação
  - Ícone da categoria
  - Nome da categoria
  - Valor formatado
  - Data

### 4. Metas Financeiras
- **Criação de metas** com: 
  - Título personalizado
  - Valor alvo
  - Prazo (opcional)
  - Ícone (emoji)
  - Cor do card
- **Visualização de progresso**
  - Barra de progresso visual (percentual)
  - Valor atual vs.  valor alvo
  - Valor restante para atingir
  - Dias restantes até o prazo
  - Sugestão de depósito mensal calculada automaticamente
- **Depósitos**
  - Via chat conversacional
  - Atualização automática do progresso

### 5. Categorias Personalizáveis
- **CRUD completo** (criar, editar, excluir)
- **Categorias separadas** para receitas e despesas
- **Seleção de ícone** (emoji) para cada categoria
- **Categorias padrão pré-configuradas:**
  - **Despesas:** Alimentação, Transporte, Moradia, Saúde, Lazer, Compras, Educação, Contas, Investimentos, Outros
  - **Receitas:** Salário, Freelance, Investimentos, Outros

### 6. Perfil e Configurações
- **Informações do usuário**
  - Exibição de nome
  - Exibição de email
- **Seletor de tema** (Claro, Escuro, Sistema)
- **Menu de configurações**
  - Gerenciar categorias
  - Notificações (planejado)
  - Privacidade
  - Exportar dados (planejado)
  - Ajuda e suporte
- **Logout** com redirecionamento

### 7. Autenticação e Segurança
- **Cadastro** com email e senha
- **Login** com persistência de sessão
- **Auto-confirmação de email** habilitada
- **Rotas protegidas** para usuários autenticados
- **Row-Level Security (RLS)** - cada usuário vê apenas seus dados
- **Conformidade LGPD**
  - Não coleta dados bancários
  - Não requer CPF
  - Criptografia em trânsito (HTTPS)

---

## Navegação

A interface possui **5 abas principais** no menu inferior:

1. **Início** - Dashboard com saldo, gráficos e resumo
2. **Chat** - Interface conversacional para registrar transações e metas
3. **Transações** - Histórico completo com filtros e busca
4. **Metas** - Gerenciamento de objetivos financeiros
5. **Perfil** - Configurações e personalização

---

## Diferenciais

- **Controle em 30 segundos/dia** via chat
- **Sem conexão bancária** necessária (privacidade total)
- **Categorização automática** inteligente
- **Tom de voz amigável** e brasileiro (sem julgamentos)


## Reflexão

 ### O que funcionou bem?  
 Conhecer os tipos de documentação que podem ajudar a montar um bom projeto como o PRD e o ICP foram ótimos pontos iniciais que refinei no Github Copilot. O Lovable foi uma ótima ferramenta para vibe coding e que realmente fez tudo majoritalmente como imaginei e com ótimos resultados
 
 ### O que não funcionou como o esperado? 
 Gostaria de poder interagir por mais tempo com o Lovable no dia a dia, além disso o lovable teve dificuldade em criar a IA de início no site que desenhei e em outros momentos senti que os créditos diários acabaram muito rapidamente
 
 ### O que aprendeu sobre conversar com IAs?
 É possível e já viável realizar vibe coding de forma funcional e que gere bons produtos. É realmente um novo capítulo para a TI e o desenvolvimento de software

 ### Brand Book refinado com Github Copilot:

````markdown
# Fala Grana — Brand Book

**Versão:** 1.0  
**Data:** 2026-01-08  
**Autor:** pedroMADBR

---

## 1. ESSÊNCIA DA MARCA

### Missão
Tornar o controle financeiro tão natural quanto uma conversa, empoderando brasileiros a alcançarem suas metas sem fricção ou complexidade.

### Visão
Ser o primeiro app de finanças que as pessoas querem abrir todo dia — não por obrigação, mas porque é simples, útil e humano.

### Valores

1. **Conversação, não Complicação**  
   Finanças devem ser tão fáceis quanto mandar um áudio no WhatsApp

2. **Acessível para Todos**  
   Design Universal:  funciona para Ana de 28, Maria de 50, e qualquer pessoa entre elas

3. **Transparência Radical**  
   Sem jargões, sem pegadinhas, sem taxas escondidas.  Clareza em tudo.  

4. **Progresso > Perfeição**  
   Começar pequeno é melhor que não começar.  Celebramos cada R$ economizado.

5. **Privacidade Inegociável**  
   Seus dados são seus.  Ponto.

---

## 2. IDENTIDADE VISUAL

### Paleta de Cores

#### Cores Primárias

**Verde Grana** (Principal)
```css
--color-primary: #00D98C;
--color-primary-hover: #00E599;
--color-primary-active: #00B372;
```
- **Uso:** CTAs, progresso de metas, confirmações, logo
- **Significado:** Crescimento, dinheiro (grana), otimismo

**Azul Confiança** (Secundário)
```css
--color-secondary: #2D3E50;
--color-text-primary: #2D3E50;
```
- **Uso:** Textos principais, ícones, headers
- **Significado:** Confiança, segurança, profissionalismo

#### Cores de Apoio

```css
--color-warning: #FFB800;      /* Avisos, dicas */
--color-danger: #E63946;       /* Alertas, erros */
--color-success: #00D98C;      /* Mesma cor primária */

--color-bg-light: #F5F7FA;     /* Background claro */
--color-bg-white: #FFFFFF;     /* Cards, modals */

--color-text-secondary: #A0AEC0; /* Textos secundários */
--color-border: #E2E8F0;       /* Bordas, divisores */
```

#### Dark Mode

```css
--color-bg-dark:  #1A202C;           /* Background escuro */
--color-primary-dark: #00E599;      /* Verde ajustado para contraste */
--color-text-dark: #E2E8F0;         /* Texto principal dark */
--color-text-secondary-dark: #A0AEC0;
--color-card-dark: #2D3E50;         /* Cards em dark mode */
```

**Regra de Contraste:** Todos os pares texto/fundo devem ter **mínimo 4. 5:1** (WCAG AA)

---

### Tipografia

**Fonte Principal:  Inter**

```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

**Hierarquia:**

```css
/* Títulos */
--font-h1: Inter Bold, 48px / 56px (line-height);   /* Desktop */
--font-h1-mobile: Inter Bold, 32px / 40px;          /* Mobile */

/* Subtítulos */
--font-h2: Inter SemiBold, 24px / 32px;

/* Corpo */
--font-body: Inter Regular, 16px / 24px;  /* Base WCAG */

/* Labels/Botões */
--font-button: Inter Medium, 16px / 20px;

/* Captions */
--font-caption: Inter Regular, 14px / 20px;
```

**Pesos disponíveis:**
- Regular (400) - Textos
- Medium (500) - Botões, labels
- SemiBold (600) - Subtítulos
- Bold (700) - Títulos, ênfase

---

### Logotipo

#### Versões

1. **Logo Completo** (Ícone + Wordmark)
   - Uso: Header do app, site, materiais oficiais
   - Tamanho mínimo: 120px largura

2. **Ícone Sozinho**
   - Uso: App icon, favicon, redes sociais
   - Tamanho mínimo: 24x24px

3. **Monocromático**
   - Uso: Parceiros, impressões, fundos coloridos
   - Versões: Verde (#00D98C), Branco (#FFFFFF), Preto (#2D3E50)

#### Anatomia do Logo

```
Ícone:  Balão de fala arredondado com símbolo R$ estilizado
- Cor: Verde Grana #00D98C
- Estilo: Flat, minimalista, arredondado

Wordmark: "Fala Grana"
- "Fala":  Azul Confiança #2D3E50
- "Grana": Verde Grana #00D98C
- Fonte: Inter Bold
- Espaçamento ícone-texto: 16px
```

#### Área de Proteção

Manter espaço mínimo equivalente a **metade da altura do ícone** em todos os lados. 

---

## 3. TOM DE VOZ

### Personalidade

Se Fala Grana fosse uma pessoa: 
- Amigo próximo (não chefe, não professor)
- Otimista (celebra vitórias pequenas)
- Esperto, mas não pedante
- Confiável (está do seu lado)
- Brasileiro raiz

### Diretrizes de Tratamento

**FAZER:**
- Usar o nome da pessoa quando disponível ("Ana, anotado!")
- Quando não souber o nome, falar diretamente sem pronome ("Anotado!", "Bora lá")
- Em contextos onde pronome é necessário, usar "você" de forma natural
- Nunca usar "senhor/senhora" ou tratamentos formais

**Exemplos corretos:**
```
"Ana, conseguiu economizar R$ 200 esse mês!"
"Anotado! R$ 45 no mercado."
"Bora criar sua primeira meta?"
"Quanto gastou no almoço?"
```

**Exemplos INCORRETOS:**
```
❌ "Você conseguiu economizar..." (redundante quando tem nome)
❌ "Senhor João, o senhor gastou..."
❌ "Caro usuário..."
```

### Diretrizes de Linguagem

**FAZER:**
- Verbos no imperativo amigável: "Fala pra gente", "Bora", "Vem ver"
- Gírias brasileiras leves: "grana", "tá rolando", "tranquilo", "beleza"
- Contrações naturais: "tá", "pra", "né"
- Mensagens curtas (máximo 2 linhas no chat)
- Perguntas abertas: "Como foi o dia financeiro?", "Qual a meta?"

**NÃO FAZER:**
- Jargões sem explicação: "amortização", "CDI", "yield"
- Tom bancário/corporativo: "Prezado cliente", "Vossa Excelência"
- Julgar gastos: ❌ "Gastou DEMAIS" → "Gastinho acima do normal"
- Promessas vazias: "Fique rico rápido", "Método infalível"
- Textos longos e densos
- Usar emojis em excesso (máximo 1 por mensagem em contextos informais)

### Exemplos de Mensagens por Contexto

#### Onboarding
```
Oi! Sou o Fala Grana. 
Vou te ajudar a organizar sua grana de um jeito simples:  só conversando. 

Bora começar? Qual sua maior meta agora?
```

#### Transação Registrada (com nome)
```
Anotado, Ana! R$ 45 no mercado. 
Quer que eu lembre de fazer lista de compras na próxima? 
```

#### Transação Registrada (sem nome)
```
Anotado! R$ 45 no mercado. 
Quer lembrete pra lista de compras na próxima?
```

#### Meta Próxima de Ser Atingida
```
Olha só, João! 
Faltam só R$ 200 pra bater a meta de R$ 3. 000.
Tá quase!  Bora manter o ritmo? 
```

#### Erro ou Não Compreendeu
```
Ops, não entendi direito. 
Pode repetir de outro jeito?  Tipo:  'Gastei R$ 50 no Uber'
```

#### Dica do Agente Financeiro
```
Maria, notei que o mercado tá pesando no orçamento. 
Quer ajuda pra montar uma lista de compras e economizar uns 10% por semana?
```

#### Primeira Meta Criada
```
Primeira meta criada! R$ 3.000 em 6 meses.
Vou te ajudar a chegar lá.  Combinamos de registrar os gastos todo dia? 
```

---

## 4. COMPONENTES UI

### Botões

**Primário (CTA Principal)**
```css
background: var(--color-primary);
color: #FFFFFF;
border-radius:  12px;
padding: 14px 24px;
min-height: 44px; /* WCAG touch target */
font:  var(--font-button);
box-shadow: 0 2px 4px rgba(0,0,0,0.1);

/* Estados */
hover: background #00E599;
active: background #00B372;
disabled:  background #A0AEC0, cursor not-allowed;
```

**Secundário**
```css
background: transparent;
color: var(--color-primary);
border: 2px solid var(--color-primary);
/* Resto igual ao primário */
```

### Cards

```css
background: #FFFFFF; /* light mode */
background: var(--color-card-dark); /* dark mode */
border-radius: 16px;
padding: 20px;
box-shadow: 0 4px 12px rgba(0,0,0,0.08);
```

### Inputs (Chat)

```css
background: var(--color-bg-light);
border: 1px solid var(--color-border);
border-radius: 24px; /* Estilo bolha de chat */
padding: 12px 20px;
font:  var(--font-body);
min-height: 48px;

/* Focus */
border-color: var(--color-primary);
outline: 2px solid rgba(0,217,140,0.2);
```

---

## 5. ACESSIBILIDADE (WCAG 2.2 AA)

### Checklist Obrigatório

- Contraste texto/fundo maior ou igual a 4.5:1
- Tamanho mínimo de fonte: 16px
- Touch targets:  mínimo 44x44px
- Foco visível em todos os elementos interativos
- Textos alternativos em imagens e ícones
- Suporte a zoom até 200% sem quebra de layout
- Navegação por teclado funcional (Tab, Enter, Esc)
- Compatível com leitores de tela (TalkBack/VoiceOver)
- Não depender exclusivamente de cor para transmitir informação
- Respeitar preferência de movimento reduzido (prefers-reduced-motion)

### Testes Requeridos

Antes de cada release:
1. Testar com leitor de tela (VoiceOver/TalkBack)
2. Navegar apenas com teclado (Tab, Enter, Esc)
3. Validar contraste com WebAIM Contrast Checker
4. Testar com zoom 200%
5. Validar com usuários reais (incluindo personas com necessidades especiais)

---

## 6. SLOGAN E MENSAGENS

**Tagline Principal:**
> "Fala Grana — Suas finanças, só conversando"

**Alternativas (contextos específicos):**
- "Finanças que entendem você" (empático)
- "Fale, nós organizamos" (funcional)
- "Sua grana, sua conversa" (autonomia)

**Elevator Pitch:**
> "Fala Grana é o app que organiza suas finanças por conversa. Fale 'gastei R$ 50 no Uber', a gente registra, categoriza e ainda te ajuda a alcançar suas metas.  É tipo ter um amigo financeiro no bolso — sem julgamento, só ajuda."

---

## 7. CHECKLIST DE CONSISTÊNCIA

Antes de lançar qualquer material, verificar:

- As cores seguem a paleta definida? 
- A fonte é Inter (ou exceções aprovadas)?
- O tom de voz é amigável e brasileiro?
- O tratamento está correto (nome da pessoa ou direto, sem "você" desnecessário)?
- Está acessível (contraste, alt text)?
- O logo está no tamanho e versão corretos?
- A mensagem reflete nossos valores? 
- Foi testado em dark mode?

---

**Versão:** 1.0 — Atualizado em 08/01/2026  
````

### ICP (Ideal Costumer Profile) refinado com Github Copilot:
````markdown
# Fala Grana — ICP (Ideal Customer Profile)

**Versão:** 1.0  
**Data:** 2026-01-08  
**Autor:** pedroMADBR

---

## O que é este documento?

**ICP (Ideal Customer Profile)** define o perfil do cliente perfeito para o Fala Grana — aquele que tem maior probabilidade de: 
- Aderir facilmente (baixo CAC - Custo de Aquisição de Cliente)
- Permanecer ativo (alta retenção)
- Recomendar para outros (alto NPS - Net Promoter Score)

---

## PERFIL DEMOGRÁFICO

| Característica | Valor Ideal | Faixa Aceitável |
|----------------|-------------|-----------------|
| **Idade** | 28-35 anos | 25-45 anos |
| **Localização** | Capitais e regiões metropolitanas | Brasil urbano |
| **Renda Mensal** | R$ 3.500 - R$ 6.000 | R$ 2.500 - R$ 8.000 |
| **Classe Social** | Classe C alta / B baixa | C/B |
| **Escolaridade** | Superior incompleto/completo | Ensino médio+ |
| **Ocupação Principal** | CLT jovem ou freelancer | Variado |
| **Dispositivo** | Smartphone Android/iOS | Mobile-first |

### Distribuição por Ocupação

- 40% — CLT em início/meio de carreira (até 8 anos de experiência)
- 35% — Freelancers, autônomos, profissionais liberais
- 25% — Empreendedores MEI ou pequenos negócios

---

## PERFIL PSICOGRÁFICO

### Mentalidade Financeira Atual

**Pensamentos típicos:**
- "Sei que preciso controlar meus gastos, mas apps são chatos"
- "Tentei planilha e desisti em 1 semana"
- "Quero ter uma reserva, mas não sei por onde começar"
- "Uso WhatsApp e Instagram o dia todo, finanças deviam ser assim também"

### Valores que Guiam Decisões

1. **Simplicidade > Funcionalidades complexas**
   - Prefere app com 3 recursos bem-feitos do que 20 confusos

2. **Autonomia > Dependência de especialistas**
   - Quer aprender sozinho, no seu ritmo

3. **Transparência > Jargões técnicos**
   - Valoriza linguagem clara, sem "economês"

4. **Progresso gradual > Transformação overnight**
   - Realista:  sabe que não vai "ficar rico rápido"

### Frustrações com Soluções Atuais

1. **Apps bancários tradicionais:**
   - Interface confusa, difícil de entender
   - Muita propaganda de empréstimo e produtos

2. **GuiaBolso / Mobills:**
   - Muito trabalho manual para categorizar
   - Interface poluída, excesso de informação

3. **Planilhas (Excel/Sheets):**
   - Dá preguiça abrir e preencher
   - Muito técnico, não é intuitivo

4. **Consultores financeiros:**
   - Caro demais para a realidade atual
   - Vergonha de expor a situação financeira

### Comportamento Digital

- Heavy user de apps de mensagem (WhatsApp, Telegram)
- Consome conteúdo em vídeos curtos (Reels, TikTok, YouTube Shorts)
- Prefere áudio a texto (usa áudios no WhatsApp)
- Ativo em redes sociais (compartilha ferramentas úteis)
- Atenção fragmentada (precisa de micro-interações, não longos formulários)

---

## PERFIL COMPORTAMENTAL (Financeiro)

### Situação Financeira Atual

**Controle de gastos:**
- 80% — Sem controle formal
- 15% — Já tentou e desistiu
- 5% — Controla minimamente (queremos capturar antes de virarem power users de concorrentes)

**Reservas:**
- 60% — Nenhuma reserva de emergência
- 30% — 0-3 meses de reserva
- 10% — 3+ meses (early adopters que querem otimizar)

**Dívidas:**
- 50% — Dívidas pequenas (cartão, parcelamentos)
- 30% — Sem dívidas, mas também sem sobra
- 20% — Endividamento moderado (querem sair da situação)

**Investimentos:**
- 70% — Nenhum investimento além de poupança
- 20% — Tesouro Direto ou CDB básico
- 10% — Portfólio diversificado (não é foco do MVP)

### Gatilhos de Adesão

**Eventos de vida que levam ao Fala Grana:**

1. **Meta específica surgiu**
   - "Quero viajar em 6 meses"
   - "Vou casar ano que vem"
   - "Preciso trocar de carro"

2. **Mudança de responsabilidade**
   - Casamento / união estável
   - Nascimento de filho
   - Primeiro emprego formal

3. **"Susto financeiro"**
   - Conta chegou e não tinha dinheiro
   - Percebeu que gastou todo o salário em 10 dias
   - Dívida começou a crescer

4. **Renda extra chegou**
   - Recebeu aumento
   - Freelance rentável
   - Herança ou venda de bem

### Objeções Típicas

| Objeção | Resposta do Fala Grana |
|---------|------------------------|
| "Mais um app, não tenho tempo" | "30 segundos por dia.  Só conversando." |
| "Será que é difícil?" | "Se manda áudio no WhatsApp, já sabe usar" |
| "Meus dados estão seguros?" | "LGPD 100%.  Criptografia.  Controle total dos seus dados." |
| "Precisa conectar no banco?" | "Não!  Fala suas movimentações, nós organizamos" |

---

## JORNADA DE DECISÃO

### 1. Awareness (Consciência)

**Como descobrem o Fala Grana:**

- 60% — Recomendação de amigo/familiar (word-of-mouth)
- 25% — Conteúdo educacional (Instagram/TikTok:  "finanças descomplicadas")
- 10% — Busca Google/YouTube:  "app simples controlar gastos"
- 5% — Anúncios pagos (remarketing)

**Conteúdos que atraem:**
- "3 apps que mudam sua relação com dinheiro"
- "Como economizar R$ 500/mês sem sofrer"
- "Controle financeiro por conversa?  Testei!"

### 2. Consideração

**Primeiros 5 minutos são críticos:**

1. **Download** (App Store / Google Play)
   - Decisão baseada em:  nota alta (4.5+), screenshots claros, descrição simples

2. **Onboarding** (máximo 2 minutos)
   - Pede apenas:  nome, principal meta, permissão de notificações
   - Se pedir menos:  usuário fica
   - Se pedir CPF, dados bancários:  usuário desinstala

3. **Primeira transação** (momento da verdade)
   - Testa falar:  "Gastei R$ 20 no almoço"
   - Se funcionar bem: "uau, é isso mesmo!"
   - Se não entender ou bugar: desinstala

### 3. Decisão (Virar usuário ativo)

**Fatores de conversão:**

- App respondeu rápido (menor que 2 segundos)
- Entendeu linguagem natural (não precisou seguir template rígido)
- Interface bonita e clara
- Sentiu que "entende minha vida" (não julga)

**Primeira semana:**
- Meta:  registrar 3+ transações
- Se atingir: 70% chance de virar usuário ativo em 30 dias
- Se não atingir: alta probabilidade de churn (abandono)

### 4. Retenção (Virar evangelista)

**O que faz permanecer:**

1. Ver progresso visual nas metas (sensação de conquista)
2. Dicas do agente que realmente ajudam (não genéricas)
3. Notificações úteis (não spam)
4. Sentir que está evoluindo financeiramente

**Quando recomendam:**
- Amigo reclama de dinheiro apertado:  "Baixa o Fala Grana!"
- Conseguiu bater uma meta: Post no Instagram/stories

---

## INDICADORES DE FIT PERFEITO

### Cliente Ideal tem 4+ destes sinais:

- Usa WhatsApp ou Telegram diariamente
- Já tentou controlar finanças antes (planilha, app) e falhou
- Tem meta financeira clara nos próximos 6-12 meses
- Compartilha apps e ferramentas úteis com amigos
- Renda entre R$ 2.5k-8k (tem margem para economizar)
- Valoriza design e experiência (não aceita app "feio")
- Smartphone como dispositivo principal (não usa PC para finanças)
- Ativo em redes sociais

### NÃO é fit se:

- Quer day trade ou investimentos avançados (fora do escopo MVP)
- Prefere planilhas Excel (perfil muito técnico/controlador)
- Precisa controle multi-empresa/CNPJ (B2B, não B2C)
- Não tem smartphone ou dados móveis
- Resistente a apps em geral (usuário analógico)

---

## MÉTRICAS DE VALIDAÇÃO DO ICP

**Como saber se estamos atingindo o ICP certo:**

### Dados Demográficos (Analytics)

```
Idade média: 28-35 anos (validado)
Localização: 70%+ em capitais (validado)
Dispositivo: 90%+ mobile (validado)
```

### Comportamento (Produto)

```
Taxa de ativação (1+ transação em 7 dias): maior ou igual a 40%
Tempo médio de registro: menor que 30 segundos
Retenção D7:  maior ou igual a 25%
Retenção D30: maior ou igual a 15%
```

### Qualitativo (Feedback)

```
NPS maior que 30 entre early adopters
"Recomendaria para amigos":  maior ou igual a 60%
Menciona "simples/fácil" no feedback:  maior ou igual a 70%
```

---

## SEGMENTAÇÃO POR PRIORIDADE

### Tier 1 (Foco Máximo) — 60% dos esforços

**Persona:** Ana, 28 anos
- CLT, R$ 3.5k-5k/mês
- Quer juntar para viagem ou casamento
- Usuária heavy de apps de mensagem
- Tentou Mobills e achou chato
- Instagram e TikTok diário

**Canais:** Instagram, TikTok, word-of-mouth

### Tier 2 (Foco Secundário) — 30% dos esforços

**Persona:** João, 35 anos
- Freelancer, renda variável
- Precisa de reserva de emergência
- Usa planilha mas desiste frequentemente
- Valoriza autonomia

**Canais:** LinkedIn, YouTube, comunidades de freelancers

### Tier 3 (Oportunista) — 10% dos esforços

**Persona:** Maria, 50 anos
- CLT sênior ou aposentada
- Quer reduzir despesas para investir
- Menos tech-savvy, mas aprende rápido
- Valoriza simplicidade extrema

**Canais:** Facebook, WhatsApp, boca a boca familiar

---

## TEMPLATE DE QUALIFICAÇÃO

**Use este checklist ao analisar novos usuários:**

```
[ ] Idade 25-45 anos? 
[ ] Renda R$ 2.5k-8k? 
[ ] Usa smartphone como dispositivo principal?
[ ] Tem meta financeira nos próximos 12 meses?
[ ] Frustrado com soluções atuais (planilha/apps)?
[ ] Ativo em redes sociais? 

Se 5+ "Sim" — ICP Perfeito (investir marketing)
Se 3-4 "Sim" — ICP Aceitável (monitorar)
Se menor que 3 "Sim" — Não é fit (não investir recursos)
```

---

**Versão:** 1.0 — Atualizado em 08/01/2026  
````
