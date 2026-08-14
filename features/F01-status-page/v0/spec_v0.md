# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro Engine`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T04:19:57Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


# SPECIFICATION: F01 — Página de Status de Desenvolvimento do Repositório Harness_teste

**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão:** `v0` (POC)  
**Status:** Compilado (Agent 1 - Spec Compiler)

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

O presente documento estabelece o *contract boundary* normativo para a implementação da Feature `F01`. O objetivo central é projetar e materializar uma interface web estática (HTML5, CSS3, JS) que atue como um painel de telemetria visual para o repositório `Harness_teste`, refletindo sua integração com o ecossistema do `Replicable Harness v6`.

O *behavioral blueprint* exige uma arquitetura de front-end limpa, semântica e responsiva. A interface deve atuar como um radiador de informações (*information radiator*), expondo de forma clara e imediata o estado da arquitetura híbrida de agentes, a matriz de pontuação determinística e o comportamento do laço de autoafinação local. A integridade da linha de base (*baseline integrity*) visual deve ser garantida através do uso estrito de tecnologias web nativas, assegurando alta performance e ausência de dependências transitórias complexas.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para prevenir a expansão não autorizada de escopo (*scope creep*) e garantir a aderência estrita ao isolamento de fases, os seguintes itens estão expressamente fora do *contract boundary* desta iteração (v0):

*   **NON-GOAL 1 (Isolamento de Backend):** Não haverá implementação de backend dinâmico, APIs REST/GraphQL ou integração com banco de dados externo. A aplicação será estritamente *client-side* (arquivos estáticos).
*   **NON-GOAL 2 (Restrição de Dependências):** É terminantemente proibido o uso de bibliotecas ou frameworks CSS/JS pesados (ex: React, Angular, Vue, Bootstrap, Tailwind via NPM). O estilo deve ser construído utilizando Vanilla CSS moderno (CSS Variables, Grid, Flexbox).
*   **NON-GOAL 3 (Mutação de Estado Real):** O console de log interativo não consumirá logs reais do sistema nesta versão; ele deve operar através de uma simulação visual determinística via JavaScript *client-side*.
*   **NON-GOAL 4 (Alteração de Governança):** Nenhuma modificação será feita nos diretórios `governance/`, `.github/workflows/` ou em contratos de baseline existentes.

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

O design e a futura implementação desta especificação tocam os seguintes invariantes do `CONSTITUTION.md`:

*   **ARTIGO 1, §1 e §2 (Strict Stage Isolation):** Esta especificação define exclusivamente o comportamento normativo. A delegação de tarefas e a geração de código são estritamente reservadas aos Agentes 2 e Build Runner, respectivamente.
*   **ARTIGO 2, §1 (Baseline Invariance):** A adição desta página de status não deve quebrar ou alterar nenhum contrato previamente consolidado no `Features_state.md`. A entrega consiste em novos artefatos isolados na camada de apresentação.
*   **ARTIGO 3, §2 e §3 (Determinismo e Matriz de Corte):** A interface gráfica deve prever a representação visual exata da matriz MoSCoW e do laço de autoafinação de 3 retries, refletindo os princípios determinísticos do *Replicable Harness*.

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte a seguir define os critérios determinísticos para a validação da feature. A elegibilidade para *merge* exige 100% de atendimento dos requisitos MUST HAVE.

### 🔴 MUST HAVE (Obrigatório para Merge - 100% exigido)
*   **MH-01:** O artefato principal deve ser um arquivo `index.html` válido e semântico (HTML5).
*   **MH-02:** A página deve conter um cabeçalho (*Header*) exibindo claramente o nome do projeto (`Harness_teste`) e um hiperlink funcional apontando para o "Harness Central".
*   **MH-03:** A interface deve apresentar indicadores visuais distintos e claros para os três estágios da Arquitetura Híbrida:
    *   *Stage 1 & 2:* GitHub Actions.
    *   *Stage 3:* Antigravity Desktop.
*   **MH-04:** A página deve exibir uma seção dedicada às "Métricas MoSCoW", contendo a representação visual das categorias MUST, SHOULD e COULD.
*   **MH-05:** Todo o estilo visual deve ser implementado exclusivamente com Vanilla CSS (sem frameworks externos), garantindo um design moderno e limpo.

### 🟡 SHOULD HAVE (Alvo do Laço de Autoafinação de 3 Retries)
*   **SH-01:** A página deve ser totalmente responsiva, adaptando-se fluidamente a resoluções de dispositivos móveis e desktops (utilizando *media queries*).
*   **SH-02:** A interface deve incluir um "Console de Log Interativo" construído com Vanilla JavaScript.
*   **SH-03:** O Console de Log deve simular visualmente o laço de autoafinação (*3-retry loop*), injetando mensagens de log simuladas no DOM com pequenos atrasos temporais (ex: `setTimeout` ou `setInterval`) para demonstrar o comportamento dinâmico do agente.
*   **SH-04:** O design deve utilizar variáveis CSS (`:root`) para facilitar a manutenção de temas (cores primárias, secundárias, fontes e espaçamentos).
