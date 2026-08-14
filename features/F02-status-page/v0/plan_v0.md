Como **Agente 2 (Plan Architect)** do REPLICABLE_HARNESS v6, reconheço e internalizo o **CONSTITUTION.md** como inviolável e canônico. Em estrita conformidade com o **ARTIGO 1.2**, declaro que não alterarei a especificação fornecida nem gerarei código de implementação. Minha saída é exclusivamente o plano arquitetural e a decomposição em sub-issues MoSCoW.

Tendo em vista que a especificação recebida (`spec_v0.md`) encontra-se no status de **DRAFT INICIAL (Aguardando Injeção de Requisito)** com *placeholders* estruturais, elaborei o **Plano Arquitetural Executável (`plan_v0.md`)** espelhando esta mesma topologia. Este plano está pronto para ser instanciado pelo *Build Runner* assim que os requisitos reais forem injetados.

---

# `plan_v0.md` — Plano de Tarefas Arquiteturais

**Status:** DRAFT INICIAL (Aguardando Injeção de Requisito)  
**Especificação Alvo:** `spec_v0.md` (F02)  
**Fronteira de Contrato:** `[Definir Domínio/Módulo Afetado]`  

## 🏛️ 1. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)
Este plano foi construído sob a égide das seguintes regras constitucionais:
*   **ARTIGO 1.2:** Este artefato restringe-se ao planejamento arquitetural e decomposição de tarefas. Nenhuma linha de código de implementação está contida aqui.
*   **ARTIGO 2.1 & 2.2 (Inviolabilidade da Linha de Base):** As tarefas geradas garantem que o `Features_state.md` não será alterado sem validação prévia.
*   **ARTIGO 3.1 & 3.2 (Determinismo MoSCoW):** A decomposição de tarefas reflete exatamente a matriz de corte da especificação, orientando o *Build Runner* para o laço de autoafinação de 3 retries nos itens *SHOULD HAVE*.

## 🚫 2. Limites de Escopo (NON-GOALS)
Para prevenir deriva cognitiva (*cognitive drift*) e expansão de escopo (*scope creep*):
1.  **Nenhuma alteração na Especificação:** O Agente 2 aceita a `spec_v0.md` como verdade absoluta.
2.  **Nenhuma modificação em áreas protegidas:** O plano proíbe explicitamente que o *Build Runner* toque em `governance/*`, `.github/workflows/*` ou `docs/REPLICABLE_HARNESS_V6.md`.
3.  **Nenhuma implementação de UI/UX ou Refatoração Arquitetural:** O plano foca estritamente nos limites definidos pela Seção 2 da especificação.

---

## 🏗️ 3. Estratégia Arquitetural (Architectural Strategy)

A implementação de `[NOME_DO_REQUISITO]` no domínio `[Definir Domínio/Módulo Afetado]` seguirá uma abordagem de **Isolamento de Contrato**. 
1.  **Setup de Testes (TDD):** O *Build Runner* deverá iniciar escrevendo os testes que validam os critérios MUST HAVE antes da lógica de negócios.
2.  **Implementação Encapsulada:** A lógica interna será isolada, expondo apenas as interfaces estritamente necessárias (`[listar interfaces/APIs/contratos]`).
3.  **Laço de Autoafinação:** Após garantir 100% dos MUST HAVEs, o *Build Runner* utilizará seus 3 retries locais para otimizar latência, cobertura e telemetria (SHOULD HAVEs).

---

## 📋 4. Decomposição em Sub-issues MoSCoW

As tarefas abaixo devem ser executadas sequencialmente pelo **Build Runner (Antigravity Desktop)**. A transição para as tarefas amarelas (SHOULD) só é permitida após a conclusão e passagem de testes de todas as tarefas vermelhas (MUST).

### 🔴 FASE 1: MUST HAVE (Bloqueante para Merge - 100% Obrigatório)
*O não cumprimento de qualquer sub-issue desta fase invalida o PR.*

*   [ ] **`ISSUE-001-MUST`: Implementar Comportamento Core Determinístico**
    *   **Ação:** Desenvolver a lógica para que o sistema execute `[ação determinística e testável, ex: retornar HTTP 200 com payload X ao receber requisição Y]`.
    *   **Validação:** Teste unitário/integração confirmando a transição de estado exata descrita no *Target State* da spec.
*   [ ] **`ISSUE-002-MUST`: Garantir Condições de Contorno e Segurança**
    *   **Ação:** Implementar as travas necessárias para garantir que `[condição de contorno, ex: dados sensíveis não sejam logados em plain-text]`.
    *   **Validação:** Teste de segurança/limite confirmando a restrição.
*   [ ] **`ISSUE-003-MUST`: Validação de Regressão e Baseline**
    *   **Ação:** Executar a suíte de testes completa. Garantir que a nova implementação não quebre nenhum contrato existente.
    *   **Validação:** CI local verde. Nenhuma alteração detectada no comportamento documentado em `Features_state.md`.

### 🟡 FASE 2: SHOULD HAVE (Laço de Autoafinação - Máx 3 Retries)
*O Build Runner deve iterar nestas tarefas para maximizar o score calculado por `scripts/eval_moscow.py`.*

*   [ ] **`ISSUE-004-SHOULD`: Otimização de Performance (Latência)**
    *   **Ação:** Refinar a implementação da `ISSUE-001-MUST` para que o tempo de resposta seja inferior a `[X]ms` no percentil 95.
    *   **Validação:** Benchmark local ou teste de carga simplificado.
*   [ ] **`ISSUE-005-SHOULD`: Expansão de Cobertura de Testes**
    *   **Ação:** Adicionar testes unitários adicionais para as novas classes de domínio introduzidas, visando cobertura superior a `[X]%`.
    *   **Validação:** Relatório de cobertura de código (ex: *coverage/lcov-report*).
*   [ ] **`ISSUE-006-SHOULD`: Instrumentação e Telemetria**
    *   **Ação:** Integrar logs estruturados ou emissão de eventos de telemetria para a operação `[Z]`.
    *   **Validação:** Verificação de saída de logs/eventos no console ou mock de coletor durante os testes.

---
**Aguardando injeção de contexto:** Assim que o Agente 1 compilar a `spec_v1.md` com os requisitos reais de negócio, este plano será automaticamente re-instanciado com os domínios, ações e métricas concretas.