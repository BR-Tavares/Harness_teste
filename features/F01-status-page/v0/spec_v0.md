# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** `Google Gemini Engine`
- **Versão Técnica do Modelo:** `gemini-3.5-flash`
- **Data e Horário da Compilação:** `2026-08-14T04:15:47Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---


## 🎯 1. Visão Geral e Desenho Comportamental (Behavioral Blueprint)

A presente especificação define os requisitos comportamentais, de interface e de contrato para a implementação da **F01: Página de Status de Desenvolvimento** do repositório `Harness_teste`. Esta página atua como o painel visual unificado (dashboard) que consolida o estado de conformidade, arquitetura e execução do ciclo de vida do `Replicable Harness v6`.

### 1.1 Fronteira de Contrato (Contract Boundary)
*   **Artefato Principal:** Um único arquivo HTML autossuficiente localizado na raiz do repositório (`index.html`).
*   **Dependências:** Zero dependências de rede externas (scripts CDN, fontes remotas ou frameworks pesados). Todo o estilo e comportamento interativo devem ser resolvidos localmente via Vanilla CSS e Vanilla JS embutidos ou referenciados de forma relativa e offline-first.
*   **Portabilidade:** O arquivo deve ser executável diretamente via protocolo `file://` no navegador ou servido por qualquer servidor estático simples (ex: `python -m http.server`).

### 1.2 Comportamento da Interface (UI/UX Blueprint)
A interface deve ser estruturada em uma grade responsiva (Grid/Flexbox) contendo quatro quadrantes ou seções principais:
1.  **Header de Identificação:** Identifica o repositório alvo (`Harness_teste`) e provê rastreabilidade com link de navegação para o ecossistema central.
2.  **Painel de Arquitetura Híbrida:** Representação visual dos três estágios operacionais do Harness:
    *   *Stage 1 (GitHub Actions):* Validação de Sintaxe e Invariantes.
    *   *Stage 2 (GitHub Actions):* Geração de Plano e Alocação.
    *   *Stage 3 (Antigravity Desktop):* Execução Local e Laço de Autoafinação.
3.  **Matriz de Métricas MoSCoW:** Exibição clara do progresso de conformidade do projeto, detalhando o status dos requisitos (Must Have, Should Have, Could Have).
4.  **Console de Log Interativo:** Um componente simulador de terminal que demonstra visualmente o comportamento do motor de autoafinação (Self-Tuning Loop) em seus ciclos de retry.

## 🚫 2. Limites de Escopo (NON-GOALS)

Para garantir a viabilidade técnica da versão `v0` (Proof of Concept) e evitar a deriva cognitiva (*scope creep*), os seguintes pontos estão explicitamente fora de escopo:
*   **NON-GOAL 1:** Integração em tempo real com APIs dinâmicas do GitHub ou WebSockets ativos nesta versão. Toda a reatividade do console de logs e indicadores deve ser simulada deterministicamente no lado do cliente (client-side mock).
*   **NON-GOAL 2:** Persistência de dados em banco de dados (SQL/NoSQL) ou necessidade de um servidor de aplicação ativo (Node.js, Python, PHP, etc.).
*   **NON-GOAL 3:** Utilização de frameworks de renderização reativa (React, Vue, Angular) ou pré-processadores de CSS que exijam etapa de compilação/build.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

A implementação desta feature interage diretamente com os seguintes princípios do `CONSTITUTION.md`:
*   **Artigo 1 (Separação Estrita de Fases):** A página de status deve refletir visualmente a separação de fases entre o ambiente de CI (GitHub Actions - Stages 1 e 2) e o ambiente local (Antigravity Desktop - Stage 3).
*   **Artigo 3 (Determinismo e Matriz MoSCoW):** A exibição das métricas na página deve seguir estritamente a nomenclatura e a lógica de pontuação auditável do Harness, servindo como espelho visual do arquivo `Features_state.md`.
*   **Áreas Protegidas:** O arquivo gerado (`index.html`) não deve modificar, sobrescrever ou interferir em nenhum arquivo contido no diretório `governance/` ou nos scripts de validação do Harness.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

O sucesso da implementação da feature `F01` será avaliado estritamente com base nos critérios abaixo.

### 4.1 MUST HAVE (Obrigatório para aprovação do Build)

*   **M.1 - Arquivo Único e Autossuficiente:** A entrega deve consistir em um arquivo `index.html` na raiz do repositório, contendo todo o HTML, CSS e JavaScript necessários para renderização completa sem requisições de rede externas.
*   **M.2 - Identificação do Repositório:** O cabeçalho da página deve exibir de forma destacada o título "Harness_teste - Status de Desenvolvimento" e conter um link funcional (tag `<a>`) apontando para o repositório ou painel do "Harness Central".
*   **M.3 - Painel de Arquitetura Híbrida:** Exibir visualmente os três estágios (Stage 1, Stage 2 e Stage 3) com indicadores de status coloridos (ex: Verde para Ativo/Sucesso, Azul para Executando, Cinza para Aguardando).
*   **M.4 - Matriz MoSCoW Estática:** Apresentar uma tabela ou grid contendo a distribuição de requisitos do projeto dividida em colunas/linhas para "MUST HAVE", "SHOULD HAVE" e "COULD HAVE", com seus respectivos estados de conclusão (ex: Concluído, Em Progresso, Pendente).
*   **M.5 - Responsividade Vanilla:** A página deve se adaptar perfeitamente a resoluções mobile (mínimo 320px de largura) e desktop (até 1920px) utilizando apenas CSS Grid, Flexbox e Media Queries nativos.

### 4.2 SHOULD HAVE (Desejável para maximização do Score)

*   **S.1 - Console de Log Interativo (Simulador):** A página deve conter uma seção estilizada como terminal de linha de comando (fundo escuro, fonte monoespaçada) que simule a execução do laço de autoafinação de 3 retries do Harness.
    *   *Comportamento esperado:* Ao carregar a página (ou disparar via botão "Simular"), o console deve imprimir sequencialmente, com pequenos atrasos de tempo (ex: 500ms), linhas de log simulando:
        1.  Início da validação local (Stage 3).
        2.  Falha simulada no Retry 1 (ex: "Erro de asserção no teste de regressão").
        3.  Ajuste automático e execução do Retry 2.
        4.  Sucesso no Retry 3 (ex: "100% dos requisitos MUST HAVE validados. Build elegível para merge!").
*   **S.2 - Controles do Console:** Disponibilizar botões interativos ("Iniciar Simulação", "Pausar", "Limpar Console") para que o usuário possa controlar a animação do terminal de logs.
*   **S.3 - Estética Dark Mode Nativa:** A interface deve adotar por padrão uma paleta
