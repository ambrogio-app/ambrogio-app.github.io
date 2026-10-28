# Instructions for agents

This repository contains only the website of Ambrogio: a single Astro page published at the root of the organisation's GitHub Pages domain, <https://ambrogio-app.github.io/>. It has no Reqvire model. The rules common to all repositories are in `ambrogio-model/AGENTS.md`.

## Content

- The page says what Ambrogio is and what it does, and links to the documentation and the repositories. Instructions, configuration, limits and versions belong to `ambrogio-docs`: link to its pages instead of repeating them.
- Every statement about the product must match the documentation in `ambrogio-docs`, which derives from the model and the code. When a feature described here changes, update this page in the same work.
- Describe Ambrogio with the standard definition: "Talk to it like Alexa, chat with it like ChatGPT — one self-hosted AI assistant for your whole homelab." When more is needed: "Multi-agent by design: each agent you configure handles one job, such as the house, music, weather or your documents, using the services you already host." Do not call it a "home assistant".
- English, plain words, no marketing tone, no emoji, no data of a specific installation.
- The homelab diagram (`src/components/Homelab.astro`) shows the services of `ambrogio-homelab-example`: services in the home inside the homelab box, the LLM (which can be a cloud provider) and the public web search outside it. When the example changes its services, update the diagram. The Android and iOS app is not part of the product yet: the diagram marks it as soon, with a dashed outline, and the page says nothing more about it until it exists. The icons in `src/assets/icons/` (GitHub, Open Source Initiative, Android, Apple) come from Simple Icons 16.36.0. Third-party logos come from their owners' official sources or from Simple Icons in the brand colour it records, listed in README.md, and are not otherwise altered.
- The page uses no external fonts, scripts or trackers.

## Brand

`src/brand/`, `public/favicon.svg` and the logos in `.github/` are copies from the private repository `ambrogio-brand`, made by its `scripts/sync`: do not edit them here. The page uses the brand's tokens (`--ambrogio-*`), the Nunito typeface and the logo from `src/brand/`, and has only a light theme.

## Demo video

`public/video/ambrogio-demo.mp4` and its poster `ambrogio-demo.jpg` come from `build/ambrogio-demo.mp4` of the private repository `ambrogio-video`, reduced for the web. When the video changes there, regenerate both from the workspace folder:

```bash
V=ambrogio-video/build/ambrogio-demo.mp4; O=ambrogio-app.github.io/public/video
ffmpeg -i $V -vf scale=1280:-2 -c:v libx264 -preset slow -crf 26 -pix_fmt yuv420p -c:a aac -b:a 128k -movflags +faststart $O/ambrogio-demo.mp4
ffmpeg -ss 43.8 -i $V -frames:v 1 -vf scale=1280:-2 -q:v 3 $O/ambrogio-demo.jpg
```

## Publishing and checks

`main` accepts changes only through a pull request whose CI and secret scan pass. On every push to `main`, `.github/workflows/pages.yml` publishes the site after the CI and the secret scan.

```bash
npm run typecheck
npm run build
```

Enable the pre-commit hook with `git config core.hooksPath .githooks`; gitleaks 8.30.1 must be on `PATH`.
