# DevArt Forms — Current State

## Development Source

Current manifest version:

`1.1.0`

The source contains:

- Package `pkg_devartforms`
- Component `com_devartforms`
- Task plugin `plg_task_devartforms`
- Extension plugin `plg_extension_devartforms` (Options params merge)
- Content plugin `plg_content_devartforms` (`{devartform id="N"}`)
- Site module `mod_devartforms`
- Per-form Mailchimp (enable + HTTPS list-manage URL, browser-side opt-in forward)

## Implemented Source

The current source includes:

- Administrator dashboard, forms, form editing, and submissions views
- Frontend rendering through menu items, module, and shortcode
- Service→Storage submission pipeline with one-time submission keys
- Optional independent PoW, reCAPTCHA v2, and Turnstile mechanisms
- Cloudflare-aware client IP resolution and independent rate limiting
- Configurable database storage and scheduled retention purge
- Immediate mail by default, optional queued mail via scheduled task
- Streaming CSV export and light submissions list
- Granular submissions ACL (`view` / `export` / `delete`)
- Per-form Access view level for frontend visibility/submit
- Full language packs for component, module, and content plugin (15 locales;
  machine-generated packs marked for review)

## Repository Tooling

- Validation and build tooling follows the package manifest rather than a
  product-specific configuration.
- The package manifest declares `com_devartforms`, `plg_task_devartforms`,
  `plg_extension_devartforms`, `plg_content_devartforms`, and `mod_devartforms`.
- Build output belongs under `builds/` and must never overwrite an existing
  build.
- The manifests require PHP 8.3.0 or newer.

## Verification Status

`1.1.0` was validated, built, installed on local Herd sites (`demo3` and
`joomla6_tests`), exercised with DevArt QA harness (`qa:component` + curated
Forms Cypress), and confirmed on the VPS (including admin header transparency
and audit follow-up). Verified artifact SHA-256:
`1787bccfb867c95472f573107105322e8cec6a2760b29e2aea5cdbd5ad1fc6a3`.
Public GitHub release / `update.xml` for `1.1.0` remain pending operator request.
Previous public release remains `v1.0.10`.
