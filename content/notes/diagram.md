---
publish: true
title: Mermaid diagram
tags:
  - sample
  - diagram
---

# Mermaid diagram

The `mermaid` plugin turns a fenced `mermaid` block into a diagram.

```mermaid
flowchart LR
  A[Markdown in content/] --> B[Riebeckite build]
  B --> C[dist/]
  C --> D[Cloudflare Workers]
  D --> E[integrated.riebeckite.dev]
```

## Why this page exists

It checks that a plugin added on top of the starter preset works in the published site, not only in local development.

Return to [[welcome]].
