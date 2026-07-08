# Qint developer documentation

Developer docs for [Qint](https://qint.ch) — built with [Mintlify](https://mintlify.com) (`docs.json` format). Will live at **docs.qint.ch**.

## Local preview

```bash
npx mint@latest dev
```

Opens a live-reloading preview at http://localhost:3000. Useful extras:

```bash
npx mint@latest broken-links        # check every internal link resolves
npx mint@latest openapi-check openapi.yaml   # validate the OpenAPI spec
```

(Requires Node 20+. The first run downloads the Mintlify preview bundle.)

## Layout

```
docs.json           Mintlify config: branding, colors, navigation tabs
openapi.yaml        OpenAPI 3.1 spec for the merchant API (renders the API Reference tab)
*.mdx               Getting-started pages
accept-payments/    Payment links, invoices, API payments, assets & networks
webhooks/           Overview, signature verification, events, delivery & retries
guides/             WooCommerce, underpayments, payouts, going-live checklist
api-reference/      API intro + one page per endpoint (wired to openapi.yaml)
logo/, favicon.svg  Brand assets (light + dark logos)
```

Editing content = editing the `.mdx` files. Adding a page = create the `.mdx` file **and** list it in `docs.json` under `navigation`. Changing an endpoint = edit `openapi.yaml` (the endpoint pages under `api-reference/` pick it up automatically).

## Publishing to docs.qint.ch (one-time setup, ~10 minutes)

1. **Sign up at [mintlify.com](https://mintlify.com)** (Start for free) using the
   SwizzX GmbH GitHub account, which creates your Mintlify dashboard at
   `dashboard.mintlify.com`.

2. **Connect the GitHub repo.** Push this folder to
   `SwizzX-GmbH/qint-docs`, then in the Mintlify dashboard install the
   **Mintlify GitHub App** and grant it access to that repository
   (Dashboard → Settings → GitHub App, or the prompt during onboarding).
   Every push to the default branch now auto-deploys the docs.

3. **Add the custom domain.** Dashboard → Settings → Domain Setup → enter
   `docs.qint.ch`. Mintlify shows you a **CNAME target** — add that CNAME
   record for the `docs` subdomain at qint.ch's DNS provider. Once DNS
   propagates, Mintlify provisions TLS automatically and
   https://docs.qint.ch is live.

Until step 3 completes, the docs are reachable at the `*.mintlify.app`
subdomain assigned in the dashboard.
