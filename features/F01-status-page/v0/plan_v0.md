# plan_v0.md — Plano Arquitetural de Tarefas (F01)

**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão Plano:** `v0`  
**Data de Emissão:** 2025-01-16  
**Arquiteto:** Agente 2 (Plan Architect)

---

## 📋 METADADOS DE AUDITORIA

| Campo | Valor |
|-------|-------|
| **Especificação Base** | `spec_v0.md` (Agente 1 — Spec Compiler) |
| **Versão Técnica do Modelo** | `claude-haiku-4-5-20251001` |
| **Data de Geração do Plano** | 2025-01-16T13:09:38Z |
| **Status do Plano** | EXECUTÁVEL / PRONTO PARA BUILD |
| **Conformidade Constitucional** | ✅ ARTIGOS 1-4 validados |

---

## 🏛️ INVARIANTES CONSTITUCIONAIS AFETADOS

### Invariantes Avaliados
1. **ARTIGO 1 — Separação Estrita de Fases e Papéis**
   - ✅ **Conformidade:** Este plano é **exclusivamente arquitetural**; não contém código de implementação.
   - ✅ **Implicação:** Build Runner implementará isoladamente via sub-issues MoSCoW; nenhuma alteração a `spec_v0.md`.

2. **ARTIGO 2 — Inviolabilidade da Linha de Base**
   - ✅ **Conformidade:** Plano não altera `Features_state.md`; apenas decompõe F01 em tarefas atômicas.
   - ✅ **Implicação:** Após validação positiva, F01 será adicionada como novo entry em baseline.

3. **ARTIGO 3 — Determinismo e Matriz de Corte MoSCoW**
   - ✅ **Conformidade:** Decomposição segue matriz MoSCoW; score computável via `scripts/eval_moscow.py`.
   - ✅ **Implicação:** Merge bloqueado se qualquer MUST HAVE não atingir 100%.

4. **ARTIGO 4 — Prevenção de Deriva Cognitiva**
   - ✅ **Conformidade:** Plano declara explicitamente NON-GOALS e limites de escopo.
   - ✅ **Implicação:** Build Runner deve rejeitar qualquer expansão não autorizada.

---

## 🚫 NON-GOALS (Escopo Explicitamente Excluído)

| NON-GOAL | Justificativa | Responsabilidade |
|----------|---------------|------------------|
| **Modificação de `spec_v0.md`** | Spec é imutável após compilação; alterações requerem novo ciclo Agente 1. | Build Runner |
| **Alteração de `governance/*`** | Arquivos constitucionais são read-only; violação bloqueia PR. | CI/CD (`check_invariants.py`) |
| **Integração com GitHub API real** | Escopo de v1+; v0 usa dados hardcoded. | Agente 2 (Plan Architect) |
| **Persistência de estado (localStorage)** | Escopo de v1+; v0 reseta ao reload. | Agente 2 (Plan Architect) |
| **Bibliotecas externas (React, Vue, Bootstrap)** | Vanilla CSS3 + ES6 puro obrigatório. | Build Runner |
| **Temas dinâmicos (dark/light mode)** | Escopo de v1+; design fixo em tema claro. | Agente 2 (Plan Architect) |

---

## 📊 DECOMPOSIÇÃO MOSCOW — MATRIZ DE TAREFAS

### 🔴 MUST HAVE (Bloqueadores de Merge — 100% obrigatório)

#### **MUST-01: Renderização HTML5 Válida**
- **Descrição:** Página deve ser HTML5 válido, sem erros de parsing.
- **Critério de Aceitação:**
  - ✅ Arquivo `docs/status-page/index.html` criado com doctype `<!DOCTYPE html>`.
  - ✅ Validação W3C Markup Validator retorna 0 erros.
  - ✅ Meta tags obrigatórias presentes: `charset="UTF-8"`, `viewport`.
- **Esforço Estimado:** 1 ponto (trivial)
- **Dependências:** Nenhuma
- **Responsável:** Build Runner
- **Verificação:** `html5-validator docs/status-page/index.html`

---

#### **MUST-02: Cabeçalho com Identidade Visual**
- **Descrição:** Exibir "Harness_teste" + link para Replicable Harness v6 docs.
- **Critério de Aceitação:**
  - ✅ Cabeçalho renderiza com altura 80px (desktop), 60px (mobile).
  - ✅ Gradiente azul (#0066cc → #0052a3) aplicado.
  - ✅ Título "Harness_teste — Status de Desenvolvimento" visível em branco.
  - ✅ Link "→ Replicable Harness v6" funcional (abre em nova aba).
  - ✅ Logo/ícone 20×20px presente.
- **Esforço Estimado:** 2 pontos
- **Dependências:** MUST-01
- **Responsável:** Build Runner
- **Verificação:** Inspeção visual + teste de link

---

#### **MUST-03: Indicadores de 3 Pipelines**
- **Descrição:** Mostrar status (RUNNING/SUCCESS/FAILED) para GH Stage 1, GH Stage 2, Antigravity Stage 3.
- **Critério de Aceitação:**
  - ✅ 3 cards renderizados em grid (1 coluna mobile, 3 colunas desktop).
  - ✅ Cada card exibe: título, ícone de status (⏳/✅/❌), label, timestamp.
  - ✅ Cores de fundo corretas: Amarelo (#fff3cd) / Verde (#d4edda) / Vermelho (#f8d7da).
  - ✅ Barra de progresso (0-100%) presente em cada card.
  - ✅ Simulação de atualização a cada 5 segundos (JS).
- **Esforço Estimado:** 3 pontos
- **Dependências:** MUST-01, MUST-02
- **Responsável:** Build Runner
- **Verificação:** Inspeção visual + console JS sem erros

---

#### **MUST-04: Matriz MoSCoW com Contadores**
- **Descrição:** Exibir cards com MUST (n), SHOULD (n), COULD (n) features.
- **Critério de Aceitação:**
  - ✅ 3 cards renderizados em grid (1 coluna mobile, 3 colunas desktop).
  - ✅ Cada card exibe: título ("MUST HAVE" / "SHOULD HAVE" / "COULD HAVE"), contador grande (ex: "12").
  - ✅ Percentual de conclusão visível (ex: "100%", "75%", "0%").
  - ✅ Barra de progresso circular (SVG) presente.
  - ✅ Cores temáticas: Vermelho (#dc3545) / Laranja (#fd7e14) / Azul (#0066cc).
  - ✅ Contadores atualizáveis via JS (simulação).
- **Esforço Estimado:** 3 pontos
- **Dependências:** MUST-01, MUST-02
- **Responsável:** Build Runner
- **Verificação:** Inspeção visual + teste de atualização JS

---

#### **MUST-05: Console de Log Simulado**
- **Descrição:** Renderizar área de log com 3 retries de autoafinação.
- **Critério de Aceitação:**
  - ✅ Área monoespacial (font-family: monospace) com altura 300px (desktop), 200px (mobile).
  - ✅ Fundo preto (#1a1a1a), texto verde (#00ff00).
  - ✅ Simulação de 3 retries com eventos de log (timestamps, status).
  - ✅ Transições de cor: amarelo (RUNNING) → verde (SUCCESS).
  - ✅ Scroll automático para o final (tail behavior).
  - ✅ Intervalo de 2 segundos entre eventos de log.
- **Esforço Estimado:** 4 pontos
- **Dependências:** MUST-01, MUST-02
- **Responsável:** Build Runner
- **Verificação:** Inspeção visual + teste de simulação de tempo

---

#### **MUST-06: Responsividade Mobile**
- **Descrição:** Página funciona em viewport 320px (mobile), 768px (tablet), 1024px+ (desktop).
- **Critério de Aceitação:**
  - ✅ Sem overflow horizontal em nenhum breakpoint.
  - ✅ Layout adapta corretamente: 1 coluna (mobile) → 3 colunas (desktop).
  - ✅ Fontes legíveis em todos os tamanhos (min 14px mobile, 16px desktop).
  - ✅ Espaçamento (padding/margin) proporcional ao viewport.
  - ✅ Testado em DevTools (Chrome, Firefox, Safari).
- **Esforço Estimado:** 3 pontos
- **Dependências:** MUST-01 a MUST-05
- **Responsável:** Build Runner
- **Verificação:** Teste em DevTools; screenshot em 3 breakpoints

---

#### **MUST-07: Acessibilidade WCAG 2.1 AA**
- **Descrição:** Contraste ≥4.5:1; navegação por teclado (Tab); ARIA labels.
- **Critério de Aceitação:**
  - ✅ Contraste de cores ≥4.5:1 (verificado com axe DevTools).
  - ✅ Navegação por teclado funcional: Tab, Shift+Tab, Enter.
  - ✅ ARIA labels em elementos interativos (botões, links, inputs).
  - ✅ Headings estruturados (h1, h2, h3) em ordem lógica.
  - ✅ Lighthouse audit: score ≥90 em acessibilidade.
- **Esforço Estimado:** 3 pontos
- **Dependências:** MUST-01 a MUST-06
- **Responsável:** Build Runner
- **Verificação:** `axe DevTools` + `Lighthouse audit`

---

#### **MUST-08: Zero Dependências Externas**
- **Descrição:** Nenhum `<script src="...">` para bibliotecas; apenas CSS inline + JS inline.
- **Critério de Aceitação:**
  - ✅ Nenhuma requisição HTTP para bibliotecas externas (React, Vue, Bootstrap, etc.).
  - ✅ CSS inline em `<style>` tag no `<head>`.
  - ✅ JavaScript inline em `<script>` tag no final do `<body>`.
  - ✅ Arquivo HTML único, auto-contido (≤50 KB).
  - ✅ Inspeção do Network tab: 0 requisições externas.
- **Esforço Estimado:** 2 pontos
- **Dependências:** MUST-01 a MUST-07
- **Responsável:** Build Runner
- **Verificação:** Inspeção do HTML + Network tab do DevTools

---

### 🟡 SHOULD HAVE (Otimizações — máximo esforço, não bloqueador)

#### **SHOULD-01: Animações Suaves**
- **Descrição:** Transições CSS3 para mudanças de estado (0.3s ease-in-out).
- **Critério de Aceitação:**
  - ✅ Transições CSS3 aplicadas a mudanças de cor, opacidade, transform.
  - ✅ Duração: 0.3s, timing-function: ease-in-out.
  - ✅ Sem jank (60fps); testado em DevTools Performance tab.
  - ✅ Hover effects em cards e links.
- **Esforço Estimado:** 2 pontos
- **Dependências:** MUST-01 a MUST-08
- **Responsável:** Build Runner
- **Verificação:** Inspeção visual + Performance tab

---

#### **SHOULD-02: Simulação de Tempo Real**
- **Descrição:** Console de log atualiza a cada 2s com novos eventos de retry.
- **Critério de Aceitação:**
  - ✅ Eventos de log aparecem a cada 2 segundos.
  - ✅ Timestamps atualizados automaticamente.
  - ✅ Transições de estado visíveis (amarelo → verde).
  - ✅ Simulação contínua (loop infinito ou até 3 ciclos completos).
- **Esforço Estimado:** 2 pontos
- **Dependências:** MUST-05
- **