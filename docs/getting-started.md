# Getting Started

This guide helps you set up and understand the WTAI documentation site.

## Prerequisites

- Python 3.8+
- MkDocs and Material theme (installed via pip)

## Run locally

```bash
mkdocs serve
```

Access at http://127.0.0.1:8000

## Mermaid diagram: Documentation workflow

```mermaid
flowchart LR
A[Write Markdown] --> B[Live Preview]
B --> C[Commit to Git]
C --> D[GitHub Actions Builds]
D --> E[GitHub Pages Deploy]
```

## Mermaid diagram: Contribution process

```mermaid
sequenceDiagram
participant U as User
participant R as Repo
participant CI as GitHub Actions
participant P as Pages
U->>R: Open PR
R->>CI: Trigger workflow
CI->>P: Publish site
P-->>U: Live docs
```
