# DevOps portfolio redesign

**Date:** 2026-10-25  
**Repository:** `drycov/drycov.github.io`

## Intent
Replace the GI-PON product landing page with a Russian-language professional portfolio for Denis, focused on DevOps, infrastructure, network engineering, and software delivery. Help a hiring manager or technical lead quickly understand the author's strengths, inspect concrete work, and find contact links.

## Goals
- Create a concise single-page portfolio with an introduction, skills, selected projects, engineering approach, and contacts.
- Feature real public repositories such as ZBSS, CMS, ALPR Mergen, OptiBudget, PPR System, and Zabbix Dialer.
- Describe technologies and outcomes only where supported by available project context; avoid fabricated metrics, employers, certifications, and employment dates.
- Make the site readable on desktop and mobile, with accessible contrast and clear links.
- Preserve the existing privacy-policy and account-deletion pages.

## Non-goals
- No backend, analytics, forms, or external UI framework.
- No invented uptime, scale, years of experience, or production metrics.
- No changes to the source applications in the featured repositories.

## Approaches
1. **Terminal/infrastructure dashboard:** memorable, but risks presenting invented live system state.
2. **Professional engineering portfolio (selected):** restrained dark visual style with real project cards, technology groups, and contact links; clearer for hiring and grounded in existing work.
3. **Keep the current Architect theme:** minimal changes, but does not meet the requested portfolio redesign.

## Constraints and implementation choices
- Keep GitHub Pages and Jekyll; retain existing static privacy/deletion pages.
- Replace the Architect layout with a custom responsive portfolio layout and CSS, avoiding added dependencies.
- Use Russian as the primary language and English metadata where useful for search/social previews.
- Link each project card to its public GitHub repository.
- Include a short, direct contact section using the existing public email and GitHub profile.

## Remaining implementation decisions
- Organize the homepage as a single scrollable page with anchored sections.
- Use lightweight CSS details (grid, terminal-inspired labels, status colors) without simulated live telemetry.
- Preserve legacy pages with a compact navigation link back to the portfolio.
