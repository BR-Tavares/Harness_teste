# Especificação Normativa: F01-v0 — Página de Status de Desenvolvimento

**Status:** APROVADA  
**Maturidade:** `v0` (POC)  
**Âncora Constitucional:** Conforme regras imutáveis do `BR-Tavares/Replicable_Harness_spec_gh-aw`

---

## 🎯 1. Escopo & Comportamento Esperado (Behavioral Blueprint)
A página web deve ser acessível via `index.html` e apresentar:
1. **Hero Header:** Título do projeto, status de conectividade com o Harness central e badge de baseline.
2. **Matriz de Estágios Operacionais:**
   - Estágio 1: Elicitação & Compilação de Spec (`gh-aw`).
   - Estágio 2: Decomposição & Sub-issues MoSCoW (`gh-aw`).
   - Estágio 3: Autoafinação no Antigravity Desktop (3 retries).
   - Estágio 4: Validação Independente no PR (CI).
3. **Métricas MoSCoW:** Cards interativos detalhando os critérios MUST, SHOULD e COULD.
4. **Visualizador de Logs:** Card simulando a execução dos 3 retries no Antigravity Desktop.

---

## 🚫 2. Limites de Escopo (NON-GOALS)
- **NON-GOAL 1:** Sem dependência de bundlers (Webpack, Vite) — puro HTML/CSS/JS.
- **NON-GOAL 2:** Sem autenticação de usuários.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)
- [x] Respeita o padrão canônico de diretórios `features/F<ID>-slug/vN/`.
- [x] Totalmente responsivo para dispositivos móveis e desktop.
- [x] Sem recursos externos bloqueantes.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

### MUST HAVE (Obrigatórios — 100%)
1. **MUST-01:** Estrutura HTML5 semântica completa (`index.html`) com viewport responsivo.
2. **MUST-02:** Estilização limpa e profissional com CSS moderno (`style.css`), tipografia nítida e hierarquia clara.
3. **MUST-03:** Apresentação clara dos 4 estágios do Replicable Harness e status ativo do `Harness_teste`.

### SHOULD HAVE (Alvo dos Retries)
1. **SHOULD-01:** Animações sutis de micro-interação ao passar o cursor sobre os cards de status.
2. **SHOULD-02:** Botão interativo para simular o laço de 3 retries e atualizar o score MoSCoW dinamicamente via JS.
