---
publish: true
title: Home
tags:
  - sample
---

# Riebeckite sample: integrated layout

This is the **integrated** sample. Content, site code, and deployment configuration live in one repository: [Rerurate514/riebeckite-e2e-integrated](https://github.com/Rerurate514/riebeckite-e2e-integrated).

- Content: `content/`
- Site code: `app/` and `riebeckite.config.ts`
- Deployment: `wrangler.jsonc` and `.github/workflows/publish.yml`
- Published site: <https://integrated.riebeckite.dev>

## How this layout works

The Riebeckite project is the repository root. `content.directory` points at `content/`, so the same checkout that builds the site also holds the Markdown. Pushing a content change to `main` runs the GitHub Actions workflow, which builds and deploys to Cloudflare Workers.

## Start here

- [[welcome]] — frontmatter, tags, WikiLinks, and backlinks
- [[japanese]] — Japanese content and internal links
- [[markdown]] — Markdown links, tables, and code
- [[diagram]] — a Mermaid diagram
- [[attachments]] — images and a downloadable attachment

## Compare the other layouts

- [Separate directories sample](https://directories.riebeckite.dev)
- [Separate repositories sample](https://repositories.riebeckite.dev)

## Riebeckite documentation

- [Quick Start](https://riebeckite.dev/getting-started/quick-start)
- [Content location](https://riebeckite.dev/guides/content-repositories/basics)
