# 2TR8DE Trading Algoritmico

Public static marketing site for the 2TR8DE trading-algorithmic offer.

## Scope

- Static-only website.
- Hosted on Cloudflare Pages Free.
- No environment variables.
- No secrets.
- No Hub assets or private Hub pages.
- No authentication, Supabase, workers, schemas, or private infrastructure.

## Source

Approved source package:

`/Users/anibalcolon/Downloads/ai-services-preview-updated(5).zip`

The package contains one approved page:

`ai-services-preview.html`

It is published as:

`index.html`

## Cloudflare Pages

Recommended settings:

- Framework preset: None / Static HTML
- Build command: none
- Build output directory: `/`
- Production branch: `main`
- Environment variables: none

## Rollback

Before first publish, rollback is simply deleting this local workspace.

After publish, rollback options:

1. Revert the GitHub commit that introduced the published change.
2. Push the revert to `main`.
3. Let Cloudflare Pages deploy the reverted static site.
