# GitHub Profile README Redesign

**Date:** 2026-03-13
**Status:** Approved

---

## Goals

- **Primary audience:** Recruiters, hiring managers, potential employers (portfolio)
- **Secondary audience:** Other PMs, designers, devs for networking
- **Language:** English
- **Visual style:** Header visual + clean content below (professional, not over-designed)

## Design Decisions

### Approach: Hybrid — Impact + Personality

Combines a polished visual header with clean, structured content that works for both audiences.

### Section Structure

#### 1. Header Banner
- Dark gradient background (dark blue → subtle purple)
- Clean typography: "Sara Maciel"
- Tagline: "Product Manager — AI Platforms, Integrations & B2B SaaS"
- Centered LinkedIn and Email badges below
- **Implementation:** Static SVG file stored in `assets/banner.svg`. The custom multi-stop gradient (`#0f1729 → #1a1e4a → #2d1b4e → #1e1145`) cannot be reproduced via capsule-render's color parameter, so a committed SVG is the correct path. Referenced in README as `![Banner](./assets/banner.svg)`.

#### 2. About Me
- Short narrative paragraph (no bullets), 3-4 lines
- Covers: what she does, the differentiator (AI + integrations + B2B SaaS intersection), how she works (AI-augmented, methodologies)
- Tone: direct, no buzzwords
- Title is "Product Manager" (not Senior)

**Text:**
> Product Manager building AI-powered platforms that connect businesses to their customers. I work at the intersection of conversational AI, CRM/ERP integrations, and B2B SaaS — turning complex technical ecosystems into products that scale.
>
> I use AI daily as a thinking and execution partner, not just as a feature I ship. Shape Up, Continuous Discovery, and data-informed decisions guide how I build.

#### 3. What I Work On
- 2x2 grid with icons and 1-line descriptions
- **Layout constraint:** GitHub strips all CSS (`style`, `class`, `display: grid`). Must use raw `<table>` / `<tr>` / `<td>` HTML without any `style` or `class` attributes. No inline styles will render.
- Items:
  - AI Conversational Platforms — End-to-end product ownership of AI agents serving thousands of businesses
  - CRM & ERP Integrations — 50+ integrations connecting real estate platforms to the AI ecosystem
  - Workflows & Automation — Operational pipelines that reduce manual work and increase reliability
  - Platform Health & Observability — Monitoring, alerting, and data-driven decisions at scale

#### 4. Toolkit
Organized in 3 sub-groups with visual badges:

- **AI Tools:** Claude, ChatGPT, Gemini, NotebookLM, Manus
- **Product & Methodology:** Shape Up, Scrum, Continuous Discovery, Product Strategy
- **Day-to-day:** Jira, Miro, Notion, SQL, GitHub, PostHog

#### 5. Featured Projects
- Placeholder section with "Coming soon" message
- Prepared to expand when public repos are created
- Future content candidates: product templates, automation scripts, documented frameworks

#### 6. Let's Connect
- CTA text: "I'm always open to conversations about product, AI, integrations, and building things that matter."
- LinkedIn and Email badges

**Canonical links:**
- LinkedIn: `https://linkedin.com/in/sara-elisa`
- Email: `mailto:saraelisatm25@gmail.com`

#### 7. GitHub Activity
- GitHub Stats card using `github-readme-stats` with `count_private=true`
- Top Languages card titled **"Top Languages (Public Repos)"** to be transparent about scope
- Dark theme matching the overall design
- **Note:** `count_private=true` requires the user to have authorized the github-readme-stats Vercel deployment via OAuth, or to self-host with a PAT that has `repo` scope. If not configured, the parameter is silently ignored. Verify before publishing.

#### 8. Footer
- Light closing line: "Built with curiosity and too many AI conversations"

## Technical Implementation

- **Banner:** Static SVG in `assets/banner.svg` — custom gradient not reproducible via capsule-render. Author the SVG directly using a `<linearGradient>` element with stops `#0f1729 → #1a1e4a → #2d1b4e → #1e1145`, canvas 860x200px. The `.banner` CSS block in `preview-readme.html` contains the reference gradient values.
- **Badges:** shields.io `for-the-badge` style
- **Stats:** github-readme-stats by anuraghazra (`count_private=true`, dark theme). Requires OAuth setup — see Section 7 note.
- **Grid layout:** `<table>` HTML only — GitHub strips CSS grid, flexbox, style attributes, and class attributes
- **Icons:** Emoji for section headers, shields.io for tools

## What's NOT Included (By Design)

- No Senior in title
- No Amplitude (not used)
- No Figma (not used)
- No snake animation (unnecessary complexity)
- No WakaTime (not relevant for PM profile)

## Preview

Visual mockup available at `preview-readme.html` in the repo root.
