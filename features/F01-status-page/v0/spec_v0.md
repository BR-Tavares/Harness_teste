# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro (gemini-3.1-pro-preview)`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T14:06:03Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


```markdown
# SPECIFICATION DOCUMENT
**Feature ID:** `F01`
**Slug:** `status-page`
**Versão:** `v0` (POC)
**Artefato:** `spec_v0.md`
**Compilador:** Agente 1 (Spec Compiler)

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

A presente especificação normativa define o *Behavioral Blueprint* e os *Contract Boundaries* para a implementação da **Página de Status de Desenvolvimento** do repositório `Harness_teste`. O objetivo arquitetural é estabelecer uma interface de usuário (UI) estática, de alta fidelidade visual e responsiva, que atue como um painel de telemetria simulada para o ecossistema `Replicable Harness v6`.

O contrato de interface exige a entrega de um artefato *client-side* puro (HTML5, CSS3, ES6+), estruturado nos seguintes domínios visuais e comportamentais:
1. **Header de Identidade:** Cabeçalho semântico contendo a nomenclatura do projeto e âncora de navegação para o "Harness Central".
2. **Pipeline Topology (Arquitetura Híbrida):** Representação gráfica do fluxo de CI/CD, com indicadores de estado (ex: *Idle*, *Running*, *Success*, *Failed*) para os estágios: GitHub Actions (Stage 1 e 2) e Antigravity Desktop (Stage 3).
3. **Telemetry Dashboard (Métricas MoSCoW):** Componente de visualização de dados exibindo a matriz de pontuação de features, categorizada estritamente em MUST, SHOULD e COULD.
4. **Interactive Log Console:** Um componente de terminal simulado via JavaScript que renderiza, de forma assíncrona e visual, o laço de autoafinação determinístico de 3 retries (*3-retry auto-tuning loop*).

## 🚫 2. Limites de Escopo (NON-GOALS)

Para mitigar qualquer risco de *scope creep* e garantir a aderência estrita ao isolamento de fases, ficam expressamente vetados nesta versão (`v0`):

- **NON-GOAL 1 (Backend/State Management):** Nenhuma integração com APIs reais, WebSockets, bancos de dados externos ou persistência de estado. Os dados devem ser *mockados* no próprio artefato *client-side*.
- **NON-GOAL 2 (Frameworks/Bibliotecas Pesadas):** É estritamente proibida a injeção de frameworks reativos (React, Vue, Angular) ou bibliotecas de estilização pesadas (Bootstrap, Tailwind via CDN pesado). O contrato exige o uso exclusivo de **Vanilla CSS moderno** (Flexbox, CSS Grid, Custom Properties) e **Vanilla JavaScript**.
- **NON-GOAL 3 (Autenticação/Autorização):** A página não possuirá nenhum mecanismo de controle de acesso ou login.
- **NON-GOAL 4 (Deploy Automatizado):** Esta especificação não cobre a configuração de *GitHub Pages* ou *Vercel*; o escopo limita-se à construção dos artefatos estáticos no repositório.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

A execução desta especificação deve respeitar os seguintes artigos do `CONSTITUTION.md`:

- **ARTIGO 1, Cláusula 2 e 3 (Strict Stage Isolation):** O Agente 2 (Plan Architect) deverá consumir este documento unicamente para gerar o `plan_v0.md`. O Build Runner não poderá alterar nenhum arquivo fora do diretório de *assets* estáticos designado para esta feature.
- **ARTIGO 2, Cláusula 1 (Baseline Invariance):** A criação desta página estabelece um novo contrato de baseline visual. Nenhuma alteração futura poderá quebrar a estrutura semântica do HTML aqui definida sem homologação explícita.
- **ARTIGO 4, Cláusula 2 (Anti-Drift Anchoring):** Os limites de escopo (NON-GOALS) definidos na Seção 2 atuam como âncoras cognitivas para impedir a deriva arquitetural durante a fase de implementação pelo Build Runner.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte abaixo será utilizada pelo `scripts/eval_moscow.py` para cômputo determinístico do score de validação. A tentativa de build só será elegível para merge se atingir **100% dos requisitos MUST HAVE**.

### 🔴 MUST HAVE (Requisitos Críticos - Bloqueantes para Merge)
- **MH-01:** O artefato deve ser composto exclusivamente por arquivos estáticos (`index.html`, `style.css`, `script.js` ou embutidos em um único arquivo HTML).
- **MH-02:** O cabeçalho deve exibir o título "Harness_teste" e conter um link funcional (mesmo que com `href="#"`) para o "Harness Central".
- **MH-03:** A interface deve apresentar três indicadores visuais distintos representando os estágios da arquitetura: "GitHub Actions Stage 1", "GitHub Actions Stage 2" e "Antigravity Desktop Stage 3".
- **MH-04:** A interface deve conter uma seção dedicada à exibição das métricas MoSCoW (MUST, SHOULD, COULD) com valores estáticos predefinidos.
- **MH-05:** O código não deve conter chamadas de rede para bibliotecas CSS/JS externas (exceção feita a web fonts, se estritamente necessário, embora fontes de sistema sejam preferíveis).

### 🟡 SHOULD HAVE (Requisitos de Refinamento - Alvo do Laço de 3 Retries)
- **SH-01:** O design deve ser totalmente responsivo, adaptando-se fluidamente a resoluções de dispositivos móveis e desktops utilizando *Media Queries* e *CSS Flexbox/Grid*.
- **SH-02:** O "Console de Log Interativo" deve simular dinamicamente via JavaScript a injeção de linhas de log, demonstrando visualmente o laço de autoafinação de 3 retries (ex: `[INFO] Retry 1/3...`, `[WARN] Adjusting parameters...`, `[SUCCESS] Baseline achieved.`), utilizando `setTimeout` ou `setInterval`.
- **SH-03:** A interface deve adotar uma estética moderna e limpa (ex: paleta de cores de terminal/dark mode ou design corporativo minimalista), utilizando variáveis CSS (`:root`) para facilitar a manutenção do tema.
- **SH-04:** O código HTML deve ser semanticamente correto (uso de `<header>`, `<main>`, `<section>`, `<article>`, `<footer>`) para garantir acessibilidade básica.
```
