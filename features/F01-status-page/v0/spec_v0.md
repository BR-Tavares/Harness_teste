# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro Engine`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T04:22:23Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão:** `v0` (POC)  
**Contract Boundary:** Aplicação Client-Side (HTML5/CSS3/JS Vanilla)  
**Baseline Integrity:** Nova feature isolada, sem impacto em contratos preexistentes.

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

A feature `F01` estabelece o *behavioral blueprint* para a interface de observabilidade do repositório `Harness_teste`. O objetivo normativo é materializar um *dashboard* estático, responsivo e de alta fidelidade visual que reflita o estado de integração com o ecossistema `Replicable Harness v6`. 

O desenho comportamental exige a orquestração de quatro componentes visuais fundamentais dentro de uma única página (Single Page Application estática):
1. **Identidade e Navegação:** Um cabeçalho semântico que ancore o usuário no contexto do projeto, estabelecendo a ligação com o *Harness Central*.
2. **Telemetria de Arquitetura Híbrida:** Uma representação visual de estados (ex: *Pending*, *Running*, *Success*, *Failed*) mapeando o pipeline de execução: GitHub Actions (Stage 1 e 2) e Antigravity Desktop (Stage 3).
3. **Matriz de Corte MoSCoW:** Um painel de métricas que exponha deterministicamente a pontuação de features categorizadas em MUST HAVE, SHOULD HAVE e COULD HAVE.
4. **Console de Autoafinação (Self-Tuning Loop):** Um componente interativo que simule visualmente o laço de 3 *retries* locais, demonstrando a mecânica de refinamento do agente construtor.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para garantir a prevenção de deriva cognitiva (*anti-drift anchoring*) e evitar expansão não autorizada de escopo (*scope creep*), os seguintes itens estão expressamente fora do *contract boundary* desta versão:

*   **NON-GOAL 1 (Backend/State Management):** Não será implementado nenhum backend dinâmico, banco de dados externo, chamadas de API reais ou persistência de estado. A aplicação operará estritamente via código estático *client-side* (mock de dados em memória).
*   **NON-GOAL 2 (Frameworks/Bibliotecas Externas):** Não será permitida a injeção de bibliotecas pesadas de UI (como React, Vue, Angular) ou frameworks CSS (como Tailwind, Bootstrap). O contrato exige o uso estrito de Vanilla CSS moderno (CSS Variables, Flexbox/Grid) e Vanilla JavaScript.
*   **NON-GOAL 3 (Governança):** Nenhuma alteração será feita nos arquivos de governança (`governance/*`) ou fluxos de CI/CD (`.github/workflows/*`). O escopo é estritamente limitado aos artefatos de apresentação (UI).

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

O desenvolvimento desta especificação e sua futura implementação estão ancorados nas seguintes diretivas do `CONSTITUTION.md`:

*   **Artigo 1, Cláusula 1 (Strict Stage Isolation):** Esta especificação não contém código ou plano de execução. Atua unicamente como o contrato normativo para o *Plan Architect* (Agente 2).
*   **Artigo 2, Cláusula 1 (Baseline Invariance):** A introdução da `F01` não altera o `Features_state.md` preexistente. Trata-se de uma adição isolada que não quebra contratos de baseline.
*   **Artigo 3, Cláusula 1 e 3 (Determinism and MoSCoW):** A interface deve refletir visualmente a natureza determinística do cálculo de score MoSCoW, preparando o terreno para futuras integrações com o `scripts/eval_moscow.py`.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte a seguir define os critérios determinísticos para a validação da feature. A tentativa de *build* só será elegível para *merge* se atingir **100% dos requisitos MUST HAVE**.

### 🔴 MUST HAVE (Requisitos Críticos e Inegociáveis)
*   **MH-01:** A página deve ser construída exclusivamente com HTML5 semântico, CSS3 Vanilla e JavaScript Vanilla.
*   **MH-02:** A interface deve conter um cabeçalho (Header) exibindo o título "Harness_teste" e um hiperlink funcional (mesmo que simulado/âncora) apontando para o "Harness Central".
*   **MH-03:** A interface deve apresentar uma seção de "Status da Arquitetura Híbrida" contendo três indicadores visuais distintos:
    *   GitHub Actions - Stage 1 (Spec & Plan)
    *   GitHub Actions - Stage 2 (Validation)
    *   Antigravity Desktop - Stage 3 (Build & Auto-tuning)
*   **MH-04:** A interface deve conter um painel "Métricas MoSCoW" exibindo contadores ou barras de progresso estáticas para as categorias MUST, SHOULD e COULD.

### 🟡 SHOULD HAVE (Requisitos de Refinamento e Maximização de Valor)
*   **SH-01:** O design deve ser totalmente responsivo, adaptando-se de forma fluida a resoluções de dispositivos móveis e *desktops* (utilizando CSS Media Queries e Flexbox/Grid).
*   **SH-02:** A interface deve incluir um "Console de Log Interativo" na parte inferior ou lateral da tela.
*   **SH-03:** O "Console de Log Interativo" deve utilizar JavaScript Vanilla para simular a impressão de logs em tempo real, demonstrando visualmente o laço de autoafinação de 3 *retries* (ex: imprimindo mensagens de "Attempt 1/3... Failed", "Attempt 2/3... Refining", "Attempt 3/3... Success" com atrasos temporais via `setTimeout`).
*   **SH-04:** A paleta de cores e a tipografia devem refletir um design moderno e limpo (ex: *Dark Mode* por padrão, tipografia *sans-serif* monoespaçada para os logs, uso de variáveis CSS para consistência temática).
