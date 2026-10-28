<p align="center">
  <img src=".github/logo.svg" alt="Ambrogio" width="160">
</p>

# Ambrogio — website

**Ambrogio**: talk to it like Alexa, chat with it like ChatGPT — one self-hosted AI assistant for your whole homelab. Multi-agent by design: each agent you configure handles one job, such as the house, music, weather or your documents, using the services you already host.

This repository holds the website of Ambrogio, a single page with what Ambrogio does and links to the [documentation](https://ambrogio-app.github.io/ambrogio-docs/) and the repositories. It is built with [Astro](https://astro.build/) and published at <https://ambrogio-app.github.io/>.

## Commands

```bash
npm ci
npm run dev       # local preview at http://localhost:4321
npm run typecheck # astro check
npm run build     # static site in dist/
```

## Third-party logos

The homelab diagram (`src/components/Homelab.astro`) shows the logos of the services used by [`ambrogio-homelab-example`](https://github.com/ambrogio-app/ambrogio-homelab-example). They are trademarks of their owners, used only to name those services, and live in `src/assets/services/`:

| File | Source |
|---|---|
| `home-assistant.svg` | [Simple Icons](https://simpleicons.org/) 16.36.0, from the [Home Assistant assets](https://github.com/home-assistant/assets); brand guidelines at <https://design.home-assistant.io/#brand/logo> |
| `music-assistant.svg` | `public/favicon.svg` of [music-assistant/frontend](https://github.com/music-assistant/frontend) |
| `opencloud.svg` | `services/web/assets/themes/opencloud/assets/favicon.svg` of [opencloud-eu/opencloud](https://github.com/opencloud-eu/opencloud) |
| `open-meteo.png` | `static/apple-touch-icon.png` of [open-meteo/open-meteo-website](https://github.com/open-meteo/open-meteo-website) |

The icons in `src/assets/icons/` (GitHub, Open Source Initiative, Android, Apple) come from [Simple Icons](https://simpleicons.org/) 16.36.0 and are trademarks of their owners as well.

## Publishing

Every push to `main` runs the CI and the secret scan, then `.github/workflows/pages.yml` publishes `dist/` on GitHub Pages.

## Secret scanning

Every push and pull request runs [gitleaks](https://github.com/gitleaks/gitleaks) 8.30.1 over the whole history (`.github/workflows/secret-scan.yml`). Locally, a pre-commit hook blocks commits that add secrets. Install gitleaks 8.30.1 and enable the hook once per clone:

```bash
git config core.hooksPath .githooks
```

## License

[MIT](LICENSE), except the third-party logos and icons listed above, which belong to their owners.
