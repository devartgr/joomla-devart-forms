# Changelog

## 1.1.0 — 2026-10-31

Public release after 1.0.10. Intermediate local builds (including unpublished
1.0.11 / 1.0.12 checkpoints and pre-release 1.1.0 polish) are folded into this
version; they were never published separately.

### Added
- Per-form Mailchimp integration (Integrations tab): enable checkbox + classic
  `list-manage.com/subscribe/post` URL (no Marketing API); disable without
  clearing the URL
- Optional newsletter opt-in under GDPR consent; choice stored in submissions
  and `{all_fields}`, with list unsubscribe URL when opted in
- Browser-side Mailchimp forward after successful submit (Mailchimp blocks
  server-side classic POSTs with bot/captcha protection)
- `mod_devartforms` site module and `plg_content_devartforms` shortcode
  `{devartform id="123"}` for embedding forms outside menu items
- Module param `show_empty_message` switcher when no form is selected
- Full language packs for module and content plugin across the 15 shipped locales
  (machine-generated packs remain open to review)

### Fixed
- Form edit admin UI respects Joomla dark mode
- Form editor language list uses installed Joomla content/site languages
  (was hardcoded to en-GB / el-GR only)
- Module/shortcode embeds load `com_devartforms` language files before render
- Duplicate form instances on one page use unique DOM `id`/`for` suffixes
- General «Translation languages» field lists real editor languages (not
  hardcoded `en-GB, el-GR`); Display tab lang notice defaults to `en-GB`
- Rate limit defaults to enabled when the setting key is absent (matches UI)
- Legacy `consent` fields stored as `type=text` validate as consent
- Mailchimp subscribe URLs require HTTPS Mailchimp/list-manage hosts; invalid
  URLs warn and leave integration disabled; forward name truncated to 100 chars
- Mailchimp consent scan uses coerced validation types (legacy consent aligned)
- Dark mode readability for Security tab `.bg-light` / `.alert-light` cards
- Security challenge failures log a WARNING without changing visitor JSON
- Admin Forms/Submissions/Dashboard header images: no box shadow / radius frame
  (transparent like other DevArt admin headers)
- Task and extension plugin providers use current `CMSPlugin` config-only
  constructor (Joomla 7-ready; matches content plugin)
- Content shortcode plugin auto-enable on fresh install only (survives intentional disable on update)
- Missing NEWSLETTER / embed language keys filled across shipped locales

### Notes
- Safe update from DevArt Forms 1.0.10
- Requires Joomla 6.0+ and PHP 8.3.0+
- Install or update using the full `pkg_devartforms` package only
- Existing forms, submissions and settings are preserved
- Package: `com_devartforms`, `plg_task_devartforms`, `plg_extension_devartforms`,
  `plg_content_devartforms`, `mod_devartforms`
- Verified SHA-256:
  `1787bccfb867c95472f573107105322e8cec6a2760b29e2aea5cdbd5ad1fc6a3`

## 1.0.10 — 2026-10-23

### Fixed
- Component install/update no longer shows a yellow warning when flattening
  already-flat (or empty-shell) component params; quiet Log::INFO only when a
  real rewrite happens
- Dashboard “Missing keys” / Cloudflare proxy notice after Options save:
  `plg_extension_devartforms` merges Options into existing params (preserves
  secrets + scheduler markers); empty password submits keep stored secrets;
  `ComponentParams` reads nested fieldset fallbacks; secret fields no longer use
  `lock="true"` (which always showed dots even when no secret was stored)

## 1.0.9 — 2026-10-05

Quality release: Cloudflare-safe IP/rate limiting, scheduled retention, scalable
admin data handling, server idempotency, validation hardening, Service→Storage
pipeline, i18n, granular submissions ACL, optional mail queue, and Forms Trash.

### Hardening Round 2 (same 1.0.9 pre-release)
- PoW challenge HMAC binds `submission_key` (one solved PoW → one submission)
- Duplicate key retries return the form success message
- Orphan retention uses select-ids + delete-by-ids (MySQL-safe)
- Mail queue recovers stale `processing` after 15 minutes; purges aged PII rows
- Submission/form delete cascades mail-queue rows; `idx_submission` index
- CSV export passes `fputcsv` escape arg; adds `Other` column for retired fields
- Site JS keeps key/PoW on ambiguous network failure (30 s timeout)
- Drop per-submit `SHOW COLUMNS`; UTC `created` via `Factory::getDate()->toSql()`
- Nested component params normalised flat; `keep_data_on_uninstall` option
- Cloudflare dashboard notice when mode is `none`; Retry Mail ACL aligned with view
- Captcha verifier uses CMS `HttpFactory` + `Uri` host comparison
- Note: rows created by earlier 1.0.9 builds used DB-session `NOW()` for `created`

### Leftovers (same 1.0.9 pre-release)
- Cloudflare IP ranges: built-in baseline + cached refresh via purge /
  `devartforms.cloudflare_ips` task (fail-closed on fetch errors)
- Optional `fastcgi_finish_request` flush before immediate SMTP send
- Form edit screen CSS/JS moved to `media/com_devartforms/{css,js}/form-edit.*`
- Site DI provider wires core services by constructor (static `::create()` remains for controllers/tasks)
- `phpstan.neon` level 6 added for source analysis
- i18n gaps filled across shipped locales
- Form edit exposes Access view level (frontend who can view/submit); per-form
  admin ACL asset matrix was removed as unnecessary complexity

### Hardening Round 3 (same 1.0.9 pre-release)
- JSON responses call `sendHeaders()` and set `X-Content-Type-Options: nosniff`
- Submission keys claim as `processing` then `completed` (busy ≠ false success)
- Preview search reverts to LIKE; drops short-lived FULLTEXT `ft_preview`
- Cloudflare CIDR sanity filters, atomic cache write, admin CIDR filter, status
- Retention key/rate-limit/mailqueue purge uses bounded batch loops
- Immediate mail under FPM persists outbox rows before flush; recover via mailqueue
- Dashboard scheduler health; plugin installer seeds purge/mailqueue/CF tasks

### Hardening Round 4 (same 1.0.9 pre-release)
- Mailqueue task seeds/migrates to every 5 minutes (`PT5M`); purge daily; CF weekly
- Task seed markers: deleted admin tasks are not recreated; CF task starts disabled unless proxy mode is Cloudflare
- Package uninstall honours `keep_data_on_uninstall` (read in preflight)
- Stale `processing` submission keys (>300s) can be taken over; duplicate store recovers success without a second mail
- Submit path no longer runs `SHOW COLUMNS` for `keys.status`

### Forms Trash
- Soft-delete forms with `published = -2` (Trash toolbar) instead of immediate hard delete
- Status filter: Published & Unpublished / Published / Unpublished / Trashed
- Permanent delete only from Trash; cascades related submissions with warning
- Publish/Unpublish restores a trashed form

### Added
- `ClientIpResolver` with optional Cloudflare trusted-proxy mode and HMAC IP/UA hashing
- Independent `#__devartforms_ratelimit` table (works with storage off)
- Scheduled task plugin `plg_task_devartforms` with `devartforms.purge` and `devartforms.mailqueue`
- Stateless HMAC Proof of Work via `ChallengeService` (no PoW session writes)
- One-time `#__devartforms_keys` submission keys for duplicate-submit protection
- Optional `submission_key` and `mail_status` columns on submissions
- Streaming keyset CSV export and light submissions list with lazy JSON detail view
- Form delete cascades submissions in batches
- Site Service→Storage pipeline (`SubmissionService`, `FormValidator`, `CaptchaVerifier`, `SubmissionStorage`, `NotificationService`, …)
- Granular ACL: `devartforms.submissions.view|export|delete`
- Optional queued mail delivery (`mail_delivery=queued`, default remains `immediate`)
- Admin Retry Mail action and mail status column

### Changed
- HTML field/header/footer sanitizer uses Joomla `InputFilter` whitelist
- Option fields whitelist submitted values; consent/checkbox accept only `1`
- Privacy metadata storage options are hash/none only (no full IP/UA)
- Site runtime strings use `Text::_` / `Text::script` (en-GB + el-GR)
- Package composition is `com_devartforms` + `plg_task_devartforms`

### Security
- CSV export requires `devartforms.submissions.export` or `core.admin` by default (not general managers)
- Captcha verification uses HTTP factory with resolved client IP as `remoteip`

### Notes
- Install/update seeds Scheduled Tasks once (purge daily, mailqueue every 5 minutes,
  Cloudflare IP refresh weekly when Trusted Proxy Mode is Cloudflare)
- Drive Joomla Scheduler via Lazy Scheduler or `php cli/joomla.php scheduler:run`
- Keep Data On Uninstall applies to package and component uninstall
- Captcha component keys from 1.0.8 continue to work
- Verified package SHA-256:
  `a6feff442d62112ccea083c286a39df318ef66627f14b98ef7857fc50e297e2d`

## 1.0.8 — 2026-09-28

Site router MenuItem `$client_id` warning fix.

### Fixed
- Site router no longer filters menu items with `client_id` (undefined on `MenuItem`), matching the SiteMenu-only component lookup used across other DevArt packages

## 1.0.7 — 2026-09-24


Joomla 7 forward compatibility, multilingual consent Privacy URL, and SEF form routing.

### Added
- Site RouterView for clean menu / SEF form URLs without frontend `?view=form&id=`
- Consent / GDPR Privacy / Terms URL editable per language
- Schema compatibility marker for 1.0.7

### Changed
- Application input access uses `getInput()` instead of the deprecated `$app->input` property
- Mail sending uses `MailerFactoryInterface` instead of `Factory::getMailer()`
- Frontend form assets load through WebAssetManager
- Administrator list/edit templates avoid deprecated `behavior.*`, `grid.*`, `bootstrap.tab` and `HTMLHelper::form.token` helpers

### Fixed
- Form view no longer falls back to form id `1` when no menu / id is resolved

## 1.0.6 — 2026-08-26


Language loading hotfix.

### Fixed
- Administrator dashboard/hub strings no longer show as raw language keys
- Stale unprefixed `com_devartforms.ini` files no longer shadow prefixed packs

### Added
- Language files also installed under the component `language/` folders

## 1.0.5 — 2026-08-26

Public release after 1.0.1. Intermediate 1.0.2–1.0.4 builds were not published;
their changes are included here.

### Added
- Administrator Dashboard hub (New Form / Forms / Submissions / Options)
- 15 packaged languages (en/el/fr/de/es/it/pt-BR/cs/nl/pl/ru/uk/ja/tr/zh-CN)
- Configurable frontend submission rate limiting
- Schema compatibility markers through 1.0.5

### Fixed
- Package installer no longer overwrites `manifest_cache` to a stale 1.0.1
- HTML-safe JSON embedding in administrator submissions
- Free Text / HTML field sanitization on save and frontend render
- Frontend access-level enforcement on display and submit
- Null-safe active menu query handling
- Email subject CRLF hardening (test + live notifications)
- CSV formula-injection guard on export
- Notification mail failures logged without blocking stored submissions

### Changed
- PHP minimum aligned to 8.3.0
- Curated `el-GR`; additional languages machine-generated (open to review)

### Security
- Access checks, XSS-safe admin JSON, HTML sanitization, email/CSV hardening

## 1.0.1 — 2026-07-23

Security and CAPTCHA reliability update (anti-spam, Cloudflare cache safety,
reCAPTCHA / Turnstile / PoW improvements).

## 1.0.0 — 2026-07-09

Initial public stable release for Joomla 6.
