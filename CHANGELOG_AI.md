# CHANGELOG_AI.md - 2TR8DE Trading Algoritmico

AI/developer-readable changelog for the public static marketing site.

---
Date:             2026-07-17
Issue:            2TR-66
Change:           prepare public static landing-page repository locally
Why:              Prepare the approved 2TR8DE trading-algorithmic marketing
                  landing page for publication as a separate public GitHub
                  repository and Cloudflare Pages Free static site, keeping the
                  private Hub repository and hub.2tr8de.world unchanged.
Files changed:    index.html, README.md, CHANGELOG_AI.md, _headers
Testing:          Local static server at http://localhost:8750/ returned
                  HTTP 200 text/html, 88,303 bytes from index.html. HTML parser
                  check found zero unmatched closing tags and zero unclosed
                  tags. Expected sections present: diagnostic, method, routes,
                  programs, ecosystem, about, FAQ, contact. Embedded Anibal
                  portrait loads as a data-image. Blueprint checkout confirmed:
                  $899 and https://buy.stripe.com/5kQfZg23wfsE3vQ4f1eEo1L.
                  Diamond checkout confirmed: $3,995 and
                  https://buy.stripe.com/aFa4gy4bEeoA4zUcLxeEo1M. Taaffeita
                  remains application-only via #contact/data-program and no
                  Stripe checkout. Reveal classes are visible by default
                  without JavaScript. Browser responsive checks at 1440x1000
                  and 390x844 found all sections present, portrait loaded, key
                  CTA links present, and no top-level horizontal scrolling
                  (mobile comparison table uses its own intended internal
                  horizontal scroll). Final approved wording verified in the
                  two requested public-facing locations: header/hero eyebrow is
                  "TRADING ALGORÍTMICO · QUANT RESEARCH" in visible Spanish
                  copy, and the main hero introduction paragraph reads
                  "Aprende a investigar, construir, validar y organizar
                  sistemas de trading algorítmico con una metodología
                  estructurada, herramientas privadas y acompañamiento real."
                  with no "con StrategyQuant X" phrase. Other StrategyQuant
                  references elsewhere on the page were intentionally preserved.
                  Basic secret scan found no keys/tokens in index.html. git
                  diff --check clean after intent-to-add.
Rollback:         Delete the local workspace before publication. After
                  publication, revert the Git commit and let Cloudflare Pages
                  redeploy the previous static version.
Notes:            Source ZIP:
                  /Users/anibalcolon/Downloads/ai-services-preview-updated(5).zip
                  containing ai-services-preview.html only. The approved page is
                  copied as index.html for root static hosting. No Hub files,
                  private assets, environment files, secrets, or infrastructure
                  configuration are included.
---
