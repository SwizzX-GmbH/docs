# Qint developer documentation

Developer docs for [Qint](https://qint.ch) — built with [Mintlify](https://mintlify.com) (`docs.json` format). Live at **docs.qint.ch**.

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

## Publishing to docs.qint.ch

This repository is the **only** source of docs.qint.ch. Mintlify builds the
`main` branch on every push (the "Mintlify Deployment" check on the commit shows
the result), so merging to `main` is publishing. There is no second copy to keep
in sync: the earlier private `SwizzX-GmbH/qint-docs` mirror was archived on
2026-10-08 after its content was folded in here.

Before merging a change, run `mint dev` locally (see above) and check the page
renders. Custom domain and the GitHub connection are configured in the Mintlify
dashboard (deployment `qint-docs`); nothing in this repo needs to change for a
new page to go live.

The internal system overview lives in
[the qint-api repository](https://github.com/SwizzX-GmbH/qint-api/blob/main/docs/README.md).
Do not copy internal operational details or credentials into these public docs.
