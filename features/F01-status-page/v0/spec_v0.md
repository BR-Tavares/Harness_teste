# Especificação Normativa: F01 (v0)

---

## 📑 Metadados de Auditoria (Compiler Provenance)
- **Identidade do Compilador:** Agente 1 (Spec Compiler) — REPLICABLE_HARNESS v6
- **Versão Técnica do Modelo:** `GPT-4o-2024-05-13 / Spec Compiler Engine v6.0.1`
- **Data e Horário da Compilação:** `2026-08-14T04:13:52Z`
- **Status da Especificação:** Normativa / Ativa (v0)

---

## 🎯 1. Visão Geral e Objetivos de Negócio (Behavioral Blueprint)

Esta especificação define o comportamento, a estrutura e as restrições de interface para a **Página de Status de Desenvolvimento do Repositório Harness_teste** (`F01`). 

O objetivo de negócio é fornecer uma interface de usuário (UI) estática, moderna e de alta fidelidade visual que sirva como o painel central de observabilidade para o ecossistema de testes e automação do `Replicable Harness v6`. A página deve consolidar visualmente o estado da arquitetura híbrida de execução, as métricas de conformidade MoSCoW e simular o comportamento do laço de autoafinação local.

---

## 🚫 2. Limites de Escopo (NON-GOALS)

Para garantir a aderência estrita ao escopo da versão `v0` (Proof of Concept) e evitar a deriva cognitiva (*scope creep*), os seguintes itens estão explicitamente fora do escopo desta especificação:

- **NON-GOAL 1:** Integração em tempo real com APIs dinâmicas de backend, bancos de dados ou webhooks ativos do GitHub nesta versão. Toda a reatividade e exibição de dados devem ser baseadas em estados simulados (*mocked*) no lado do cliente (*client-side*).
- **NON-GOAL 2:** Utilização de frameworks de renderização pesados (como React, Angular, Vue) ou bibliotecas de estilização externas via CDN (como Tailwind CSS ou Bootstrap). A interface deve ser construída exclusivamente com tecnologias web nativas (HTML5, Vanilla CSS e Vanilla JS).
- **NON-GOAL 3:** Mecanismos de autenticação, controle de acesso ou persistência de estado do usuário.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

A implementação desta especificação deve respeitar e refletir os seguintes princípios do `CONSTITUTION.md`:

- **Artigo 1 — Separação Estrita de Fases:** Esta especificação atua estritamente como o limite de contrato (*contract boundary*). Nenhuma linha de código de produção ou plano de tarefas é gerada nesta fase.
- **Artigo 2 — Inviolabilidade da Linha de Base:** A implementação desta página não deve alterar nenhum arquivo contido no diretório `governance/` ou modificar os contratos de baseline estabelecidos em `Features_state.md`.
- **Artigo 3 — Determinismo e Matriz de Corte MoSCoW:** A interface deve expor visualmente a lógica de pontuação e os critérios de aceitação definidos no ecossistema, servindo como um espelho didático do motor de avaliação do Harness.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

A elegibilidade para homologação desta feature depende do atendimento estrito da matriz abaixo, auditada deterministicamente.

### 🟢 MUST HAVE (Obrigatório para liberação da v0)
- **MH1 [Estrutura de Arquivo Único]:** Toda a aplicação deve ser contida em uma estrutura estática simples (ex: `index.html` com CSS e JS embutidos ou referenciados localmente), sem necessidade de servidores de build ou empacotadores (Webpack, Vite).
- **MH2 [Identificação do Repositório]:** O cabeçalho da página deve exibir de forma proeminente o nome do repositório `Harness_teste` e conter um link funcional (hiperlink) apontando para o repositório central do Harness.
- **MH3 [Status da Arquitetura Híbrida]:** Exibição visual clara e distinta de três blocos/cards representando os estágios de execução:
  - **Stage 1:** GitHub Actions (Validação de Sintaxe e Invariantes).
  - **Stage 2:** GitHub Actions (Geração de Plano e Alocação).
  - **Stage 3:** Antigravity Desktop (Execução Local e Autoafinação).
- **MH4 [Matriz de Métricas MoSCoW]:** Exibição de um painel contendo a distribuição de requisitos (MUST, SHOULD, COULD) e um indicador visual do score de conformidade atual do repositório.
- **MH5 [Zero Dependências Externas de Runtime]:** A página deve renderizar perfeitamente offline ou sem conexão com CDNs externas. Todo o CSS e comportamento interativo devem ser nativos.

### 🟡 SHOULD HAVE (Altamente recomendado para experiência do usuário)
- **SH1 [Console de Log Interativo]:** Um componente visual que simula um terminal/console de log. Ao carregar a página ou ao clicar em um botão de "Simular Execução", o console deve exibir sequencialmente (com delay realista) as linhas de log do laço de autoafinação de 3 retries (ex: *Retry 1/3: Falha detectada...*, *Retry 2/3: Ajustando parâmetros...*, *Retry 3/3: Sucesso!*).
- **SH2 [Design Responsivo e Estética Dark Mode]:** A interface deve adotar uma paleta de cores escura (Dark Mode por padrão), utilizando variáveis CSS para consistência visual, inspirada em ferramentas de terminal e IDEs modernas, adaptando-se fluidamente a telas de dispositivos móveis e desktops.
- **SH3 [Indicadores de Status Dinâmicos]:** Elementos visuais (como badges ou LEDs virtuais) que mudam de cor (verde para sucesso, amarelo para em execução, vermelho para falha) com base no estado simulado do console de log.

---

## 🔌 5. Contratos de Interface e Comportamento (Contract Boundaries)

### 5.1 Estrutura Semântica do DOM
A página deve seguir uma estrutura semântica rigorosa para garantir acessibilidade e clareza de leitura de máquina:
- `<header>`: Contendo o título principal, metadados do repositório e o link externo.
- `<main>`: Grid principal contendo as seções de status da arquitetura, métricas MoSCoW e o