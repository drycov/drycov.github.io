# Developer Portfolio Implementation Plan

> **For agentic workers:** Use this plan task by task. Each step uses checkbox syntax for tracking.

**Goal:** Replace the GI-PON home page with Denis Rykov's Russian-language developer portfolio while preserving the existing policy and account-deletion pages.

**Architecture:** Keep GitHub Pages and Jekyll. Add a dedicated portfolio layout and stylesheet for the homepage; keep legacy pages on the existing default layout and update shared navigation to link back to the portfolio.

**Tech Stack:** Jekyll, Liquid, Markdown, semantic HTML, CSS.

**Spec:** `docs/superpowers/specs/2026-10-25-devops-portfolio-design.md`

## Global Constraints

- Keep GitHub Pages and Jekyll; add no framework or runtime dependency.
- Position the site as a developer portfolio; present infrastructure and DevOps as complementary strengths.
- Use Russian as the primary language and suitable English metadata for search/social previews.
- Link only public projects; use no fabricated metrics, employers, certifications, or experience dates.
- Keep the privacy-policy and account-deletion pages available at their current URLs.
- Use responsive layout, visible keyboard focus, sufficient contrast, and reduced-motion support.

## Review Focus

- At narrow mobile widths, navigation and project cards must remain readable without horizontal overflow.
- Long project names and technology labels must wrap without breaking the card grid.
- Legacy policy and delete-account routes must remain reachable and keep their existing layout and content.
- Internal section links must target actual IDs and GitHub links must target the correct repositories.
- The portfolio must work with JavaScript disabled.

---

### Task 1: Add the developer portfolio page

**Files:**
- Create: `_layouts/portfolio.html`
- Create: `assets/css/portfolio.css`
- Modify: `index.md`
- Modify: `_config.yml`

**Interfaces:**
- Portfolio layout consumes Jekyll `page.title`, `page.description`, `site.title`, `site.description`, and rendered `content`.
- Homepage content provides section IDs `about`, `skills`, `projects`, and `contact`; navigation links target these IDs.

- [x] Add semantic layout with metadata, responsive navigation, rendered content, and footer.
- [x] Add CSS for dark developer portfolio styling, responsive skill/project cards, keyboard focus, and reduced motion.
- [x] Replace GI-PON copy with developer introduction, skills, engineering approach, five public project cards (ZBSS, CMS, Zabbix Dialer, OptiBudget, PPR System), and contact links.
- [x] Set Jekyll title, description, URL, and language to the portfolio identity.

### Task 2: Keep legacy pages connected

**Files:**
- Modify: `_includes/sidebar.html`
- Preserve: `privacy_policy.md`
- Preserve: `delete_me.md`

**Interfaces:**
- Existing legacy pages continue using `layout: default`.
- Shared sidebar links to the portfolio homepage and retains policy and account-deletion URLs.

- [x] Update shared navigation destinations without changing legacy page bodies or the account-deletion form.
- [x] Add portfolio footer links to both legacy pages.

**Verification:** Check GitHub Pages build status and rendered routes after publishing. No new tests were added.
