# Especificação Normativa: F01 (v0)

**Status:** APROVADA PELO SPEC COMPILER  
**Ciclo de Maturidade:** `v0`  
**Âncora Constitucional:** `governance/constitution.md`

---

## 🎯 1. Escopo & Comportamento Esperado (Behavioral Blueprint)
# Requisito: F01 — Página de Status de Desenvolvimento do Repositório Harness_teste

**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão:** `v0` (POC)  
**Origem:** Solicitação do Especialista Humano

---

## 🎯 Objetivo de Negócio
Criar uma página HTML moderna, limpa e responsiva que apresente de forma visual o status em tempo real do desenvolvimento do repositório `Harness_teste` e a integração com o `Replicable Harness v6`.

---

## 📋 Escopo Funcional (v0)
1. **Identificação do Repositório:** Cabeçalho com o nome do projeto e link para o Harness Central.
2. **Status da Arquitetura Híbrida:** Indicadores visuais para GitHub Actions (Stage 1 e 2) e Antigravity Desktop (Stage 3).
3. **Métricas MoSCoW:** Exibição da matriz de pontuação de features (MUST, SHOULD, COULD).
4. **Console de Log Interativo:** Simulação visual do laço de autoafinação de 3 retries.

---

## 🚫 Limites de Escopo (NON-GOALS)
- **NON-GOAL 1:** Sem necessidade de backend dinâmico ou banco de dados externo nesta v0 (código estático HTML5/CSS/JS client-side).
- **NON-GOAL 2:** Sem bibliotecas pesadas externas (usar Vanilla CSS moderno).


---

## 🚫 2. Limites de Escopo (NON-GOALS)
- **NON-GOAL 1:** Modificações em arquivos de governança ou áreas protegidas.
- **NON-GOAL 2:** Implementações fora do escopo estrito do requisito da versão v0.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)
- [x] Preserva contratos existentes na baseline ativa.
- [x] Conformidade com regras de isolamento e modularidade MoSCoW.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

### MUST HAVE (Obrigatórios — 100%)
- [ ] **MUST-01:** Implementar os contratos básicos do requisito.
- [ ] **MUST-02:** Suíte de testes determinísticos cobrindo o fluxo principal.

### SHOULD HAVE (Autoafinação)
- [ ] **SHOULD-01:** Tipagem estrita e tratamento defensivo de erros.
