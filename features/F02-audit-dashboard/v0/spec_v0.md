# Especificação Normativa: F02 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro (gemini-3.1-pro-preview)`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T04:44:06Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


# `spec_v0.md` — Especificação Normativa Executável
**Feature ID:** `F02` | **Slug:** `audit-dashboard` | **Versão:** `v0` (POC)

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

O artefato `audit.html` estabelece o *contract boundary* para a interface de telemetria visual do ecossistema `Harness_teste`. Seu propósito arquitetural é atuar como um radiador de informações estático e autônomo, refletindo o status de certificação emitido pelo *Validation Agent* (Stage 4). 

O desenho comportamental exige uma aplicação *offline-first*, encapsulada, que renderize deterministicamente três vetores de dados mockados no *client-side*:
1. **Matriz de Invariantes:** Representação visual do estado de conformidade dos 4 Artigos Constitucionais.
2. **Telemetria MoSCoW:** Um medidor quantitativo (*Score Meter*) que plota a pontuação de requisitos MUST HAVE (peso 10) e SHOULD HAVE (peso 3).
3. **Rastreabilidade de Autoafinação:** Uma matriz tabular que expõe o laço de *retries* (Tentativas 1, 2 e 3 Campeã), evidenciando a convergência do algoritmo de *self-tuning*.

A interface deve garantir alta densidade semântica na apresentação dos dados, utilizando sinalização visual clara (ex: *badges* de `[PASS]`/`[FAIL]`) para atestar a integridade do *baseline*.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para garantir a prevenção de deriva cognitiva (*Anti-Drift Anchoring*) e evitar *scope creep*, os seguintes itens estão expressamente fora do escopo desta especificação:

*   **NON-GOAL 1 (Isolamento de Dados):** Nenhuma integração com backend dinâmico, APIs REST/GraphQL externas ou bancos de dados. O estado da aplicação deve ser derivado exclusivamente de um objeto de estado (mock) injetado via Vanilla JS.
*   **NON-GOAL 2 (Zero Dependências Externas):** É estritamente proibida a importação de *frameworks* pesados (React, Angular, Vue) ou bibliotecas de UI via CDN (Bootstrap, Tailwind, jQuery). A implementação deve ser restrita a HTML5 semântico, Vanilla CSS e Vanilla JS.
*   **NON-GOAL 3 (Mutabilidade de Estado):** O painel não deve possuir formulários ou ações que alterem o estado dos invariantes ou acionem novos *builds*. Trata-se de uma interface de auditoria *read-only*.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

O desenvolvimento desta *feature* tangencia e reforça os seguintes artigos da `CONSTITUTION.md`:

*   **ARTIGO 1 — Separação Estrita de Fases e Papéis:** O painel materializa visualmente a auditoria independente do *Validation Agent*, sem prover ferramentas de alteração de código, respeitando o isolamento de papéis.
*   **ARTIGO 3 — Determinismo e Matriz de Corte MoSCoW:** A interface é a representação gráfica da regra de 100% de MUST HAVE e do laço obrigatório de 3 *retries*, tornando o cálculo de *score* auditável por humanos.
*   **ARTIGO 4 — Prevenção de Deriva Cognitiva:** O próprio painel atua como âncora visual para o especialista humano, garantindo que as regras constitucionais estejam sempre visíveis e monitoradas.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte abaixo define os critérios determinísticos para a validação do *build*. A aprovação requer **100% de atendimento dos requisitos MUST HAVE**.

### 🔴 MUST HAVE (Requisitos Críticos — 10 pts cada)
*   **[MH01] Arquitetura Zero-CDN:** O arquivo `audit.html` (e seus eventuais arquivos `.css`/`.js` locais) deve carregar e renderizar perfeitamente em ambiente *offline*, sem requisições de rede para fontes, estilos ou scripts externos.
*   **[MH02] Quadro de Invariantes Constitucionais:** A interface deve renderizar uma seção contendo os 4 artigos da Constituição, cada um acompanhado de um *badge* visual indicando o status de conformidade (ex: `[PASS]`).
*   **[MH03] Medidor Visual MoSCoW:** A interface deve exibir um componente gráfico (barra de progresso ou gráfico circular em CSS/JS) que calcule e mostre a pontuação total baseada em um objeto de dados mockado (MUST HAVE = 10 pts, SHOULD HAVE = 3 pts).
*   **[MH04] Matriz de Histórico de Retries:** A interface deve apresentar uma tabela de rastreabilidade exibindo as 3 iterações do laço de autoafinação (Retry 1, Retry 2, Retry 3 Campeão), com colunas para "Tentativa", "Score Atingido" e "Status".

### 🟡 SHOULD HAVE (Requisitos de Refinamento — 3 pts cada)
*   **[SH01] Suporte a Dark Mode Nativo:** A interface deve implementar um esquema de cores escuro, ativado automaticamente via *media query* (`prefers-color-scheme: dark`) ou através de um *toggle* na UI.
*   **[SH02] Responsividade Fluida:** O *layout* deve utilizar CSS Flexbox ou Grid para se adaptar deterministicamente a *viewports* de dispositivos móveis (ex: empilhamento de colunas em telas menores que 768px).
*   **[SH03] Interatividade de Filtragem:** A tabela de histórico de *retries* deve permitir ordenação ou filtragem simples no *client-side* (ex: destacar apenas a tentativa campeã).
