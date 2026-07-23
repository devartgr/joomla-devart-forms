# DevArt Forms for Joomla

Professional Joomla 6 forms solution designed for contact forms, business inquiries, registrations, feedback, applications, surveys, and high-performance production websites.

![Joomla](https://img.shields.io/badge/Joomla-6.x-blue)
![PHP](https://img.shields.io/badge/PHP-8.2%2B-green)
![Release](https://img.shields.io/badge/Version-1.0.1-orange)
![License](https://img.shields.io/badge/License-GPLv3-red)

---

# Overview

DevArt Forms is a modern Joomla 6 native forms component built for creating professional forms with a strong focus on simplicity, performance, security, multilingual support and production-ready architecture.

Unlike overly complex enterprise form builders, DevArt Forms provides a clean administrator interface while delivering the functionality required by business websites, organizations, educational institutions, municipalities, publishers and high-traffic Joomla installations.

The extension is designed exclusively for Joomla 6 and modern PHP versions without legacy compatibility layers.

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

Fully compatible with Joomla multilingual websites.

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

- com_devartforms

---

# Requirements

- Joomla 6.x
- PHP 8.2+

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

# Security Highlights

- Joomla ACL support
- CSRF protection
- Server-side validation
- SQL parameter binding
- Safe output escaping
- Secure email processing
- Proof of Work
- Google reCAPTCHA v2
- Cloudflare Turnstile
- Production-safe architecture

---

# Compatibility

Supported:

- Joomla 6.x
- PHP 8.2+
- Joomla native updates
- Modern Joomla MVC architecture

Not Supported:

- Joomla 3
- Joomla 4
- Joomla 5
- Legacy PHP versions

---

# Current Version

**1.0.1**

---

# What's New in 1.0.1

## Fixed

- Improved anti-spam validation reliability
- Improved Cloudflare cache compatibility
- Fixed CAPTCHA reset handling after successful submissions
- Fixed repeated submission handling
- Fixed Proof of Work validation edge cases

## Improved

- Google reCAPTCHA v2 server-side verification
- Cloudflare Turnstile server-side verification
- Proof of Work validation workflow
- CSRF token handling
- Protected form submission reliability
- Overall security hardening

## Security

- Strengthened server-side CAPTCHA verification
- Added stricter validation for invalid and expired anti-spam tokens
- Improved fail-safe handling for CAPTCHA verification failures
- Additional production security improvements

---

# Previous Release

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
