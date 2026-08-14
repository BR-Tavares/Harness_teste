Aqui está o plano de tarefas arquiteturais (`plan_v0.md`) gerado com base na especificação normativa fornecida, respeitando estritamente os Invariantes Constitucionais do REPLICABLE_HARNESS v6.

```markdown
# ARCHITECTURAL PLAN DOCUMENT
**Feature ID:** `F01`
**Slug:** `status-page`
**Versão:** `v0` (POC)
**Artefato:** `plan_v0.md`
**Arquiteto:** Agente 2 (Plan Architect)

## 🎯 1. Estratégia Arquitetural (Architectural Strategy)

A arquitetura para a **Página de Status de Desenvolvimento** baseia-se no paradigma *Vanilla Web* (HTML5, CSS3, ES6+ puro), garantindo zero dependências externas e máxima performance. A estrutura será dividida em três camadas lógicas implementadas em arquivos estáticos dedicados (ou embutidos, se preferível pelo Build Runner, mas logicamente separados):

1.  **Camada Estrutural (HTML5):** Focada em semântica e acessibilidade, utilizando tags nativas (`<header>`, `<main>`, `<section>`, etc.) para definir os domínios visuais (Header, Pipeline, Telemetry, Console).
2.  **Camada de Apresentação (CSS3):** Utilização de *CSS Custom Properties* (`:root`) para definição de um *Design System* minimalista (preferencialmente *Dark Mode*). O layout será orquestrado exclusivamente via *CSS Flexbox* e *CSS Grid*, com *Media Queries* para garantir responsividade fluida.
3.  **Camada Comportamental (JS ES6+):** Um script isolado e assíncrono responsável unicamente por manipular o DOM do "Console de Log Interativo", simulando o laço de 3 retries através de temporizadores (`setTimeout`/`setInterval`).

---

## 📋 2. Decomposição em Sub-issues MoSCoW (Task Breakdown)

As tarefas abaixo foram desenhadas para isolar a entrega dos requisitos críticos (MUST HAVE) dos requisitos de refinamento (SHOULD HAVE), permitindo que o Build Runner garanta a elegibilidade de merge antes de otimizar a interface.

### 🔴 Fase 1: Fundação e Estrutura Crítica (Foco em MUST HAVE)
**Sub-issue 1.1: Setup Estático e Identidade**
*   **Ação:** Criar os arquivos base (`index.html`, `style.css`, `script.js`).
*   **Ação:** Implementar o `<header>` semântico com o título "Harness_teste" e um link âncora (`href="#"`) para "Harness Central".
*   **Validação:** Garantir ausência de chamadas de rede para bibliotecas externas (CDNs de CSS/JS).
*   **Mapeamento:** `MH-01`, `MH-02`, `MH-05`, `SH-04` (parcial).

**Sub-issue 1.2: Topologia de Pipeline e Dashboard de Telemetria**
*   **Ação:** Criar a seção "Pipeline Topology" com três indicadores visuais estáticos: "GitHub Actions Stage 1", "GitHub Actions Stage 2" e "Antigravity Desktop Stage 3".
*   **Ação:** Criar a seção "Telemetry Dashboard" exibindo as métricas MoSCoW (MUST, SHOULD, COULD) com valores estáticos *mockados*.
*   **Mapeamento:** `MH-03`, `MH-04`.

### 🟡 Fase 2: Refinamento Visual e Interatividade (Foco em SHOULD HAVE)
*Nota: Esta fase é o alvo principal do laço de autoafinação local de 3 retries do Build Runner.*

**Sub-issue 2.1: Estilização Moderna e Responsividade**
*   **Ação:** Definir variáveis CSS (`:root`) para uma paleta de cores moderna (estética de terminal/dark mode).
*   **Ação:** Aplicar *CSS Flexbox/Grid* para estruturar o layout das seções criadas na Fase 1.
*   **Ação:** Implementar *Media Queries* para garantir que o layout se adapte fluidamente entre resoluções mobile e desktop.
*   **Mapeamento:** `SH-01`, `SH-03`.

**Sub-issue 2.2: Simulação do Console de Log (Comportamento Assíncrono)**
*   **Ação:** Implementar lógica em Vanilla JavaScript no `script.js` para o "Interactive Log Console".
*   **Ação:** Criar uma função que utilize `setTimeout` ou `setInterval` para injetar dinamicamente linhas de log no DOM (ex: `[INFO] Retry 1/3...`, `[WARN] Adjusting parameters...`, `[SUCCESS] Baseline achieved.`), simulando o laço de autoafinação.
*   **Mapeamento:** `SH-02`.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

*   **ARTIGO 1, Cláusula 2 (Strict Stage Isolation):** Este documento (`plan_v0.md`) não contém código de implementação, apenas a orquestração arquitetural. O Build Runner deverá consumir estas sub-issues para gerar o código.
*   **ARTIGO 3, Cláusula 1 e 2 (Determinismo e Matriz de Corte):** A Fase 1 do plano garante a entrega de 100% dos requisitos MUST HAVE (bloqueantes para merge). A Fase 2 orienta o laço de 3 retries para maximizar os requisitos SHOULD HAVE.
*   **ARTIGO 4, Cláusula 2 (Anti-Drift Anchoring):** A seção de NON-GOALS abaixo blinda o escopo contra expansões não autorizadas durante a execução.

---

## 🚫 4. Limites de Escopo (NON-GOALS)

Para garantir o alinhamento estrito com a especificação `spec_v0.md`, o Build Runner está **expressamente proibido** de:

1.  **Backend/State Management:** Criar integrações com APIs, WebSockets ou persistência de dados real. Tudo deve ser *mockado* no client-side.
2.  **Frameworks/Bibliotecas:** Instalar ou linkar React, Vue, Angular, Bootstrap, Tailwind ou jQuery. O uso de Vanilla CSS e JS é mandatório.
3.  **Autenticação:** Implementar telas de login, tokens ou controle de acesso.
4.  **Deploy:** Alterar arquivos de workflow do GitHub Actions para configurar deploys (ex: GitHub Pages). O escopo é restrito à criação dos artefatos no repositório.
```