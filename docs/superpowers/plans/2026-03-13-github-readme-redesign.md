# GitHub Profile README Redesign — Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rewrite the GitHub profile README for `saramaciel-rgb` with a visual banner, structured content sections, and professional positioning.

**Architecture:** Static SVG banner + GitHub-flavored Markdown with inline HTML tables (no CSS — GitHub strips it). External services: shields.io for badges, github-readme-stats for activity widgets.

**Tech Stack:** SVG, GitHub-flavored Markdown, HTML tables, shields.io, github-readme-stats

**Spec:** `docs/superpowers/specs/2026-03-13-github-readme-redesign-design.md`

**Preview mockup:** `preview-readme.html` (open in browser for visual reference)

---

## Chunk 1: Banner + README

This plan has 3 tasks that must be done sequentially. No tests — this is a static Markdown/SVG project.

---

### Task 1: Create the banner SVG

**Files:**
- Create: `assets/banner.svg`

- [ ] **Step 1: Create assets directory**

```bash
mkdir -p assets
```

- [ ] **Step 2: Create `assets/banner.svg`**

Create an SVG file at 860x200px with:
- A `<linearGradient>` using stops: `#0f1729` (0%), `#1a1e4a` (35%), `#2d1b4e` (65%), `#1e1145` (100%), at 135 degrees
- A subtle cross-pattern overlay at low opacity for texture
- Text "Sara Maciel" centered, white, bold, ~36px
- Text "Product Manager — AI Platforms, Integrations & B2B SaaS" centered below, white at 70% opacity, ~15px
- Font: `Segoe UI, -apple-system, sans-serif` (safe cross-platform)

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="860" height="200" viewBox="0 0 860 200">
  <defs>
    <linearGradient id="bg" x1="100%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" stop-color="#0f1729"/>
      <stop offset="35%" stop-color="#1a1e4a"/>
      <stop offset="65%" stop-color="#2d1b4e"/>
      <stop offset="100%" stop-color="#1e1145"/>
    </linearGradient>
    <pattern id="grid" width="60" height="60" patternUnits="userSpaceOnUse">
      <path d="M 36 30 v-4 h-2 v4 h-4 v2 h4 v4 h2 v-4 h4 v-2 h-4 z M 6 30 v-4 H4 v4 H0 v2 h4 v4 h2 v-4 h4 v-2 H6 z" fill="#9C92AC" fill-opacity="0.03"/>
    </pattern>
  </defs>
  <rect width="860" height="200" fill="url(#bg)"/>
  <rect width="860" height="200" fill="url(#grid)"/>
  <text x="430" y="88" text-anchor="middle" font-family="Segoe UI, -apple-system, BlinkMacSystemFont, sans-serif" font-size="36" font-weight="700" fill="#ffffff">Sara Maciel</text>
  <text x="430" y="118" text-anchor="middle" font-family="Segoe UI, -apple-system, BlinkMacSystemFont, sans-serif" font-size="15" fill="#ffffff" fill-opacity="0.7">Product Manager — AI Platforms, Integrations &amp; B2B SaaS</text>
</svg>
```

- [ ] **Step 3: Verify the SVG renders correctly**

Open `assets/banner.svg` in a browser and confirm:
- Gradient goes dark blue → purple
- Both text lines are visible, centered, and readable
- Subtle texture pattern visible in background

- [ ] **Step 4: Commit**

```bash
git add assets/banner.svg
git commit -m "feat: add banner SVG for profile README"
```

---

### Task 2: Rewrite README.md

**Files:**
- Modify: `README.md` (full rewrite)

**Reference:** Open `preview-readme.html` in browser for visual target. The Markdown below reproduces that layout using only GitHub-compatible syntax.

**Note:** The spec references the banner as `![Banner](./assets/banner.svg)` (plain Markdown). This plan uses `<p align="center"><img ...></p>` instead to achieve centering and full-width display, which plain Markdown image syntax cannot do on GitHub. This is an intentional deviation.

- [ ] **Step 1: Rewrite `README.md` with all 8 sections**

Replace the entire contents of `README.md` with the following:

````markdown
<p align="center">
  <img src="./assets/banner.svg" alt="Sara Maciel — Product Manager" width="100%"/>
</p>

<p align="center">
  <a href="https://linkedin.com/in/sara-elisa">
    <img src="https://img.shields.io/badge/LinkedIn-Sara%20Maciel-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="mailto:saraelisatm25@gmail.com">
    <img src="https://img.shields.io/badge/Email-Contact%20me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
  </a>
</p>

---

## About me

Product Manager building **AI-powered platforms** that connect businesses to their customers. I work at the intersection of **conversational AI, CRM/ERP integrations, and B2B SaaS** — turning complex technical ecosystems into products that scale.

I use AI daily as a thinking and execution partner, not just as a feature I ship. Shape Up, Continuous Discovery, and data-informed decisions guide how I build.

---

## What I work on

<table>
  <tr>
    <td width="50%">
      <strong>🤖 AI Conversational Platforms</strong><br/>
      End-to-end product ownership of AI agents serving thousands of businesses
    </td>
    <td width="50%">
      <strong>🔗 CRM & ERP Integrations</strong><br/>
      50+ integrations connecting real estate platforms to the AI ecosystem
    </td>
  </tr>
  <tr>
    <td width="50%">
      <strong>⚙️ Workflows & Automation</strong><br/>
      Operational pipelines that reduce manual work and increase reliability
    </td>
    <td width="50%">
      <strong>📊 Platform Health & Observability</strong><br/>
      Monitoring, alerting, and data-driven decisions at scale
    </td>
  </tr>
</table>

---

## Toolkit

**AI Tools**

![Claude](https://img.shields.io/badge/Claude-cc785c?style=for-the-badge&logoColor=white)
![ChatGPT](https://img.shields.io/badge/ChatGPT-412991?style=for-the-badge&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-4285f4?style=for-the-badge&logo=google&logoColor=white)
![NotebookLM](https://img.shields.io/badge/NotebookLM-fbbc04?style=for-the-badge&logo=google&logoColor=black)
![Manus](https://img.shields.io/badge/Manus-1a1a2e?style=for-the-badge&logoColor=white)

**Product & Methodology**

![Shape Up](https://img.shields.io/badge/Shape%20Up-3b82f6?style=for-the-badge&logoColor=white)
![Scrum](https://img.shields.io/badge/Scrum-6366f1?style=for-the-badge&logoColor=white)
![Continuous Discovery](https://img.shields.io/badge/Continuous%20Discovery-8b5cf6?style=for-the-badge&logoColor=white)
![Product Strategy](https://img.shields.io/badge/Product%20Strategy-0ea5e9?style=for-the-badge&logoColor=white)

**Day-to-day**

![Jira](https://img.shields.io/badge/Jira-0052cc?style=for-the-badge&logo=jira&logoColor=white)
![Miro](https://img.shields.io/badge/Miro-ffdd00?style=for-the-badge&logo=miro&logoColor=black)
![Notion](https://img.shields.io/badge/Notion-efefef?style=for-the-badge&logo=notion&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-24292f?style=for-the-badge&logo=github&logoColor=white)
![PostHog](https://img.shields.io/badge/PostHog-1d4aff?style=for-the-badge&logo=posthog&logoColor=white)

---

## Featured Projects

> 🚧 **Coming soon** — Public templates, frameworks, and tools for product managers working with AI platforms and integrations.

---

## Let's connect

I'm always open to conversations about product, AI, integrations, and building things that matter.

<a href="https://linkedin.com/in/sara-elisa">
  <img src="https://img.shields.io/badge/LinkedIn-Sara%20Maciel-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>
<a href="mailto:saraelisatm25@gmail.com">
  <img src="https://img.shields.io/badge/Email-Contact%20me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
</a>

---

## GitHub Activity

<a href="https://github.com/saramaciel-rgb">
  <img src="https://github-readme-stats.vercel.app/api?username=saramaciel-rgb&show_icons=true&count_private=true&theme=github_dark&bg_color=0d1117&title_color=58a6ff&text_color=c9d1d9&icon_color=79c0ff&border_color=30363d" alt="Sara's GitHub Stats" />
</a>

**Top Languages (Public Repos)**

<a href="https://github.com/saramaciel-rgb">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=saramaciel-rgb&layout=compact&theme=github_dark&bg_color=0d1117&title_color=58a6ff&text_color=c9d1d9&border_color=30363d&card_width=400" alt="Top Languages (Public Repos)" />
</a>

---

<p align="center">
  <sub>✨ Built with curiosity and too many AI conversations</sub>
</p>
````

- [ ] **Step 2: Verify the README renders correctly**

Push to GitHub (or preview locally with a Markdown renderer) and confirm:
- Banner displays full-width at top
- LinkedIn and Email badges render and link correctly
- "What I work on" table renders as 2x2 grid
- All toolkit badges render with correct colors
- Featured Projects blockquote renders cleanly
- GitHub stats cards load (may take a few seconds)
- GitHub stats card shows private commit count (if `count_private` OAuth is configured — see Post-Implementation Notes)
- "Top Languages (Public Repos)" label renders as a bold markdown heading above the card
- Footer text is centered and subtle

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "feat: redesign profile README with banner, toolkit, and stats"
```

---

### Task 3: Clean up

**Files:**
- Delete: `preview-readme.html` (served its purpose as mockup, not needed in the published profile)

- [ ] **Step 1: Remove the preview HTML**

```bash
git rm preview-readme.html
```

- [ ] **Step 2: Commit**

```bash
git commit -m "chore: remove preview mockup file"
```

- [ ] **Step 3: Push to GitHub and verify live**

```bash
git push origin main
```

Open `https://github.com/saramaciel-rgb` in a browser and verify the profile README renders as expected.

---

## Post-Implementation Notes

- **`count_private=true`:** If private commit counts don't appear in the stats card, the github-readme-stats Vercel deployment needs OAuth authorization. Visit the deployment URL to authenticate, or self-host with a PAT that has `repo` scope.
- **Top Languages title:** Uses a bold markdown heading above the card instead of the `title` query parameter (which doesn't work reliably on the public instance).
- **Future projects:** When ready to add public repos, replace the "Featured Projects" blockquote with pinned repo cards using `[![Repo Card](https://github-readme-stats.vercel.app/api/pin/?username=saramaciel-rgb&repo=REPO_NAME&theme=github_dark)](https://github.com/saramaciel-rgb/REPO_NAME)`.
