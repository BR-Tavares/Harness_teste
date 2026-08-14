# Plano de Tarefas Arquiteturais: F01 (v0)

---

## 📑 Metadados de Auditoria (Architect Provenance)
- **Identidade do Arquiteto:** `Agente 2 (Plan Architect)`
- **Framework:** `REPLICABLE_HARNESS v6`
- **Data e Horário do Planejamento:** `2026-08-14T13:10:00Z` *(Simulado)*
- **Status do Plano:** Ativo (plan_v0.md)
- **Feature Alvo:** `F01` — Página de Status de Desenvolvimento do Repositório Harness_teste

---

## 🏗️ 1. Estratégia Arquitetural (Architectural Strategy)

A arquitetura para a **Página de Status de Desenvolvimento** baseia-se no paradigma *Vanilla Web*, garantindo zero dependência de cadeias de compilação (build steps) e máxima portabilidade. O Build Runner deverá implementar a solução utilizando a seguinte topologia de arquivos:

**Estrutura de Diretórios Proposta:**
```text
src/
├── index.html        (Estrutura semântica e ponto de entrada)
├── css/
│   └── styles.css    (Design System via CSS Variables, Grid/Flexbox, Animações)
└── js/
    └── app.js        (Lógica de simulação do console e interatividade)
```

**Decisões Técnicas:**
- **HTML:** Uso de tags semânticas (`<header>`, `<main>`, `<section>`, `<article>`).
- **CSS:** Adoção de uma abordagem *Mobile-First* com Media Queries. O estado global de design (cores, espaçamentos) será ancorado na pseudo-classe `:root`.
- **JavaScript:** Padrão de módulo (ES6) ou script deferido (`<script defer>`), manipulando o DOM nativamente (`document.getElementById`, `createElement`, etc.) sem frameworks reativos.

---

## 🚫 2. Prevenção de Deriva Cognitiva (Anti-Drift Anchoring)

Para garantir a conformidade com o **ARTIGO 4** da Constituição, o Build Runner deve operar sob as seguintes restrições absolutas:

- **INVARIANTS TOUCHED:**
  - **ARTIGO 1:** O Build Runner atuará apenas nos arquivos dentro do diretório `src/`. É estritamente proibido modificar arquivos em `governance/`, `.github/workflows/` ou a especificação.
  - **ARTIGO 3:** O sucesso do PR será medido deterministicamente. O Build Runner deve focar primariamente nas sub-issues marcadas como **MUST HAVE**.
- **NON-GOALS (Limites de Escopo):**
  - **NÃO** inicializar projetos Node.js (`npm init`, `package.json`).
  - **NÃO** importar bibliotecas externas via CDN (ex: Tailwind, React, jQuery).
  - **NÃO** implementar chamadas `fetch()` ou `XMLHttpRequest` para APIs reais.
  - **NÃO** utilizar `localStorage` ou `sessionStorage` para persistência de estado.

---

## 📋 3. Decomposição em Sub-issues MoSCoW (Execution Plan)

O Build Runner (Antigravity Desktop) deve executar as seguintes sub-issues sequencialmente. O laço de autoafinação (3-retry) deve ser utilizado para garantir a entrega dos requisitos SHOULD HAVE.

### 🔴 Sub-issue 1: Fundação Estrutural e Identidade (MUST HAVE)
**Objetivo:** Estabelecer o esqueleto do projeto e o cabeçalho semântico.
**Tarefas:**
1. Criar o diretório `src/` e os arquivos `index.html`, `css/styles.css` e `js/app.js`.
2. Configurar o boilerplate do HTML5 em `index.html`, linkando o CSS e o JS.
3. Implementar a tag `<header>` contendo o título exato `"Status - Harness_teste"`.
4. Adicionar no cabeçalho um hiperlink (`<a>`) com o texto `"Harness Central"` apontando para `#`.
**Critérios de Aceite:** `[M01]`, `[M02]` atendidos integralmente.

### 🔴 Sub-issue 2: Superfície de Telemetria e Matriz MoSCoW (MUST & SHOULD HAVE)
**Objetivo:** Construir os painéis visuais de estado e pontuação com design responsivo.
**Tarefas:**
1. Definir variáveis CSS (`:root`) em `styles.css` para cores (primária, secundária, sucesso, alerta, erro), tipografia e espaçamentos **(SHOULD - S02)**.
2. Criar uma seção no HTML para os "Indicadores de Estágio". Adicionar 3 cards/badges visuais com os textos: `"GitHub Actions (Stage 1)"`, `"GitHub Actions (Stage 2)"` e `"Antigravity Desktop (Stage 3)"`.
3. Criar uma seção para a "Matriz MoSCoW". Adicionar elementos visuais (barras de progresso estáticas ou contadores numéricos) para as categorias `MUST`, `SHOULD` e `COULD`.
4. Aplicar CSS Flexbox/Grid e Media Queries para garantir que os painéis se adaptem a telas de celulares e desktops **(SHOULD - S01)**.
**Critérios de Aceite:** `[M03]`, `[M04]`, `[S01]`, `[S02]` atendidos.

### 🔴 Sub-issue 3: Console de Execução Simulado (MUST & SHOULD HAVE)
**Objetivo:** Implementar a interface de log interativa e a lógica de simulação do laço de autoafinação.
**Tarefas:**
1. Criar uma área visual de "Console/Terminal" no HTML (fundo escuro, fonte monospace).
2. No arquivo `app.js`, escrever uma função que injete dinamicamente linhas de log no console após o carregamento da página.
3. A simulação deve imprimir sequencialmente (com pequenos atrasos via `setTimeout`) o fluxo de 3 retries. Exemplo de saída esperada:
   - `> Iniciando laço de autoafinação...`
   - `> Retry 1: Failed (Ajustando parâmetros)`
   - `> Retry 2: Partial (Otimizando SHOULD HAVEs)`
   - `> Retry 3: Success (100% MUST atingido)`
4. Adicionar animações CSS (`@keyframes` ou `transition`) para que as novas linhas de log apareçam com um efeito de *fade-in* ou digitação **(SHOULD - S03)**.
**Critérios de Aceite:** `[M05]`, `[S03]` atendidos.

### 🟢 Sub-issue 4: Aprimoramentos de UX (COULD HAVE)
**Objetivo:** Adicionar funcionalidades desejáveis de interface, caso o tempo e o laço de retries permitam.
**Tarefas:**
1. Implementar um botão/toggle no cabeçalho que alterne uma classe `.dark-mode` no elemento `<body>`, ajustando as variáveis CSS para um tema escuro **(COULD - C01)**.
2. Adicionar o atributo `title` nativo do HTML (ou tooltips via CSS puro) nos indicadores de estágio (Stage 1, 2 e 3) com uma breve descrição de cada um **(COULD - C02)**.
**Critérios de Aceite:** `[C01]`, `[C02]` atendidos (Não bloqueia o merge se falhar).

---

## 🧪 4. Estratégia de Validação Local (Validation Strategy)

Antes de submeter o PR, o Build Runner deve garantir que a validação local passe pelos seguintes testes de sanidade:

1. **Teste de Build Zero:** Abrir o arquivo `src/index.html` diretamente no navegador (via protocolo `file://`). A página deve renderizar perfeitamente sem nenhum servidor local rodando.
2. **Auditoria de Console:** Verificar o *Developer Tools* do navegador. Não deve haver erros de JavaScript (Red errors) nem falhas de carregamento de recursos (404).
3. **Teste de Responsividade:** Redimensionar a janela do navegador para 320px de largura. O layout não deve quebrar horizontalmente (sem scroll horizontal indesejado).
4. **Verificação de Invariantes:** Rodar mentalmente (ou via script local, se disponível) a checagem: *Foi adicionada alguma dependência externa?* Se sim, reverter imediatamente.