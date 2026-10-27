# partner-bootcamp-cert-host

**Public static host** for the Posit Partner Bootcamp **certification course** on
`partners.posit.co`. It serves one file:

- **`post-course-congrats.html`** — the completion "congrats" badge snippet that the course's
  **Wrap-up lesson** fetches client-side (cross-origin `fetch()` from `partners.posit.co`,
  which works because GitHub Pages sends `Access-Control-Allow-Origin: *` over HTTPS).

## Why this exists

The live partner theme (`posit-dev/partner-skilljar-theme` → `academy-partner.netlify.app`)
issues every partner course's LinkedIn credential as **"Posit Academy"** with no company logo
(`LINKEDIN_ORG_ID` is empty there, and it's an Academy-owned, domain-wide constant we don't
control). This repo hosts a **course-scoped fork** of that snippet with:

- `LINKEDIN_ORG_ID = '1978648'` — **Posit, PBC** (`urn:li:fsd_company:1978648`), so the
  LinkedIn credential shows the Posit company page + logo.
- `ISSUER_NAME = 'Posit, PBC'`, and the credential `name` is just the course title (the issuer
  is conveyed by the org id).

Only the certification course's Wrap-up lesson points its loader here, so this does **not**
affect any other partner course.

## Provenance

`post-course-congrats.html` is forked verbatim from
**`posit-dev/partner-skilljar-theme@51a5ca55`** (`post-course-congrats.html`), then edited only
for the LinkedIn issuer/org id (see the `FORK NOTE` comment in the file). If the upstream badge
markup changes, re-sync from that repo and re-apply the two-line config diff.

## Hosting

GitHub Pages, `main` branch, root. Served at
`https://sol-eng.github.io/partner-bootcamp-cert-host/post-course-congrats.html`.

Related: the certification course lives in `sol-eng/partner-bootcamp-certification`; the lab-ZIP
public host is `sol-eng/partner-bootcamp-skilljar-lab-host`.
