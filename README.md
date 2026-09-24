# DevArt Forms for Joomla

Professional Joomla 6 forms solution designed for contact forms, business inquiries, registrations, feedback, applications, surveys, and high-performance production websites.

![Joomla](https://img.shields.io/badge/Joomla-6.x-blue)
![PHP](https://img.shields.io/badge/PHP-8.3%2B-green)
![Release](https://img.shields.io/badge/Version-1.0.7-orange)
![License](https://img.shields.io/badge/License-GPLv3-red)

---

# Overview

DevArt Forms is a modern Joomla 6 native forms component built for creating professional forms with a strong focus on simplicity, performance, security, multilingual support and production-ready architecture.

Unlike overly complex enterprise form builders, DevArt Forms provides a clean administrator interface while delivering the functionality required by business websites, organizations, educational institutions, municipalities, publishers and high-traffic Joomla installations.

The extension is designed exclusively for Joomla 6 and PHP 8.3+ without legacy compatibility layers.

---

# Features

## Professional Form Builder

Create unlimited forms using a clean visual field builder.

Supported field types:

- Text
- Email
- Textarea
- Select
- Radio
- Checkbox
- Checkbox Group
- Hidden
- Heading
- Free Text
- Date / Time

Field features include:

- Required fields
- Published state
- Field ordering
- Internal field names
- Multilingual labels
- Placeholders
- Descriptions
- Built-in validation
- Responsive layouts

---

## Multilingual Support

Complete multilingual editing for:

- Form titles
- Form descriptions
- Field labels
- Placeholders
- Help text
- Success messages
- Error messages
- Email templates

Packaged administrator and site languages:

- English (`en-GB`)
- Greek (`el-GR`, curated)
- French, German, Spanish, Italian, Brazilian Portuguese
- Czech, Dutch, Polish, Russian, Ukrainian, Japanese, Turkish, Chinese Simplified

Fully compatible with Joomla multilingual websites. Machine-generated packs are open to native-speaker review.

---

## Email Notifications

Flexible notification system supporting:

- Administrator notifications
- User confirmation emails
- HTML emails
- Plain text emails
- Reply-To
- CC
- BCC
- Custom recipients
- Email field recipients
- Dynamic placeholders

---

## Submission Manager

Manage form submissions directly inside Joomla.

Features include:

- Submission list
- Search
- Filters
- Sorting
- Pagination
- Submission details
- CSV export

Designed for both small and very large websites.

---

## Security

Built-in protection includes:

- Joomla ACL
- Frontend form access levels
- CSRF protection
- Server-side validation
- Client-side validation
- SQL parameter binding
- Safe output escaping
- Honeypot protection
- Proof of Work
- Google reCAPTCHA v2
- Cloudflare Turnstile
- Rate limiting
- CSV formula-injection guard
- Email subject header hardening

Anti-spam validation is performed server-side for maximum reliability.

Designed for secure production deployments.

---

## Backup & Restore

Portable form management.

Features include:

- Export forms
- Import forms
- Configuration backup
- Configuration restore
- Safe validation

Ideal for migrations, backups and development workflows.

---

## Joomla Native Updates

Supports Joomla native update notifications through GitHub.

Update Server:

https://raw.githubusercontent.com/devartgr/joomla-devart-forms/main/update.xml

---

# Included Extension

This package installs:

- `com_devartforms`

The package is component-only. It does not contain modules or plugins.

---

# Requirements

- Joomla 6.x
- PHP 8.3+

---

# Performance

Built for production environments.

Features include:

- Lightweight frontend
- Optimized database queries
- Minimal frontend assets
- Cache-friendly rendering
- Cloudflare compatible
- CDN friendly
- Responsive layouts
- Low resource usage

Suitable for:

- Business websites
- Corporate websites
- Municipal websites
- Educational institutions
- Associations
- NGOs
- News portals
- Enterprise deployments
- High-traffic Joomla websites

---

# Compatibility

Supported:

- Joomla 6.x
- PHP 8.3+
- Joomla native updates
- Modern Joomla MVC architecture

Not Supported:

- Joomla 3
- Joomla 4
- Joomla 5
- Legacy PHP versions

---

# Current Version

**1.0.7**

---

# What's New in 1.0.7

Joomla 7 forward compatibility, multilingual consent Privacy URL, and SEF form routing.

## Added

- Site router for clean menu / SEF form URLs
- Consent Privacy / Terms URL per language
- Schema compatibility marker for 1.0.7

## Changed

- `getInput()`, `MailerFactoryInterface`, and WebAssetManager for J7-ready APIs
- Administrator templates no longer rely on deprecated HTMLHelper behavior/grid/bootstrap.tab helpers

## Fixed

- Form view no longer defaults to form id `1` when no id is resolved

Safe update from DevArt Forms 1.0.6. Existing forms and submissions are preserved.

---

# Previous Releases

## Version 1.0.6

Language loading hotfix.

- Administrator dashboard/hub strings no longer show as raw language keys
- Stale unprefixed `com_devartforms.ini` files no longer shadow prefixed packs
- Language files also installed under the component `language/` folders

## Version 1.0.5

Public release after 1.0.1. Intermediate 1.0.2–1.0.4 builds were not published; their changes are included there.

- Administrator Dashboard hub (New Form / Forms / Submissions / Options)
- 15 packaged languages
- Configurable submission rate limiting
- Production hardening (access levels, XSS-safe admin JSON, HTML sanitization, email/CSV safety)
- Fixed package installer overwriting `manifest_cache` to a stale 1.0.1 after updates
- Schema compatibility markers through 1.0.5
- PHP minimum aligned to 8.3.0

## Version 1.0.1

Security and CAPTCHA reliability update:

- Anti-spam validation reliability
- Cloudflare cache compatibility
- CAPTCHA reset and repeated submission handling
- reCAPTCHA v2 / Turnstile / Proof of Work improvements

## Version 1.0.0

Initial public stable release featuring:

- Professional multilingual form builder
- Unlimited forms
- Multiple field types
- Submission manager
- CSV export
- Backup & Restore
- Administrator and user email notifications
- Proof of Work anti-spam
- Google reCAPTCHA v2
- Cloudflare Turnstile
- Joomla Update Server support

---

# Author

**Kostas Stathopoulos**  
DevArt

https://devart.gr

GitHub Repository:

https://github.com/devartgr/joomla-devart-forms

---

# License

GNU General Public License v3.0 (GPLv3)

---

# Disclaimer

This software is provided "as is", without warranty of any kind.

DevArt shall not be held liable for any damages, data loss, downtime, security incidents, business interruption, loss of profits or other consequences arising from the use or inability to use this software.

Always test updates in a staging environment before deploying to production systems.
