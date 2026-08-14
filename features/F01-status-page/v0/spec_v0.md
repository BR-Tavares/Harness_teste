# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro Engine`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T04:21:25Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


# SPECIFICATION: F01 — Página de Status de Desenvolvimento (v0)

**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão:** `v0` (POC)  
**Status:** COMPILADO (Agent 1 - Spec Compiler)  

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

Esta especificação normativa define o *contract boundary* para a Feature F01, estabelecendo a fundação visual e interativa para o monitoramento do repositório `Harness_teste` sob a governança do `Replicable Harness v6`. 

O *behavioral blueprint* dita que a aplicação deve operar como um artefato estático (Client-Side Rendering puro), garantindo alta performance e zero dependência de infraestrutura de backend nesta iteração (v0). A interface deve atuar como um *dashboard* de telemetria simulada, traduzindo o estado da arquitetura híbrida e a integridade da linha de base (*baseline integrity*) em componentes visuais de fácil assimilação.

**Componentes Comportamentais Principais:**
1. **Header de Identidade:** Ponto de ancoragem de navegação, exibindo o contexto do projeto e roteamento estático para o Harness Central.
2. **Painel de Arquitetura Híbrida:** Representação de estado (State Representation) dos três estágios do pipeline (GitHub Actions Stage 1 & 2, Antigravity Desktop Stage 3).
3. **Matriz de Corte MoSCoW:** Visualização de dados estáticos refletindo a pontuação de features, garantindo transparência sobre o determinismo de aceitação.
4. **Console de Log Interativo:** Um componente de simulação baseada em eventos (Event-Driven Simulation) via JavaScript vanilla, que emula visualmente o laço de autoafinação local de 3 retries (*3-retry auto-tuning loop*).

## 🚫 2. Limites de Escopo (NON-GOALS)

Para prevenir expansão não autorizada de escopo (*scope creep*) e garantir a aderência estrita à arquitetura proposta, os seguintes itens estão **expressamente fora do escopo**:

- **NON-GOAL 1 (Zero Backend):** Não haverá implementação de backend dinâmico, chamadas de API reais, WebSockets ou integração com banco de dados externo. Todo o estado será gerenciado localmente via HTML5/CSS/JS.
- **NON-GOAL 2 (Zero Heavy Frameworks):** É estritamente proibido o uso de bibliotecas ou frameworks pesados de UI (ex: React, Vue, Angular, Tailwind, Bootstrap). O estilo deve ser construído exclusivamente com Vanilla CSS moderno (CSS Variables, Flexbox, Grid).
- **NON-GOAL 3 (Zero Real Telemetry):** O console de logs não consumirá logs reais do sistema operacional ou do CI/CD nesta versão; ele deve operar estritamente como uma simulação visual determinística.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

O desenvolvimento desta feature deve respeitar os seguintes princípios constitucionais do REPLICABLE_HARNESS v6:

- **ARTIGO 1, §3 (Isolamento de Escopo):** O código gerado para esta feature deve residir exclusivamente nos diretórios de aplicação web (ex: `src/` ou `public/`). Nenhuma alteração em `governance/` ou `.github/workflows/` é permitida para a satisfação desta especificação.
- **ARTIGO 2, §1 (Baseline Invariance):** A introdução desta página estática não deve quebrar nenhum contrato de roteamento ou build previamente estabelecido no `Features_state.md`.
- **ARTIGO 3, §1 e §2 (Determinismo MoSCoW):** A interface deve refletir visualmente a filosofia de 100% de MUST HAVEs e o laço de 3 retries, educando o usuário sobre as regras de governança do sistema.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte a seguir será utilizada pelo `scripts/eval_moscow.py` e pelo Validation Agent para cômputo determinístico de aprovação do PR.

### 🔴 MUST HAVE (Obrigatório para Merge - 100% exigido)
- **[M01]** O artefato final deve ser composto exclusivamente por arquivos estáticos (`index.html`, `style.css`, `script.js`).
- **[M02]** A interface deve conter um cabeçalho identificando o projeto `Harness_teste` com um link âncora funcional apontando para o "Harness Central".
- **[M03]** A interface deve apresentar indicadores visuais distintos para os 3 estágios da arquitetura (Stage 1: Spec, Stage 2: Plan, Stage 3: Build).
- **[M04]** A interface deve exibir um painel ou seção dedicada à Matriz MoSCoW, listando categorias MUST, SHOULD e COULD.
- **[M05]** O estilo visual deve ser implementado 100% em Vanilla CSS, sem importação de frameworks externos.

### 🟡 SHOULD HAVE (Alvo do laço de autoafinação de 3 retries)
- **[S01]** O layout deve ser totalmente responsivo, adaptando-se fluidamente a resoluções de desktop e dispositivos móveis (utilizando CSS Grid/Flexbox e Media Queries).
- **[S02]** O "Console de Log Interativo" deve ser implementado via Vanilla JavaScript, injetando linhas de log simuladas sequencialmente no DOM para demonstrar o laço de "3 retries" (ex: *Retry 1/3: Refining SHOULD HAVE...*).
- **[S03]** A interface deve empregar uma paleta de cores moderna e limpa, utilizando CSS Variables (Custom Properties) no `:root` para facilitar futuras implementações de *Dark Mode*.
- **[S04]** Os indicadores visuais de arquitetura (Stage 1, 2 e 3) devem possuir micro-interações (ex: *hover states* ou transições suaves de CSS) para indicar status de "processando" ou "concluído".
