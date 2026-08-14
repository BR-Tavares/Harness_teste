# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Anthropic Claude Haiku (claude-haiku-4-5-20251001)`
- **Versão Técnica do Modelo:** `claude-haiku-4-5-20251001`
- **Data e Horário da Compilação:** `2026-08-14T13:09:38Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


# spec_v0.md — Página de Status de Desenvolvimento (F01)

**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão Spec:** `v0`  
**Status:** EXECUTÁVEL  
**Data de Emissão:** 2025-01-16

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

### Propósito Normativo
Estabelecer a especificação executável para uma página HTML5 responsiva que funcione como **painel de status visual em tempo real** do repositório `Harness_teste`, integrando indicadores da arquitetura híbrida (GitHub Actions + Antigravity Desktop) e métricas MoSCoW de features.

### Contrato de Comportamento (Contract Boundary)
A página deve:
1. **Renderizar sem dependências externas** (Vanilla CSS3 + ES6 JavaScript puro).
2. **Exibir estado simulado** de 3 pipelines paralelos (GH Actions Stage 1, GH Actions Stage 2, Antigravity Desktop Stage 3).
3. **Apresentar matriz MoSCoW interativa** com contadores de features por categoria (MUST, SHOULD, COULD).
4. **Simular console de log** do laço de autoafinação com 3 retries, mostrando transições de estado.
5. **Ser totalmente responsivo** (mobile-first, breakpoints em 768px e 1024px).
6. **Ser acessível** (WCAG 2.1 AA mínimo: contraste ≥4.5:1, navegação por teclado, ARIA labels).

## 🚫 2. Limites de Escopo (NON-GOALS)

| NON-GOAL | Justificativa |
|----------|---------------|
| **Backend dinâmico ou API REST** | v0 é POC estático; dados hardcoded em JSON embutido no HTML. |
| **Bibliotecas externas (React, Vue, Bootstrap)** | Vanilla CSS3 Grid/Flexbox + ES6 puro garante zero dependências. |
| **Integração com GitHub API real** | Simulação de dados; integração real é escopo de v1+. |
| **Persistência de estado (localStorage)** | Dados resetam ao reload; v1 pode adicionar persistência. |
| **Autenticação ou autorização** | Página pública; sem controle de acesso nesta versão. |
| **Temas dinâmicos (dark/light mode)** | Design fixo em tema claro; modo escuro é escopo futuro. |

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

### Invariantes Avaliados
1. **ARTIGO 1 — Separação Estrita de Fases e Papéis**
   - ✅ **Conformidade:** Esta spec é **exclusivamente normativa**; não contém código de implementação, apenas contratos comportamentais e critérios de aceitação.
   - ✅ **Implicação:** O Agente 2 (Plan Architect) gerará `plan_v0.md` com sub-issues MoSCoW; o Build Runner implementará isoladamente.

2. **ARTIGO 2 — Inviolabilidade da Linha de Base**
   - ✅ **Conformidade:** F01 é nova feature; não altera contratos existentes em `Features_state.md`.
   - ✅ **Implicação:** Após validação positiva, será adicionada como novo entry em baseline.

3. **ARTIGO 3 — Determinismo e Matriz de Corte MoSCoW**
   - ✅ **Conformidade:** Critérios de aceitação são computáveis e auditáveis via `scripts/eval_moscow.py`.
   - ✅ **Implicação:** Score final = (MUST_atendidos / MUST_totais) × 100%; merge bloqueado se < 100%.

4. **ARTIGO 4 — Prevenção de Deriva Cognitiva**
   - ✅ **Conformidade:** Esta spec declara explicitamente NON-GOALS e INVARIANTS TOUCHED.
   - ✅ **Implicação:** Agentes devem rejeitar qualquer expansão de escopo não autorizada.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

### 🔴 MUST HAVE (Bloqueadores de Merge — 100% obrigatório)

| ID | Critério | Descrição | Verificação |
|----|----------|-----------|------------|
| **M1** | Renderização HTML5 válida | Página deve ser HTML5 válido, sem erros de parsing. | `html5-validator` ou `W3C Markup Validator` |
| **M2** | Cabeçalho com identidade | Exibir "Harness_teste" + link para Replicable Harness v6 docs. | Inspeção visual; link funcional. |
| **M3** | Indicadores de 3 pipelines | Mostrar status (RUNNING/SUCCESS/FAILED) para GH Stage 1, GH Stage 2, Antigravity Stage 3. | Cada pipeline renderiza com ícone + label + timestamp. |
| **M4** | Matriz MoSCoW com contadores | Exibir cards com MUST (n), SHOULD (n), COULD (n) features. | Contadores visíveis e atualizáveis via JS. |
| **M5** | Console de log simulado | Renderizar área de log com 3 retries de autoafinação (Retry 1, 2, 3). | Logs aparecem com timestamps; transições de cor (amarelo→verde). |
| **M6** | Responsividade mobile | Página funciona em viewport 320px (mobile), 768px (tablet), 1024px+ (desktop). | Teste em DevTools; sem overflow horizontal. |
| **M7** | Acessibilidade WCAG 2.1 AA | Contraste ≥4.5:1; navegação por teclado (Tab); ARIA labels em elementos interativos. | axe DevTools ou Lighthouse audit. |
| **M8** | Zero dependências externas | Nenhum `<script src="...">` para bibliotecas; apenas CSS inline + JS inline. | Inspeção do HTML; nenhuma requisição HTTP para libs. |

### 🟡 SHOULD HAVE (Otimizações — máximo esforço, não bloqueador)

| ID | Critério | Descrição | Verificação |
|----|----------|-----------|------------|
| **S1** | Animações suaves | Transições CSS3 para mudanças de estado (0.3s ease-in-out). | Inspeção visual; sem jank (60fps). |
| **S2** | Simulação de tempo real | Console de log atualiza a cada 2s com novos eventos de retry. | Observar mudanças no console ao longo do tempo. |
| **S3** | Paleta de cores temática | Usar cores que remetem a "desenvolvimento" (azul, verde, laranja, vermelho). | Inspeção visual; paleta coerente. |
| **S4** | Ícones SVG inline | Usar SVG puro (não imagens externas) para ícones de status. | Inspeção do HTML; `<svg>` inline. |
| **S5** | Rodapé com metadados | Exibir versão da spec (v0), data de geração, hash de commit (simulado). | Rodapé visível com informações. |

### 🔵 COULD HAVE (Desejos — escopo futuro)

| ID | Critério | Descrição | Escopo |
|----|----------|-----------|--------|
| **C1** | Modo escuro | Toggle para tema dark mode. | v1+ |
| **C2** | Integração com GitHub API | Buscar status real de workflows. | v1+ |
| **C3** | Gráficos de histórico | Chart.js ou D3.js para tendências de features. | v2+ |
| **C4** | Notificações push | Alertar quando pipeline falha. | v2+ |

---

## 🏗️ 5. Estrutura de Artefatos Esperados

### Arquivo Principal
- **Caminho:** `docs/status-page/index.html`
- **Tamanho máximo:** 50 KB (HTML + CSS + JS inline)
- **Encoding:** UTF-8

### Estrutura Interna do HTML
```
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Harness_teste — Status de Desenvolvimento</title>
    <style>/* CSS inline aqui */</style>
  </head>
  <body>
    <!-- Cabeçalho -->
    <!-- Seção de Pipelines -->
    <!-- Seção MoSCoW -->
    <!-- Console de Log -->
    <!-- Rodapé -->
    <script>/* JS inline aqui */</script>
  </body>
</html>
```

---

## 🎨 6. Especificação de Componentes Visuais

### 6.1 Cabeçalho (Header)
- **Altura:** 80px (desktop), 60px (mobile)
- **Conteúdo:**
  - Logo/Ícone (20×20px)
  - Título: "Harness_teste — Status de Desenvolvimento"
  - Link: "→ Replicable Harness v6" (abre em nova aba)
- **Fundo:** Gradiente azul (#0066cc → #0052a3)
- **Texto:** Branco (#ffffff)

### 6.2 Seção de Pipelines (Pipeline Status)
- **Layout:** 3 cards em grid (1 coluna mobile, 3 colunas desktop)
- **Card por pipeline:**
  - Título: "GitHub Actions Stage 1" / "GitHub Actions Stage 2" / "Antigravity Desktop Stage 3"
  - Ícone de status: ⏳ (RUNNING), ✅ (SUCCESS), ❌ (FAILED)
  - Cor de fundo: Amarelo (#fff3cd) / Verde (#d4edda) / Vermelho (#f8d7da)
  - Timestamp: "Última atualização: 2025-01-16 14:32:15 UTC"
  - Progresso: Barra de progresso (0-100%)

### 6.3 Seção MoSCoW (Feature Matrix)
- **Layout:** 3 cards em grid (1 coluna mobile, 3 colunas desktop)
- **Card por categoria:**
  - Título: "MUST HAVE" / "SHOULD HAVE" / "COULD HAVE"
  - Contador grande: "12" (número de features)
  - Percentual de conclusão: "100%" / "75%" / "0%"
  - Barra de progresso circular (SVG)
  - Cor temática: Vermelho (#dc3545) / Laranja (#fd7e14) / Azul (#0066cc)

### 6.4 Console de Log (Retry Simulation)
- **Layout:** Área monoespacial (font-family: monospace)
- **Altura:** 300px (desktop), 200px (mobile)
- **Fundo:** Preto (#1a1a1a)
- **Texto:** Verde (#00ff00)
- **Conteúdo simulado:**
  ```
  [14:32:15] Iniciando autoafinação...
  [14:32:17] Retry 1/3: Compilando spec...
  [14:32:19] ✓ Spec compilada com sucesso
  [14:32:21] Retry 2/3: Validando critérios MoSCoW...
  [14:32:23] ✓ 12/12 MUST HAVE atendidos
  [14:32:25] Retry 3/3: Finalizando...
  [14:32:27] ✓ Build elegível para merge
  ```
- **Scroll:** Automático para o final (tail behavior)

### 6.5 Rodapé (Footer)
- **Altura:** 40px
- **Conteúdo:**
  - "Spec v0 | Gerado em 2025-01-16 | Hash: abc1234d (simulado)"
  - Link: "Editar spec" (aponta para `spec_v0.md` no GitHub)
- **Fundo:** Cinza (#f8f9fa)
- **Texto:** Cinza escuro (#495057)

---

## 🔄 7. Comportamento Dinâmico (JavaScript)

### 7.1 Simulação de Pipelines
- **Ciclo:** A cada 5 segundos, atualizar status de um pipeline aleatoriamente.
- **Estados:** RUNNING → SUCCESS (ou FAILED com 10% de chance).
- **Progresso:** Incrementar barra de progresso de 0% a 100% durante RUNNING.

### 7.2 Simulação de Retries
- **Acionador:** Ao carregar a página, iniciar simulação de 3 retries.
- **Intervalo:** 2 segundos entre eventos de log.
- **Eventos:**
  1. "Iniciando autoafinação..."
  2. "Retry 1/3: Compilando spec..."
  3. "✓ Spec compilada com sucesso"
  4
