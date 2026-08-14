Aqui está o plano de tarefas arquiteturais (`plan_v0.md`) gerado com base na especificação normativa fornecida e em estrita conformidade com a `CONSTITUTION.md`.

---

# `plan_v0.md` — Plano de Tarefas Arquiteturais
**Feature ID:** `F02` | **Slug:** `audit-dashboard` | **Versão:** `v0` (POC)
**Agente Responsável:** Agente 2 (Plan Architect)

## 🏛️ 1. Âncora Constitucional e Limites Arquiteturais

Para garantir a **Prevenção de Deriva Cognitiva (Artigo 4)** e o **Isolamento Estrito de Fases (Artigo 1)**, este plano orienta o *Build Runner* sob as seguintes restrições absolutas:

*   **INVARIANTS TOUCHED:**
    *   **Artigo 1:** O painel será estritamente *read-only*, refletindo a auditoria sem permitir mutação de código ou acionamento de pipelines.
    *   **Artigo 3:** A lógica de cálculo do *Score Meter* deve refletir deterministicamente a regra de pesos (MH = 10, SH = 3) e o laço de 3 *retries*.
    *   **Artigo 4:** Nenhuma dependência externa será adicionada.
*   **NON-GOALS (Restrições de Escopo):**
    *   Nenhuma chamada de rede (Fetch/XHR) para APIs externas.
    *   Nenhum uso de CDNs (Google Fonts, FontAwesome, Tailwind, React, etc.).
    *   Nenhum formulário de submissão ou alteração de estado persistente.

---

## 📐 2. Estratégia Arquitetural

A aplicação seguirá o padrão **Vanilla Web Component-like Architecture**, dividida em três camadas lógicas que podem residir no mesmo arquivo (`audit.html`) ou em arquivos locais adjacentes (`audit.css`, `audit.js`), garantindo o requisito *Offline-First*.

1.  **Camada de Dados (Mock State):** Um objeto JavaScript constante (`const auditState = {...}`) injetado no *client-side*, contendo os vetores de Invariantes, MoSCoW e Retries.
2.  **Camada de Apresentação (DOM/CSS):** Estrutura semântica HTML5 estilizada com CSS Grid/Flexbox nativo, utilizando variáveis CSS (`:root`) para gerenciar o *Dark Mode*.
3.  **Camada de Comportamento (Vanilla JS):** Funções puras de renderização que leem o `auditState` e injetam o HTML correspondente no DOM (`innerHTML` ou `createElement`), além de calcular o *score* matemático.

---

## 📋 3. Decomposição em Sub-issues MoSCoW (Actionable Tasks)

O *Build Runner* deve executar as seguintes tarefas sequencialmente. A aprovação do PR exige 100% de sucesso nas tarefas marcadas como **[MUST HAVE]**.

### 🔴 TAREFAS CRÍTICAS (MUST HAVE) - *Bloqueantes para Merge*

#### Task 1: Setup da Arquitetura Zero-CDN e Estado Mockado
*   **Refere-se a:** `[MH01]`
*   **Descrição:** Criar a estrutura base do arquivo `audit.html`. Definir o objeto de estado JavaScript que alimentará a interface.
*   **Critérios de Êxito:**
    *   O arquivo HTML deve possuir a tag `<meta charset="UTF-8">` e `<meta name="viewport" content="...">`.
    *   Nenhuma tag `<link>` ou `<script>` apontando para URLs externas (`http://` ou `https://`).
    *   Criação de um objeto JS `mockData` contendo arrays para `invariants`, `moscowRequirements` e `retries`.

#### Task 2: Renderização do Quadro de Invariantes Constitucionais
*   **Refere-se a:** `[MH02]`
*   **Descrição:** Implementar a seção visual que lista os 4 Artigos da Constituição.
*   **Critérios de Êxito:**
    *   O DOM deve ser populado dinamicamente via JS a partir do `mockData.invariants`.
    *   Cada artigo deve exibir um *badge* visual. Se o status for `true`, exibir `[PASS]` (com cor de sucesso, ex: verde); se `false`, exibir `[FAIL]` (com cor de erro, ex: vermelho).

#### Task 3: Implementação do Medidor Visual MoSCoW (Score Meter)
*   **Refere-se a:** `[MH03]`
*   **Descrição:** Criar o componente gráfico e a lógica matemática de pontuação.
*   **Critérios de Êxito:**
    *   Função JS que itera sobre `mockData.moscowRequirements`.
    *   Cálculo determinístico: Requisitos `MUST HAVE` atendidos somam 10 pontos; `SHOULD HAVE` atendidos somam 3 pontos.
    *   Renderização de uma barra de progresso (usando a tag `<progress>` do HTML5 ou uma `div` com `width` dinâmico via CSS) refletindo a pontuação obtida vs. pontuação máxima possível.

#### Task 4: Construção da Matriz de Histórico de Retries
*   **Refere-se a:** `[MH04]`
*   **Descrição:** Desenvolver a tabela de rastreabilidade do laço de autoafinação.
*   **Critérios de Êxito:**
    *   Renderizar uma tag `<table>` semântica.
    *   Colunas obrigatórias: "Tentativa" (1, 2, 3), "Score Atingido" e "Status" (ex: *Failed*, *Refining*, *Champion*).
    *   Os dados devem vir do array `mockData.retries`.

---

### 🟡 TAREFAS DE REFINAMENTO (SHOULD HAVE) - *Alvo do Self-Tuning*

#### Task 5: Estilização Responsiva e Dark Mode Nativo
*   **Refere-se a:** `[SH01]`, `[SH02]`
*   **Descrição:** Aplicar CSS moderno para garantir acessibilidade visual e adaptação a dispositivos móveis.
*   **Critérios de Êxito:**
    *   Uso de CSS Flexbox ou Grid para organizar o *Dashboard* (ex: Invariantes ao lado do Score em telas grandes, empilhados em telas pequenas).
    *   Implementação de `@media (prefers-color-scheme: dark)` alterando variáveis CSS (`--bg-color`, `--text-color`) para um tema escuro.

#### Task 6: Interatividade de Filtragem na Matriz de Retries
*   **Refere-se a:** `[SH03]`
*   **Descrição:** Adicionar capacidade de manipulação visual da tabela de histórico no *client-side*.
*   **Critérios de Êxito:**
    *   Adicionar um botão ou *checkbox* (ex: "Destacar Campeã").
    *   Ao interagir, o Vanilla JS deve filtrar as linhas da tabela ou aplicar uma classe CSS de destaque (ex: borda dourada/verde) exclusivamente na linha correspondente à Tentativa 3 (Campeã), ocultando ou esmaecendo as demais.

---

## 🔄 4. Contrato de Execução para o Build Runner
1.  **Isolamento:** O *Build Runner* deve criar/editar apenas os arquivos necessários para esta *feature* (ex: `audit.html`, `audit.js`, `audit.css`).
2.  **Proibição de Modificação de Baseline:** É terminantemente proibido alterar qualquer arquivo dentro do diretório `governance/` ou `.github/workflows/`.
3.  **Validação:** Após a implementação, o *Build Runner* deve garantir que o arquivo abre perfeitamente em um navegador local sem acesso à internet, validando o `[MH01]`.