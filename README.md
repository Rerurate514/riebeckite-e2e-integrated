# Riebeckite E2E: integrated layout

A public, continuously deployed Riebeckite sample where the content, the site, and the deployment configuration live in one repository.

- **Published site:** <https://integrated.riebeckite.dev>
- **Riebeckite documentation:** <https://riebeckite.dev>
- **Other samples:** [separate directories](https://directories.riebeckite.dev) · [separate repositories](https://repositories.riebeckite.dev)

## Purpose

This repository shows the simplest Riebeckite layout. It is the layout to start with when one team owns both the Markdown and the site code. The build reads content from `content/` in this checkout, so there is no second repository to configure.

## Directory structure

```text
.
├── content/                   Markdown, images, and attachments
│   ├── index.md
│   ├── notes/
│   └── assets/
├── app/                       Riebeckite/HonoX site code
├── public/                    Static files served as-is
├── riebeckite.config.ts       Site settings and plugins
├── wrangler.jsonc             Cloudflare Worker and custom domain
├── package.json
└── .github/workflows/
    └── publish.yml            Build and deploy on push to main
```

## Requirements

- Node.js 22 or newer
- npm
- A Cloudflare account with a `riebeckite.dev` zone

## Setup

```sh
git clone https://github.com/Rerurate514/riebeckite-e2e-integrated.git
cd riebeckite-e2e-integrated
npm ci
```

Riebeckite is installed from npm as `@riebeckite/*` packages. This repository does not link to a local Riebeckite checkout, so it verifies the published package experience.

## Local development

```sh
npm exec riebeckite check
npm exec riebeckite dev
```

Open the URL printed by the dev server (usually <http://localhost:5173>). Edit a file in `content/` and the page reloads.

Useful commands:

```sh
npm exec riebeckite doctor    # diagnose content, assets, and configuration
npm exec riebeckite build     # production build into dist/
npm exec riebeckite inspect   # inspect configuration, plugins, and content
```

## Build

```sh
npm run build
```

The static output is written to `dist/`. The build fails if the configuration or content graph is invalid.

## Deploy

The Worker is named `riebeckite-e2e-integrated` and is attached to the custom domain `integrated.riebeckite.dev` by `wrangler.jsonc`.

Manual deploy:

```sh
npx wrangler login
npx wrangler deploy
```

The first deploy creates the Worker and the custom domain. No separate DNS record is needed; Cloudflare creates the record for the custom domain.

## GitHub Actions

`.github/workflows/publish.yml` runs on every push to `main` and on manual dispatch. It:

1. checks out the repository and verifies the run is for the current `main`;
2. installs dependencies with `npm ci`;
3. restores build caches and publication state;
4. runs `riebeckite check`, `riebeckite build`, `riebeckite publish validate`, and the publication gate;
5. deploys with `cloudflare/wrangler-action`;
6. records the publication state on the `publication-state` branch.

Required repository credentials:

| Name | Kind | Purpose |
| --- | --- | --- |
| `CLOUDFLARE_API_TOKEN` | Secret | Workers Scripts:Edit for the account |
| `CLOUDFLARE_ACCOUNT_ID` | Variable | Cloudflare account ID |

Set them in **Settings → Secrets and variables → Actions**. `riebeckite deploy setup` can also register them when the GitHub CLI is installed.

## Content in this sample

`content/index.md` explains the layout. `content/notes/` demonstrates frontmatter, tags, WikiLinks, backlinks, Markdown links, tables, code, Mermaid, and images. `content/assets/` holds the source image. `public/assets/` holds the downloadable text attachment.

## Related documentation

- [Quick Start](https://riebeckite.dev/getting-started/quick-start)
- [Project structure](https://riebeckite.dev/getting-started/project-structure)
- [Integrated setup](https://riebeckite.dev/getting-started/integrated-setup)
- [Cloudflare Workers deployment](https://riebeckite.dev/guides/deployment/cloudflare-workers)
- [GitHub Actions deployment](https://riebeckite.dev/guides/deployment/github-actions)

## License

Apache License 2.0. See [LICENSE](LICENSE).
