# Especificação Normativa: F02 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini 3.1 Pro (gemini-3.1-pro-preview)`
- **Versão Técnica do Modelo:** `gemini-3.1-pro-preview`
- **Data e Horário da Compilação:** `2026-08-14T13:11:33Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


Como **Agente 1 (Spec Compiler)** do REPLICABLE_HARNESS v6, reconheço e internalizo o **CONSTITUTION.md** como inviolável e canônico. Minha função é estritamente analítica e normativa: não gerarei código de implementação nem planos de execução (ARTIGO 1.1). 

Como você não forneceu um requisito específico no prompt, elaborei a **Especificação Normativa Executável (`spec_v0.md`)** utilizando um modelo de alta densidade semântica com *placeholders* estruturais `[ENTRE COLCHETES]`. Este artefato está pronto para ser preenchido com o seu requisito real, garantindo ancoragem contra deriva cognitiva e determinismo na avaliação.

Por favor, forneça o requisito específico para que eu possa compilar a versão final, ou utilize o *blueprint* canônico abaixo.

# `spec_v0.md` — Especificação Normativa Executável

**Status:** DRAFT INICIAL (Aguardando Injeção de Requisito)  
**Fronteira de Contrato (Contract Boundary):** `[Definir Domínio/Módulo Afetado]`  
**Hash de Rastreabilidade:** `[Gerado no momento da compilação]`

## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

Esta especificação define a topologia comportamental e as fronteiras de contrato para a implementação de `[NOME_DO_REQUISITO]`. O objetivo primário é estabelecer uma transição de estado determinística no sistema, garantindo que a nova funcionalidade opere de forma idempotente e isolada.

*   **Estado Atual (Baseline):** O sistema atualmente `[descrever o comportamento atual ou a ausência da funcionalidade]`.
*   **Estado Alvo (Target State):** Após a integração, o sistema deverá `[descrever o comportamento esperado, fluxos de dados e respostas do sistema]`.
*   **Fronteiras de Contrato (Contract Boundaries):** A implementação deve expor apenas as interfaces estritamente necessárias (`[listar interfaces/APIs/contratos]`), encapsulando a lógica interna para evitar acoplamento sistêmico.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para prevenir a expansão não autorizada de escopo (*scope creep*) e mitigar qualquer deriva cognitiva (*cognitive drift*) durante as fases de planejamento (Agente 2) e construção (Build Runner), os seguintes itens estão **expressamente excluídos** desta especificação:

1.  **[Exemplo: Refatoração Arquitetural]:** Nenhuma alteração na arquitetura base de `[Módulo X]` será tolerada.
2.  **[Exemplo: Modificação de UI/UX]:** O escopo é estritamente *backend/lógica de negócios*. Nenhuma interface de usuário será criada ou alterada.
3.  **Alteração de Invariantes:** Nenhuma modificação nos arquivos sob o diretório `governance/`, `.github/workflows/` ou `docs/REPLICABLE_HARNESS_V6.md`.
4.  **[Exemplo: Otimização Prematura]:** Não é objetivo desta iteração otimizar a latência do banco de dados além dos limites aceitáveis padrão.

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

A execução desta especificação será auditada contra os seguintes invariantes constitucionais:

*   **ARTIGO 1.3 & 2.1 (Isolamento e Baseline):** A implementação não pode, sob nenhuma hipótese, quebrar os contratos já consolidados no arquivo `governance/Features_state.md`.
*   **ARTIGO 3.1 (Determinismo MoSCoW):** A aprovação desta especificação está condicionada ao atendimento de 100% dos critérios `MUST HAVE` listados na Seção 4.
*   **ARTIGO 4.2 (Ancoragem Anti-Deriva):** Esta seção atua como âncora de contexto obrigatória para o Agente 2 (Plan Architect) e para o Validation Agent.

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A matriz de corte abaixo será utilizada pelo script `scripts/eval_moscow.py` para cômputo determinístico do *score* de aceitação.

### 🔴 MUST HAVE (Inviolável - 100% Obrigatório para Merge)
*Estes critérios representam o núcleo funcional. Falha em qualquer um destes invalida o PR.*
1.  **[Critério 1]:** O sistema DEVE `[ação determinística e testável, ex: retornar HTTP 200 com payload X ao receber requisição Y]`.
2.  **[Critério 2]:** A implementação DEVE garantir que `[condição de contorno, ex: dados sensíveis não sejam logados em plain-text]`.
3.  **[Critério 3]:** O código DEVE passar em todos os testes de regressão automatizados sem alterar o `Features_state.md` existente.

### 🟡 SHOULD HAVE (Alvo do Laço de Autoafinação - 3 Retries)
*Estes critérios agregam valor significativo e devem ser perseguidos pelo Build Runner no laço de retentativas locais.*
1.  **[Critério 1]:** O tempo de resposta da operação DEVERIA ser inferior a `[X]ms` no percentil 95.
2.  **[Critério 2]:** O sistema DEVERIA incluir cobertura de testes unitários superior a `[X]%` para as novas classes de domínio introduzidas.
3.  **[Critério 3]:** O sistema DEVERIA emitir eventos de telemetria estruturados para a operação `[Z]`.

**Aguardando input:** Por favor, forneça o requisito de negócio ou técnico desejado para que eu possa substituir os *placeholders* e gerar a especificação normativa final e imutável para o Agente 2.
