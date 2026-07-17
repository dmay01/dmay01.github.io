# Copilot Coding Agent Instructions (v1.x)

## Repository Role

This repository is Daniel May's personal website, built as a thin site on the pluginized al-folio v1 architecture.

This repo owns site configuration, content, data, and explicitly acknowledged site overrides.

## Ownership Boundaries

Follow `docs/BOUNDARIES.md`.

- This site owns:
  - `Gemfile`, `_config.yml`
  - site content (`_pages`, `_projects`, `_news`, `_teachings`, `_bibliography`, `_data`)
  - acknowledged overrides listed in `.al-folio-overrides.yml`
- Plugin repos own:
  - runtime/component logic
  - component correctness/unit tests
  - feature-specific assets

Do not reintroduce plugin-owned runtime assets into starter paths unless intentionally overriding behavior.

## Plugin Naming and Featuring

- Theme-coupled plugins: repo `al-folio-<feature>`, gem/plugin id `al_folio_<feature>`.
- Reusable plugins: repo `al-<feature>` (or neutral), gem/plugin id aligned to namespace.
- Featured plugin metadata lives in `_data/featured_plugins.yml`.
- Featuring and bundling are separate decisions.

## Core Stack

- Jekyll (Ruby)
- Node tooling only (Prettier)
- No starter-local Tailwind build pipeline

## High-Signal Paths

- `_config.yml` - starter plugin wiring and feature flags
- `.al-folio-overrides.yml` - reviewed local runtime overrides and upstream checksums
- `.github/workflows/` - CI workflows
- `docs/` - user, maintainer, upgrade, and plugin-system documentation
- `.agents/skills/al-folio-bootstrap/SKILL.md` - canonical agent workflow for new site setup
- `.agents/skills/al-folio-v1-migration/SKILL.md` - canonical agent workflow for customized fork migration
- `.codex/skills` - symlink to `.agents/skills`

## Validated Commands

```bash
npm ci
npm run lint:prettier
JEKYLL_ENV=production bundle exec jekyll build
bundle exec al-folio upgrade audit --no-fail
bundle exec al-folio upgrade overrides audit
bundle exec al-folio upgrade report
docker compose up -d
curl -fsS http://127.0.0.1:8080/ >/dev/null
docker compose logs --tail=80
docker compose down
```

## CI Expectations

Keep these workflows aligned when changing site behavior:

- `upgrade-check.yml`
- `deploy.yml`
- `broken-links.yml`
- `broken-links-site.yml`

## Editing Guidance

- Prefer site wiring/content/data changes in this repo.
- Route runtime/layout/feature fixes to owning plugin repos.
- Keep all contributor guidance consistent with v1 ownership boundaries.
- When a site keeps local overrides of plugin-owned files, run `bundle exec al-folio upgrade overrides audit` and update `.al-folio-overrides.yml` after reviewing diffs.
