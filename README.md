# Harness_teste — Repositório Consumidor do Replicable Harness v6

[![Harness Engine](https://img.shields.io/badge/Powered%20By-Replicable_Harness_spec_gh--aw-blue.svg)](https://github.com/BR-Tavares/Replicable_Harness_spec_gh-aw)
[![Status](https://img.shields.io/badge/Status-Development%20Active-green.svg)](index.html)

Este repositório é uma demonstração prática de um repositório consumidor que utiliza o **[Replicable Harness v6](https://github.com/BR-Tavares/Replicable_Harness_spec_gh-aw)** de forma desacoplada via `workflow_call`, sem necessidade de duplicar arquivos de scripts ou regras centrais.

---

## 🔗 Integração com o Harness Central (`workflow_call`)

O repositório invoca a engine de especificação reutilizável diretamente do repositório central:

```yaml
# .github/workflows/harness.yml
name: Invoke Harness v6
on:
  issues:
    types: [opened, labeled]
  workflow_dispatch:

jobs:
  spec-and-plan:
    uses: BR-Tavares/Replicable_Harness_spec_gh-aw/.github/workflows/reusable-harness.lock.yml@main
    with:
      feature_id: "F01"
      version: "v0"
    secrets:
      ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
```

---

## 🚀 Aplicação de Exemplo: Status Dashboard (`index.html`)

O ciclo `F01-status-page` implementa uma página web responsiva que exibe o status em tempo real do desenvolvimento do projeto `Harness_teste`.

Para visualizar localmente:
Abra o arquivo [`index.html`](file:///c:/Users/andre/Documents/antigravity/Harness_teste/index.html) diretamente em qualquer navegador moderno.
