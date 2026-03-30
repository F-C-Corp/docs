# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

OpenFiskal API documentation site built with [Mintlify](https://mintlify.com). Pages are MDX files with YAML frontmatter. Configuration lives in `docs.json` (not `mint.json` — that's deprecated).

## Commands

```bash
npm i -g mint          # Install Mintlify CLI
mint dev               # Local preview at localhost:3000
mint broken-links      # Check for broken internal links
mint validate          # Validate docs build
mint a11y              # Accessibility check
```

Always run `mint broken-links` before committing changes.

## Architecture

- **`docs.json`** — Site config: two-tab navigation (Fiscalization API, Hosted Receipts API), theme, redirects, integrations
- **`*.mdx`** (root) — Guide pages (supported-scope, getting-started, auth, register-lifecycle, etc.)
- **`api-reference/openapi.yaml`** — Fiscalization API spec (v1.1.0). Mintlify auto-generates endpoint pages from this
- **`api-reference/hosted-receipts-openapi.yaml`** — Hosted Receipts API spec
- **`api-reference/schemas/*.mdx`** — Schema definition pages using `openapi-schema:` frontmatter field
- **`snippets/`** — Reusable MDX content
- **`images/`** — Logos and visual assets
- **`.mintignore`** — Excludes `drafts/` and `*.draft.mdx` from builds

Deployment is automatic on push to the default branch via the Mintlify GitHub app.

## Adding/Editing Pages

1. Every page needs `title` and `description` in YAML frontmatter
2. New pages must be added to the appropriate navigation group in `docs.json`
3. Internal links use root-relative paths without extensions (e.g., `/getting-started`)
4. All code blocks require language tags
5. API reference pages are auto-generated from OpenAPI specs; schema pages use `openapi-schema: SchemaName` frontmatter

## Writing Style

Per AGENTS.md and CONTRIBUTING.md:
- Active voice, second person ("you")
- Sentence case headings
- Bold for UI elements, code formatting for technical terms
- No marketing language ("powerful", "seamless", "robust")
- No decorative emoji
- One idea per sentence
