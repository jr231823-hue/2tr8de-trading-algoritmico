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
Date:             2026-07-17
Issue:            2TR-66
Change:           Remove the demonstrative contact form and replace it with a
                  disabled Taaffeíta CTA block (no fake destination).
Why:              The #contact section's form was explicitly marked as
                  demonstrative ("Este formulario es demostrativo...") and its
                  submit handler only showed a fake success message -- no data
                  was ever sent or received. Now that the site is live in
                  production on 2tr8de.com, keeping it live created a false
                  submission experience for real visitors. A bare `mailto:`
                  link was considered as an interim CTA target and explicitly
                  rejected before commit: it would open a blank-recipient mail
                  compose window, which is its own kind of false affordance.
                  A disabled button with honest "coming soon" copy was chosen
                  instead so the CTA never implies a working destination that
                  does not exist yet.
Files changed:    index.html
Changes:          Replaced the entire #contact section (title, disclaimer
                  paragraph, "Programa seleccionado" selector readout, and the
                  6-field <form id="diagnosticForm">) with a plain CTA block:
                  heading "¿Buscas acompañamiento privado 1-1?", the approved
                  Taaffeíta body copy, and a real, non-clickable
                  <button type="button" disabled aria-disabled="true"> reading
                  "Canal de solicitud próximamente" -- no mailto:, no href="#",
                  no invented destination of any kind. Removed the now-orphaned
                  JS: the [data-program] click handler that wrote into
                  #selectedProgram, and the #diagnosticForm submit handler
                  that faked a success state. Added one small additive CSS
                  rule, `.button:disabled` (+`:hover` override), reusing the
                  existing --panel2/--muted/--line design tokens so the
                  disabled state is visibly distinct (dimmed, muted colors,
                  not-allowed cursor, no hover lift) while keeping the same
                  size/shape/font-weight as every other .button on the page --
                  no new class, no new tokens. The #contact section id and
                  .contact-card grid layout are reused unchanged. Blueprint
                  ($899) and Diamond ($3,995) Stripe CTAs were not touched.
                  The Taaffeíta "Solicitar acceso" link elsewhere on the page
                  (href="#contact" data-program="Taaffeíta") still points at
                  #contact and still works as a plain anchor; its now-unused
                  data-program attribute was left in place (harmless, no
                  functional effect) rather than touching an unrelated line.
Testing:          grep confirmed zero remaining references to
                  diagnosticForm/selectedProgram/formStatus, any
                  "demostrativo"/"ningún dato" text, and no `mailto:` anywhere
                  in the file. Both Stripe links confirmed byte-for-byte
                  unchanged. Python HTMLParser tag-balance check: zero
                  unclosed/mismatched tags. Local static server smoke test run
                  twice (once per CTA iteration): HTTP 200, zero <form> tags
                  in the served output, final disabled-button text present
                  verbatim. Viewport meta tag and both responsive breakpoints
                  (max-width:1000px, max-width:700px) confirmed unchanged, so
                  desktop/mobile layout behavior for the rest of the page is
                  unaffected. git diff --check clean before commit.
Rollback:         git revert this commit restores the demonstrative form, its
                  JS handlers, and removes the .button:disabled rule exactly.
                  Not deployed as part of this change -- see Linear 2TR-66 for
                  current deployment status at the time this change ships.
Notes:            Commit created only after the diff was shown and approved.
                  Push and deploy remain separate, explicitly-approved steps
                  not taken here.
---
Date:             2026-07-17
Issue:            2TR-66
Change:           Push commit 00f0088 and deploy it to production
                  (2tr8de.com / www.2tr8de.com).
Why:              Approved to complete the production deployment block for
                  the disabled-CTA fix.
Files changed:    None (deployment/verification only; no code change).
Deployment:       git push origin main -- fast-forward 5b75ecf..00f0088,
                  confirmed via git ls-remote that origin/main now points at
                  00f00883a66b3de9d8d2315d84274bb45ee46f1f. Note: this GitHub
                  repository is bound to a Cloudflare Pages project in a
                  different Cloudflare account (the one that auto-deploys on
                  push); the project actually serving 2tr8de.com/www is a
                  direct-upload project in the correct account (the one
                  owning the 2tr8de.com zone) and does not auto-deploy from
                  GitHub. Deployed the same approved commit to that project
                  via `git archive 00f0088 | tar -x` + `wrangler pages
                  deploy`, specifying --commit-hash=00f00883a66b3de9d8d2315
                  d84274bb45ee46f1f to keep deployment metadata accurate.
Production verification: A ~10-15s edge-propagation delay was observed on
                  the 2tr8de.com custom domain immediately after deploy (the
                  new deployment was already live at its own *.pages.dev URL
                  and the project's default pages.dev alias instantly; the
                  custom domain briefly kept serving the prior deployment,
                  cf-cache-status: DYNAMIC once current). After that delay:
                  https://2tr8de.com -> HTTP 200, 86,834 bytes, zero <form>
                  tags, zero "mailto:", disabled button text exact ("Canal de
                  solicitud próximamente"), both Stripe links byte-for-byte
                  exact. https://www.2tr8de.com -> HTTP 200, identical
                  content and checks, unchanged behavior otherwise. Zoho MX
                  (mx.zoho.com/mx2/mx3), SPF, and the "zoho" DKIM selector
                  confirmed byte-for-byte unchanged. bc.2tr8de.com and
                  cf2mail.2tr8de.com CNAMEs confirmed unchanged. No DNS,
                  redirect rule, email record, or unrelated infrastructure
                  was touched by this deployment.
Rollback:         Code rollback: git revert 00f0088, then redeploy via the
                  same git archive + wrangler pages deploy path (or push and
                  wait for the other account's auto-deploy, then re-run the
                  manual deploy step here). Rollback commit target if needed:
                  5b75ecf (previous production state, includes the
                  demonstrative form). DNS/zone/email were not touched by
                  this deployment and require no rollback.
Notes:            Remaining blocker (unrelated to this fix): the Taaffeíta
                  1-to-1 application channel is still "próximamente" -- no
                  approved contact destination exists yet. Tracked in Linear
                  2TR-66, not blocking this deployment's own completion.
---
Date:             2026-07-17
Issue:            2TR-66
Change:           Connect the Taaffeíta evaluation-call CTA to a real TidyCal
                  booking link, replacing the disabled placeholder button.
Why:              An approved contact destination now exists
                  (https://tidycal.com/anibalcolon/taaffeita), resolving the
                  blocker flagged in the previous deployment entry. The
                  disabled "Canal de solicitud próximamente" button is no
                  longer accurate and should link directly to booking.
Files changed:    index.html
Changes:          In the #contact section: kept the heading "¿Buscas
                  acompañamiento privado 1-1?" unchanged. Replaced the body
                  paragraph with the approved copy, appending "Agenda una
                  llamada de evaluación para confirmar si existe buen encaje."
                  Replaced the disabled
                  <button type="button" disabled aria-disabled="true"> with
                  an active <a class="button"
                  href="https://tidycal.com/anibalcolon/taaffeita"
                  target="_blank" rel="noopener noreferrer">Solicitar
                  evaluación 1-1</a>. No other markup, CSS, or JS was
                  touched. The now-unused `.button:disabled` CSS rule (added
                  in the previous change) was intentionally left in place --
                  harmless dead code, costs nothing, and removing it was not
                  requested. Blueprint ($899) and Diamond ($3,995) Stripe
                  CTAs were not touched.
Testing:          grep confirmed exactly one occurrence of
                  href="https://tidycal.com/anibalcolon/taaffeita" with
                  target="_blank" and rel="noopener noreferrer" present on
                  the same element. Zero remaining occurrences of "Canal de
                  solicitud próximamente" or a `disabled` HTML attribute
                  (the one remaining "disabled" match in the file is the
                  pre-existing `.button:disabled` CSS rule, not an element).
                  Zero occurrences of `mailto:` and zero `<form` tags in the
                  file. Both Stripe links confirmed byte-for-byte unchanged.
                  Python HTMLParser tag-balance check: zero unclosed/
                  mismatched tags. Local static server smoke test: HTTP 200,
                  86,936 bytes, zero <form> tags in served output, new CTA
                  text "Solicitar evaluación 1-1" present verbatim. Viewport
                  meta tag and both responsive breakpoints (max-width:1000px,
                  max-width:700px) confirmed unchanged. `git diff --check`
                  clean before commit.
Rollback:         git revert this commit restores the disabled placeholder
                  button and prior body copy exactly. Not pushed or deployed
                  as part of this change -- see Linear 2TR-66 for current
                  deployment status at the time this change ships.
Notes:            Commit created locally only, after the diff was shown.
                  Push and deploy remain separate, explicitly-approved steps
                  not taken here.
---
