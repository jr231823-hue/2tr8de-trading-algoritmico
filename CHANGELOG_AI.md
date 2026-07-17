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
Date:             2026-07-17
Issue:            2TR-66
Change:           Pre-change DNS inventory and rollback values for 2tr8de.com
                  apex/www cutover from the retired Kajabi site to Cloudflare
                  Pages. Recorded read-only, before any DNS record was
                  modified, from the Cloudflare zone that actually owns
                  2tr8de.com (account jr231823@gmail.com, zone id
                  0ac4b8392a999ac4b05147ab33a6f897).
Why:              Approved to replace the retired Kajabi apex/www site with
                  the Cloudflare Pages deployment of this repository, while
                  preserving Zoho Mail (MX/SPF/DKIM) and the unrelated bc/
                  cf2mail subdomains completely untouched. These are the
                  exact values needed to roll back apex/www if ever required.
Rollback values (apex / www only -- MX, SPF, DKIM, bc, cf2mail untouched by
this block and reproduced here only as an unchanged-baseline reference):
                  - Apex A record: 104.18.42.139 (Cloudflare-proxied)
                  - Apex behavior before cutover: HTTP 301 redirect to
                    https://www.bc.2tr8de.com/
                  - www CNAME (before cutover): 2tr8de.mykajabi.com
                  - MX (unchanged by this block): 10 mx.zoho.com,
                    20 mx2.zoho.com, 50 mx3.zoho.com
                  - SPF/TXT apex (unchanged by this block):
                    "v=spf1 include:zohomail.com ~all"
                  - DKIM selector "zoho" (unchanged by this block, public key,
                    not a secret): "v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA
                    A4GNADCBiQKBgQCyKX0wVMUr00/26TQ4fr4j8VxEeLKR/BpzoFtevC8hy
                    GRtnXvACQ8uIJ3YW6slIvOl4LksS7KL3ffsyF+L2O1nv7Mh6uxGWcFKMK
                    ajCJZIpMGHnUoRHSc8h4Y1E0qKy9UNoKN63uRo0Dy9MzaNffnFfveBeIR
                    5b0FgpColyKuzZwIDAQAB"
                  - DMARC: no _dmarc record exists (pre-existing gap, not
                    introduced or fixed by this block)
                  - bc.2tr8de.com (untouched): CNAME to
                    us-east-shard-5.myclickfunnels.com
                  - cf2mail.2tr8de.com (untouched): CNAME to
                    mailer.myclickfunnels.com, plus its own SPF/Yahoo
                    verification TXT records
Rollback:         To restore the retired Kajabi site exactly: set the apex A
                  record back to 104.18.42.139 (or restore whatever routing
                  produces the same 301 to https://www.bc.2tr8de.com/), and
                  set www.2tr8de.com's CNAME back to 2tr8de.mykajabi.com. No
                  MX/SPF/DKIM change is ever part of this rollback since none
                  were modified.
Notes:            Cloudflare Pages custom-domain attachment for this zone
                  requires one manual DNS record add/edit per domain via the
                  dashboard -- the Wrangler OAuth session used for this work
                  only grants zone:read, not dns_records:edit, confirmed by
                  repeated 403 "Authentication error" responses from the
                  Cloudflare DNS API. See Linear 2TR-66 for the exact record
                  values requested for the apex/www cutover.
---
