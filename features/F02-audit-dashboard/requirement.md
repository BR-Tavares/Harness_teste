# Requisito Elicitado: F02 — Painel de Auditoria e Conformidade Constitucional

**Feature ID:** `F02`  
**Slug:** `audit-dashboard`  
**Versão:** `v0` (POC)  
**Origem:** Solicitação do Especialista Humano

---

## 🎯 Objetivo de Negócio
Desenvolver uma página web autônoma (`audit.html`) que funcione como o Painel de Auditoria dos Invariantes Constitucionais e Métricas MoSCoW do ecossistema `Harness_teste`, permitindo a conferência visual do status de certificação emitido pelo Validation Agent (Stage 4).

---

## 📋 Escopo Funcional (v0)
1. **Quadro de Invariantes Constitucionais:** Exibição interativa dos 4 artigos da `constitution.md` (Separação de Fases, Linha de Base, MoSCoW 100% e Prevenção de Deriva) com badges de status de conformidade (`[PASS]`).
2. **Medidor Visual de Score MoSCoW:** Gráfico ou barra de progresso visual demonstrando o índice de cumprimento de requisitos MUST HAVE (10 pts) e SHOULD HAVE (3 pts).
3. **Histórico do Laço de Autoafinação:** Tabela interativa detalhando o histórico das 3 tentativas (Retry 1, Retry 2 e Retry 3 Campeão).
4. **Filtros e Responsividade:** Layout moderno, responsivo (Dark Mode nativo) e totalmente offline (Zero dependências de CDN).

---

## 🚫 Limites de Escopo (NON-GOALS)
- **NON-GOAL 1:** Sem backend dinâmico ou banco de dados externo (dados mockados/client-side em Vanilla JS).
- **NON-GOAL 2:** Sem frameworks pesados externos (estritamente HTML5, Vanilla CSS e Vanilla JS).
