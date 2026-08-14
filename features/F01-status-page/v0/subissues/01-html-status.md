# [SUB-ISSUE] #01 — Implementação da Interface HTML de Status

**Feature Pai:** `F01` | **Versão:** `v0` | **Label:** `antigravity:ready`
**Âncora Constitucional:** `governance/constitution.md`

---

## 🎯 Escopo da Sub-issue
Implementar a interface autossuficiente `index.html` atendendo rigorosamente aos critérios da especificação `spec_v0.md`.

---

## 📊 Critérios MoSCoW

### 🔴 MUST HAVE (100% Obrigatório para Merge)
- [ ] **MUST-01:** Renderização em arquivo único `index.html` sem dependências remotas CDN.
- [ ] **MUST-02:** Cabeçalho semântico com título e link para o Harness Central.
- [ ] **MUST-03:** Cards de status dos estágios da arquitetura híbrida (Stage 1, 2 e 3).
- [ ] **MUST-04:** Painel de métricas MoSCoW.

### 🟡 SHOULD HAVE (Autoafinação)
- [ ] **SHOULD-01:** Design responsivo com CSS Grid / Flexbox.
- [ ] **SHOULD-02:** Console interativo simulando o laço de 3 retries de autoafinação.
- [ ] **SHOULD-03:** Tema escuro nativo (Dark Mode) com variáveis CSS.
