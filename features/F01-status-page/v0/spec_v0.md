# Especificação Normativa: F01 (v0)
**Feature ID:** `F01`  
**Slug:** `status-page`  
**Versão:** `v0` (POC)  
**Status:** Aprovado para Arquitetura  

---

## 🎯 1. Desenho Comportamental e Fronteira de Contrato (Behavioral Blueprint)

Esta especificação define o comportamento, a interface e as regras de conformidade para a **Página de Status de Desenvolvimento** do repositório `Harness_teste`. O objetivo é fornecer uma interface de usuário (UI) estática, porém altamente interativa, que sirva como o painel de controle visual (dashboard) do estado de governança e progresso do harness.

### 1.1. Comportamento Esperado da Interface (UX/UI)
- **Fronteira de Apresentação:** A interface deve ser contida em um único arquivo HTML autônomo (SPA estática) que renderize instantaneamente no navegador sem necessidade de compilação ou servidores de aplicação ativos.
- **Design System:** Estética *developer-centric* (tema escuro por padrão, fontes monoespaçadas para dados, elementos visuais limpos com transições suaves via CSS).
- **Responsividade:** Adaptação fluida entre resoluções de desktop (1920x1080) e dispositivos móveis (mínimo de 320px de largura).

### 1.2. Elementos Funcionais Obrigatórios
1. **Header de Identificação:** Exibição clara do nome do repositório (`Harness_teste`), versão da especificação (`v0`) e um link de navegação funcional para o "Harness Central".
2. **Painel da Arquitetura Híbrida:** Representação visual dos três estágios do pipeline:
   - *Stage 1 (GitHub Actions):* Validação de Sintaxe e Invariantes.
   - *Stage 2 (GitHub Actions):* Geração de Artefatos e Orquestração.
   - *Stage 3 (Antigravity Desktop):* Execução Local e Autoafinação.
3. **Matriz de Métricas MoSCoW:** Exibição tabular ou em cards das features do projeto categorizadas por prioridade (MUST, SHOULD, COULD), exibindo o status de completude de cada uma.
4. **Console de Simulação de Logs:** Um terminal interativo emulado em tela que demonstra visualmente o comportamento do laço de autoafinação de 3 retries (*3-retry self-tuning loop*).

---

## 🚫 2. Limites de Escopo (NON-GOALS)

Para garantir a aderência estrita ao cronograma e evitar a deriva cognitiva (*scope creep*), os seguintes pontos estão explicitamente fora do escopo desta versão `v0`:

- **NON-GOAL 1:** Conexão em tempo real com APIs externas (ex: GitHub API, WebSockets ou bancos de dados). Todos os dados de status nesta versão serão mockados diretamente no client-side.
- **NON-GOAL 2:** Uso de frameworks pesados de SPA (como React, Angular ou Vue) ou pré-processadores de CSS (SASS/LESS). A implementação deve usar estritamente HTML5, Vanilla CSS e Vanilla JS.
- **NON-GOAL 3:** Mecanismos de autenticação, controle de acesso ou persistência de estado no servidor.
- **NON-GOAL 4:** Execução real de comandos de terminal ou scripts de build a partir da página. O console é estritamente uma simulação visual interativa.

---

## 🏛️ 3. Invariantes Constitucionais Afetados (INVARIANTS TOUCHED)

A implementação desta especificação deve respeitar e refletir visualmente os seguintes princípios do `CONSTITUTION.md`:

- **Artigo 1 — Separação Estrita de Fases:** A página deve exibir visualmente a separação clara entre as fases de CI (Stage 1 e 2) e a fase de execução local isolada (Stage 3 - Antigravity Desktop).
- **Artigo 3 — Determinismo e Matriz de Corte MoSCoW:** A visualização da matriz MoSCoW na tela deve refletir a regra constitucional de que 100% dos requisitos *MUST HAVE* são obrigatórios para elegibilidade de merge, destacando visualmente essa barreira de qualidade.
- **Artigo 4 — Prevenção de Deriva Cognitiva:** A página deve exibir uma seção ou link para os limites de escopo ativos, ancorando visualmente o desenvolvedor aos limites do projeto.

---

## 📊 4. CRITÉRIOS DE ACEITAÇÃO MoSCoW

O sucesso da implementação desta feature será avaliado deterministicamente com base nos critérios abaixo.

### 4.1. MUST HAVE (Obrigatório para aprovação da Build)
- **F01-MH01:** Criar um arquivo HTML único (ex: `index.html` ou `status.html`) contendo toda a estrutura, estilo e comportamento (CSS e JS embutidos ou em arquivos locais relativos, sem dependências externas de rede complexas).
- **F01-MH02:** O cabeçalho deve conter o título "Harness_teste - Status de Desenvolvimento" e um link funcional (`<a>`) apontando para o repositório central ou documento de governança.
- **F01-MH03:** Exibir um painel visual com o status dos 3 estágios da arquitetura híbrida (Stage 1, Stage 2, Stage 3), utilizando cores distintas para representar estados (ex: Verde para *Success/Active*, Cinza ou Azul para *Idle/Pending*).
- **F01-MH04:** Apresentar a tabela/matriz MoSCoW listando pelo menos a feature `F01` com seus respectivos critérios de aceitação e status de homologação.
- **F01-MH05:** Garantir que o layout seja responsivo e não quebre em telas menores (testado via emulação mobile do Chrome/Firefox).

### 4.2. SHOULD HAVE (Altamente recomendado para maximização do Score)
- **F01-SH01:** Implementar o Console de Log Interativo com um botão "Iniciar Simulação" (ou "Run Self-Tuning"). Ao ser clicado, o console deve imprimir linha a linha (com delay realista de digitação/processamento) a simulação do laço de 3 retries do agente de IA, culminando em um status de sucesso.
- **F01-SH02:** Utilizar variáveis CSS (Custom Properties) para gerenciar a paleta de cores (tema escuro moderno, ex: fundo `#0d1117`, textos `#c9d1d9`, acentos em `#58a6ff` e `#2ea44f`).
- **F01-SH03:** Garantir acessibilidade básica (contraste de cores adequado para leitura de código e tags semânticas HTML5 como `<header>`, `<main>`, `<section>`, `<footer>`).
- **F01-SH04:** Zero dependências de CDNs externas para fontes ou ícones (utilizar fontes seguras do sistema como `system-ui`, `-apple-system`, `monospace`).