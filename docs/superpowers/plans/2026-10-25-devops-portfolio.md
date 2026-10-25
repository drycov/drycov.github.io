# DevOps Portfolio Implementation Plan

> **For agentic workers:** Use this plan task by task. Each step uses checkbox syntax for tracking.

**Goal:** Replace the GI-PON home page with a Russian-language, responsive DevOps and infrastructure portfolio while preserving the existing policy and account-deletion pages.

**Architecture:** Keep GitHub Pages and Jekyll. Add a dedicated portfolio layout and stylesheet for the homepage; keep legacy pages on the existing default layout and update shared navigation to link back to the portfolio.

**Tech Stack:** Jekyll, Liquid, Markdown, semantic HTML, CSS.

**Spec:** `docs/superpowers/specs/2026-10-25-devops-portfolio-design.md`

## Global Constraints

- Keep GitHub Pages and Jekyll; add no framework or runtime dependency.
- Use Russian as the primary language and suitable English metadata for search/social previews.
- Link project cards to public repositories and use no fabricated metrics, employers, certifications, or experience dates.
- Keep the privacy-policy and account-deletion pages available at their current URLs.
- Use responsive layout, visible keyboard focus, sufficient contrast, and reduced-motion support.

## Review Focus

- At narrow mobile widths, navigation and project cards must remain readable without horizontal overflow.
- Long project names and technology labels must wrap without breaking the card grid.
- Legacy policy and delete-account routes must remain reachable and keep their existing layout and content.
- Internal section links must target actual IDs and GitHub links must target the correct repositories.
- If JavaScript is unnecessary, the portfolio must work with JavaScript disabled.

---

### Task 1: Add the dedicated portfolio page

**Files:**
- Create: `_layouts/portfolio.html`
- Create: `assets/css/portfolio.css`
- Modify: `index.md`
- Modify: `_config.yml`

**Interfaces:**
- Portfolio layout consumes Jekyll `page.title`, `page.description`, `site.title`, `site.description`, `site.url`, and rendered `content`.
- Homepage content provides section IDs `about`, `skills`, `projects`, and `contact`; navigation links target these IDs.

- [ ] Add the semantic HTML layout with responsive navigation, metadata, footer, and stylesheet reference.
- [ ] Add CSS for dark, restrained portfolio styling, responsive project cards, keyboard focus, and reduced motion.
- [ ] Replace the GI-PON landing copy with profile, skills, selected work, and contact sections.
- [ ] Set Jekyll site title, description, and language to the portfolio identity.

**Verification:** Inspect generated source and repository CI output for Liquid/HTML build errors; manually check desktop/mobile layout and each link.

### Task 2: Keep legacy pages connected

**Files:**
- Modify: `_includes/sidebar.html`
- Preserve: `privacy_policy.md`
- Preserve: `delete_me.md`

**Interfaces:**
- Existing legacy pages continue using `layout: default`.
- Shared sidebar links to the new homepage and retains policy and account-deletion URLs.

- [ ] Update the shared navigation labels and destinations without changing the existing page bodies or account-deletion form.
- [ ] Confirm the homepage links to both legacy pages and the legacy navigation links back home.

**Verification:** Inspect rendered navigation and confirm the two existing routes still resolve after GitHub Pages publishes.
