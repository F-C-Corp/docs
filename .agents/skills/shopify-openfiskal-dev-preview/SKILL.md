---
name: shopify-openfiskal-dev-preview
description: Start and operate the OpenFiskal Shopify app in development mode for feature preview testing. Use when Codex needs to run `yarn dev -c <shopify-config> --store <store-domain>` for the OpenFiskal app, keep the dev process alive in a PTY session, and open the Shopify Admin app page (for example `https://admin.shopify.com/store/ofi-dev-shop-felix-it/apps/openfiskal-dev-felix`) to verify new features.
---

# Shopify OpenFiskal Dev Preview

Run the standard local dev-preview workflow for the OpenFiskal Shopify app and open the target store admin app page for testing.

## Defaults

- Shopify config file: `shopify.app.open-fiskal-dev-felix.toml`
- Store slug/domain: `ofi-dev-shop-felix-it` / `ofi-dev-shop-felix-it.myshopify.com`
- Admin app URL: `https://admin.shopify.com/store/ofi-dev-shop-felix-it/apps/openfiskal-dev-felix`

If the user provides different values, use their values.

## Workflow

1. Confirm the command inputs (config file and store).
2. Start a PTY terminal session in the Shopify app repository.
3. Run:
   `yarn dev -c shopify.app.open-fiskal-dev-felix.toml --store ofi-dev-shop-felix-it.myshopify.com`
4. Wait until the dev server reports it is ready (or is clearly waiting on auth/setup).
5. Open the Shopify admin app URL in the browser:
   `https://admin.shopify.com/store/ofi-dev-shop-felix-it/apps/openfiskal-dev-felix`
6. Keep the dev process running while testing.
7. Report status clearly: dev server state, opened URL, and any blocker.

## Operating rules

- Always run `yarn dev` in a PTY so interactive prompts can be handled.
- Do not terminate the dev process unless the user asks.
- If login/device auth is required, pause and ask the user to complete authentication.
- If the app URL redirects to install/auth screens, report that and continue only after user confirmation.
- If the configured app handle differs from `openfiskal-dev-felix`, derive the app URL from the user-provided handle.

## Quick override template

Use this command when the user gives custom values:

`yarn dev -c <shopify-config.toml> --store <store>.myshopify.com`

Use this URL pattern for custom values:

`https://admin.shopify.com/store/<store-slug>/apps/<app-handle>`
