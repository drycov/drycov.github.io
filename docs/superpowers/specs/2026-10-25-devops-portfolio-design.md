# Developer portfolio redesign

**Date:** 2026-10-25  
**Repository:** `drycov/drycov.github.io`

## Intent
Replace the GI-PON product landing page with Denis Rykov's Russian-language developer portfolio. Present software development as the primary identity, with infrastructure and DevOps as complementary strengths. Help a technical lead or prospective client quickly understand the work, inspect real public projects, and make contact.

## Goals
- Build a single-page portfolio with an introduction, development capabilities, selected projects, engineering approach, and contact links.
- Feature public projects: ZBSS, CMS, Zabbix Dialer, OptiBudget, and PPR System.
- Describe projects and technologies only where supported by repository documentation or known project context; do not publish private projects or fabricate metrics, employers, certifications, or experience dates.
- Make the site readable on desktop and mobile, with accessible contrast and clear links.
- Preserve the existing privacy-policy and account-deletion pages.

## Non-goals
- No backend, analytics, forms, or external UI framework.
- No fabricated uptime, scale, years of experience, or production metrics.
- No changes to the source applications in the featured repositories.

## Approaches
1. **Terminal/infrastructure dashboard:** visually distinctive, but suggests live system data and overemphasizes DevOps.
2. **Developer portfolio with engineering case studies (selected):** restrained dark style, real software projects, development capabilities, and infrastructure strengths; matches the requested identity and is grounded in actual work.
3. **Keep the current Architect theme:** minimal changes, but does not meet the requested portfolio redesign.

## Constraints and implementation choices
- Keep GitHub Pages and Jekyll; retain existing static privacy/deletion pages.
- Add a dedicated responsive portfolio layout and stylesheet without added runtime dependencies.
- Use Russian as the primary language and English metadata where useful for search/social previews.
- Link each project card to its public GitHub repository.
- Include the existing public email and GitHub profile as contact methods.
- Keep legacy pages on the existing Jekyll theme and layout.

## Remaining implementation decisions
- Organize the homepage as a single scrollable page with anchored sections.
- Use CSS for a developer-focused hero, skill groups, project cards, and responsive navigation.
- Avoid simulated live telemetry and JavaScript-dependent navigation.
