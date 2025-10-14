# Architecture

Core components and deployment for the WTAI documentation site.

## Site components

- MkDocs core
- Material theme
- GitHub Pages deployment

## Mermaid diagram: High-level architecture

```mermaid
flowchart TB
subgraph Local
A[Markdown Files]
B[MkDocs]
end
A --> B --> C[Static Site]
C -->|Push| D[GitHub Repo]
D --> E[GitHub Actions]
E --> F[GitHub Pages]
```

## Mermaid diagram: Navigation structure

```mermaid
mindmap
  root((WTAI Docs))
    Home
    Getting Started
    Architecture
    Guides
```
