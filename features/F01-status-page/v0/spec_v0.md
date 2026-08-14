# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro (gemini-3.1-pro-preview)`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T13:06:42Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


# Especificação Normativa Executável (spec_v0.md)
**Feature ID:** `F01` — Página de Status de Desenvolvimento do Repositório Harness_teste
**Compilador:** Agente 1 (Spec Compiler)
**Framework:** REPLICABLE_HARNESS v6

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

A presente especificação define o contrato de interface e o comportamento estrutural para a **Página de Status de Desenvolvimento** do repositório `Harness_teste`. O artefato atuará como uma superfície de telemetria visual estática (client-side), projetada para refletir o ciclo de vida e a integração com o `Replicable Harness v6`.

O *Behavioral Blueprint* exige a construção de um *dashboard* semântico, operando estritamente no navegador, composto pelos seguintes domínios visuais:
1. **Contract Boundary de Identidade:** Cabeçalho semântico contendo a nomenclatura do projeto (`Harness_teste`) e âncora de navegação para o *Harness Central*.
2. **Superfície de Telemetria da Arquitetura Híbrida:** Painel de indicadores de estado (*state indicators*) segregando visualmente os estágios de execução: GitHub Actions (Stage 1 e 2) e Antigravity Desktop (Stage 3).
3. **Matriz de Resolução MoSCoW:** Componente de visualização de dados que expõe a pontuação determinística de features categorizadas em MUST, SHOULD e COULD.
4. **Console de Execução Simulado:** Interface de log interativa que emula o comportamento do laço de autoafinação local (*3-retry auto-tuning loop*), demonstrando a progressão de refinamento de código.

A arquitetura técnica baseia-se em **Vanilla Web Technologies** (HTML5 semântico, CSS3 moderno com CSS Variables/Grid/Flexbox e ES6+ JavaScript), garantindo alta performance e zero dependência de cadeias de build complexas no client-side.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para mitigar qualquer risco de *scope creep* e garantir a prevenção de deriva cognitiva (*Anti-Drift Anchoring*), os seguintes itens estão expressamente fora do escopo desta iteração (v0):

- **NON-GOAL 1 (Zero Backend/State Persistence):** Não haverá integração com APIs REST/GraphQL, WebSockets reais, ou bancos de dados. O estado será efêmero e gerenciado via simulação estática no client-side (Mock Data).
- **NON-GOAL 2 (Zero External Dependencies):** É estritamente proibido o uso de frameworks ou bibliotecas pesadas de UI/UX (ex: React, Vue, Angular, Tailwind CSS, Bootstrap, jQuery). A estilização e o comportamento devem ser resolvidos nativamente.
- **NON-GOAL 3 (Zero CI/CD Triggering):** A interface não possuirá capacidade de invocar ou alterar o estado real dos pipelines do GitHub Actions ou do Antigravity Desktop. Trata-se de uma visualização *read-only* simulada.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

Esta especificação foi compilada sob estrita observância do `CONSTITUTION.md`:

- **ARTIGO 1 (Strict Stage Isolation):** O Agente 1 limitou-se a definir o *o quê* (requisitos e limites). Nenhum plano de implementação, estrutura de diretórios ou código-fonte foi gerado neste documento.
- **ARTIGO 2 (Baseline Invariance):** A implementação desta feature não requer mutação de contratos preexistentes em `governance/Features_state.md`. Trata-se de uma adição isolada na camada de apresentação.
- **ARTIGO 3 (Determinism & MoSCoW):** Os critérios de aceitação abaixo fornecem a matriz exata que o `scripts/eval_moscow.py` utilizará para computar o score determinístico do PR.
- **ARTIGO 4 (Anti-Drift Anchoring):** A seção de NON-GOALS blinda o Agente 2 (Plan Architect) e o Build Runner contra a introdução de complexidade acidental (ex: adição de bundlers como Webpack/Vite).

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz a seguir define os limites de aceitação para a validação determinística. A tentativa de build só será elegível para merge se atingir **100% dos requisitos MUST HAVE**.

### 🔴 MUST HAVE (Obrigatório para Merge - 100% de conformidade exigida)
- **[M01]** O artefato final deve ser um arquivo `index.html` (acompanhado ou não de arquivos `.css` e `.js` puros), sem requerer processos de transpilação ou *build steps* (ex: npm install).
- **[M02]** A interface deve renderizar um cabeçalho contendo o título "Status - Harness_teste" e um hiperlink funcional (mesmo que para um placeholder `#`) apontando para "Harness Central".
- **[M03]** A interface deve exibir indicadores visuais distintos (ex: cards, badges ou ícones) representando os três estágios da Arquitetura Híbrida: "GitHub Actions (Stage 1)", "GitHub Actions (Stage 2)" e "Antigravity Desktop (Stage 3)".
- **[M04]** A interface deve conter uma seção dedicada à "Matriz MoSCoW", exibindo contadores ou barras de progresso simuladas para as categorias MUST, SHOULD e COULD.
- **[M05]** A interface deve implementar um "Console de Log" via JavaScript Vanilla que simule visualmente a injeção de linhas de texto representando o laço de autoafinação de 3 retries (ex: *Retry 1: Failed -> Retry 2: Partial -> Retry 3: Success*).

### 🟡 SHOULD HAVE (Alvo de otimização no laço de 3 retries locais)
- **[S01]** O layout deve ser responsivo, adaptando-se adequadamente a viewports de dispositivos móveis e desktops utilizando CSS Media Queries.
- **[S02]** A estilização deve utilizar CSS Custom Properties (Variáveis CSS) para definir a paleta de cores, tipografia e espaçamentos, garantindo um design system coeso e limpo.
- **[S03]** O "Console de Log" deve apresentar animações suaves (CSS Transitions/Keyframes) ao inserir novas linhas, simulando o efeito de digitação ou *fade-in* de um terminal real.

### 🟢 COULD HAVE (Desejável, mas não impacta o score de aprovação)
- **[C01]** Implementação de um *toggle* (interruptor) para alternar entre Tema Claro (Light Mode) e Tema Escuro (Dark Mode).
- **[C02]** Adição de *tooltips* nativos (atributo `title` ou CSS puro) nos indicadores da Arquitetura Híbrida para explicar brevemente o que cada estágio faz.

### ⚪ WON'T HAVE (Explicitamente excluído desta iteração)
- **[W01]** Conexão real com a API do GitHub para buscar o status verdadeiro das Actions.
- **[W02]** Persistência do histórico de logs do console simulado após o *refresh* da página.
