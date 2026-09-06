# Hero Bio and Toolkit Implementation Report

## Executive Recommendation

Update only the active SVG hero, `assets/hero.svg`. Use the vault-supported positioning "Software engineer with a background in economics and European fintech," add a short narrative about 42 Berlin, economics, prior business work, and current engineering focus, and present TypeScript, React, Next.js, Prisma, and Docker as the five core toolkit chips.

This is the smallest coherent change because the README directly embeds the SVG, the existing five-chip geometry already fits the selected stack, and the broader icon cloud still represents secondary technologies such as C++, PostgreSQL, and Python.

Implementation status: complete and locally validated.

## Scope

Target repository: `C:\Users\molze\GitHub\peterle95`

Requested outcome: inspect the Obsidian AI vault for Peter Mölzer's public bio and technology stack, compare implementation options, and update the hero's `whoami` content and `RUNTIME / TOOLKIT` section.

Assumptions:

- "Hero section" means the SVG rendered at the top of the GitHub profile.
- The hero should use public professional facts, not private or unrelated vault material.
- The five-chip limit should be preserved unless stronger evidence requires a layout expansion.
- Conflicting employment and education dates should not appear in the hero.
- The checked-in HTML prototype and backup files are historical references, not generated sources.

## Repository Map

### Facts

| Path | Role | Evidence |
|---|---|---|
| [`README.md`](../README.md) | GitHub profile entry point | Line 3 embeds `./assets/hero.svg` at full width. |
| [`assets/hero.svg`](../assets/hero.svg) | Active hero source | Lines 1-3 define the accessible SVG; lines 65-74 contain `whoami` and the bio; lines 82-95 contain toolkit chips. |
| `assets/*.png` | Original technology icons | The active SVG uses embedded data URIs rather than these paths. |
| `prototypes/terminal-portfolio.html` | Design reference | It duplicates hero content but is not referenced by `README.md`. |
| `assets/hero.svg.backup*`, `README.md.backup*` | Historical snapshots | No active file references them. |

Render path:

```text
GitHub profile -> README.md -> assets/hero.svg
```

There is no manifest, build script, test suite, CI workflow, or SVG generator. Recent history shows direct SVG edits: icon embedding in `16ccf08`, icon expansion in `13bab45`, and animation in `b2006d5`.

### Constraints

- The SVG has a fixed `1120 x 720` view box (`assets/hero.svg:1`).
- The left pane ends at `x=777.5` (`assets/hero.svg:50`).
- The bio uses two manually positioned text nodes, so it does not wrap automatically (`assets/hero.svg:73-74`).
- The toolkit starts at global `x=802` and has about 318 units of usable width (`assets/hero.svg:82-95`).
- Toolkit chips use fixed rectangles rather than calculated text widths.
- A third chip row would cross the divider at `y=306.5` (`assets/hero.svg:97`).
- Eleven embedded logos are animated with staggered `nth-child` rules; changing chip text does not require changing those images (`assets/hero.svg:13-30`).

## Vault Findings

Vault searched: `C:\Users\molze\GitHub\Obsidian\AI`

The alternative configured path `D:\Obsidian Vault\AI Research` was absent. Unrelated and sensitive personal material was excluded.

### Primary Evidence

1. `C:\Users\molze\GitHub\Obsidian\AI\raw\processed\Peter's CV.md`, heading `ABOUT ME`

   Self-authored public source. Lines 10-15 identify Peter as a software engineer with 42 Berlin training, a B.Sc. in Economics, fintech experience at Klarna and CLARK, and specialization in TypeScript, React, and Next.js. Lines 55-80 support React, TypeScript, Docker, CI/CD, APIs, Tailwind, Node.js, MySQL, and GitHub Actions. Lines 145-190 support C++, Linux, Docker, networking, and project work.

2. `C:\Users\molze\GitHub\Obsidian\AI\raw\processed\Reference Letter - Peter Mölzer - InnoBee.md`, heading `Reference Letter for Peter Mölzer`

   Independent professional source dated 2026-07-16. Lines 11-18 confirm full-stack and DevOps work, Docker containerization, TypeScript/React standards, collaborative feature delivery, and frontend/backend schema synchronization.

3. `C:\Users\molze\GitHub\Obsidian\AI\wiki\me\profile.md`, headings `Summary` and `Stable Facts`

   Current multi-source synthesis updated 2026-09-01. Lines 18-22 support the economics-to-software transition, 42 alumnus status, and public software-engineer positioning. The note reports 14 sources and medium confidence at lines 1-10.

4. `C:\Users\molze\GitHub\Obsidian\AI\wiki\projects\career-and-work-transition.md`, heading `Career And Work Transition`

   High-confidence synthesis. Lines 46-48 list React, TypeScript, Next.js, Node.js, Tailwind, APIs, Docker, CI/CD, MySQL, and SQL as practical experience. Lines 55-60 support Prisma, WebSockets, deployment, and CI/CD contributions.

5. `C:\Users\molze\GitHub\Obsidian\AI\raw\processed\Transcendence README.md`, headings `Technical Stack` and `Individual Contributions`

   Team-authored project evidence. Lines 19-53 document TypeScript, React, Next.js, PostgreSQL/Prisma, Socket.IO, Tailwind, and related technologies. Lines 119-127 specifically attribute Prisma ORM and shared WebSocket work to Peter.

### Supporting Evidence

- `C:\Users\molze\GitHub\Obsidian\AI\wiki\projects\tech\shellfolio.md:15-19` confirms Next.js App Router, React, TypeScript, and Tailwind in a personal portfolio.
- `C:\Users\molze\GitHub\Obsidian\AI\raw\processed\shellfolio-tech-project.md:21-43` confirms Next.js 15, React 19, TypeScript 5, and Tailwind CSS 3.
- `C:\Users\molze\GitHub\Obsidian\AI\wiki\projects\tech\nextjs-memory-palace-app.md:20-26,66-95` provides recent Next.js, React, TypeScript, Prisma, and Neon/PostgreSQL evidence.
- `C:\Users\molze\GitHub\Obsidian\AI\wiki\projects\tech\printing-press-clis.md:23-29` demonstrates Go, Python, Node.js/TypeScript, Playwright, SQLite, OAuth, and CLI work, but these are broader capabilities rather than the clearest hero specialization.

### Conflicts and Exclusions

- Employment dates conflict between the CV, reference letter, and Shellfolio data. Dates are omitted.
- Humboldt dates conflict between the CV and Shellfolio data. Dates are omitted.
- Python appears in projects, but a career note also records it as a skills gap. It remains in the broad icon cloud but is not promoted to a core chip.
- AI model training in Transcendence is attributed to another teammate. No AI-training claim is made.
- The CV supports C/C++ experience, but the strongest repeated current specialization is TypeScript, React, Next.js, Docker, and Prisma/PostgreSQL.

## Evidence Matrix

| Claim | Repository evidence | Vault evidence | Assessment |
|---|---|---|---|
| Public role is software engineer | Existing hero used "software developer" at the former `assets/hero.svg:72`; README describes full-stack development at `README.md:17`. | CV `ABOUT ME:10-15`; profile `Summary:18-22`. | Strong; use "Software engineer." |
| Economics background is relevant | `README.md:17,29-34`. | CV `ABOUT ME:10-15`; profile `Summary:18-22`. | Strong; include in concise bio. |
| European fintech is relevant | Repository mentions prior markets and partnerships but not "fintech" in the active README. | CV `ABOUT ME:10-15` identifies Klarna and CLARK fintech experience. | Supported by primary vault evidence; safe without dates or titles. |
| TypeScript, React, Next.js are core | `README.md:115-117`; existing chips at `assets/hero.svg:85-90`. | CV `ABOUT ME:12-15`; career note `46-48`; Shellfolio `15-19`. | Strongest repeated specialization; retain. |
| Docker is core toolkit | `README.md:117-119`; existing chip at `assets/hero.svg:93-94`. | CV `55-80`; reference letter `11-18`; career note `46-48`. | Strong; retain. |
| Prisma merits a core chip | Prisma already exists in the eleven-logo inventory. | Transcendence README `119-127`; career note `55-60`; Memory Palace `20-26,66-95`. | Strong personal and recent evidence; promote. |
| C/C++ remains part of broader range | `README.md:116`; C++ logo remains embedded. | CV `145-190`. | Supported but less central to current specialization; retain as icon, not core chip. |

## Candidate Comparison

| Candidate | Files | Architectural fit | Effort | Risks | Reversibility |
|---|---:|---|---|---|---|
| A. Replace copy and one chip in the active SVG | 1 | Best: edits the sole rendered source and preserves existing geometry | Low | Fixed text metrics require visual verification | One-file revert |
| B. Expand to six chips with separate PostgreSQL and Prisma entries | 1 | Valid, but requires manual two-row reflow and new rectangle widths | Medium | Crowding, font fallback overflow, more layout maintenance | One-file revert |
| C. Synchronize SVG, README prose, prototype, and backups | 3+ active/historical files | Poor: prototype and backups do not render the profile and no generator links them | High | Duplicate content drifts; historical files lose value | Multi-file revert |

Candidate A wins because it satisfies the request with the smallest rendered-surface change. Candidate B adds detail the icon cloud already conveys. Candidate C conflicts with the repository's direct-render path and creates unnecessary synchronization work.

## Chosen Design

### Recommendation

- Accessible description: identify Peter as a Berlin-based software engineer with economics and European fintech experience.
- Visible `whoami` bio: `Software engineer with a background in economics and European fintech.`
- About text: summarize 42 Berlin and economics education, prior fintech/partnerships/business-development work, and the current full-stack products, developer tools, and infrastructure focus.
- Core toolkit: `TypeScript`, `React`, `Next.js`, `Prisma`, `Docker`.
- Broad icon cloud: unchanged, preserving C++, PostgreSQL, Python, infrastructure, and editor/tooling context.

### Implemented Changes

All source changes are in [`assets/hero.svg`](../assets/hero.svg):

- Line 3 synchronizes the accessible description with the visible bio.
- Lines 73-80 provide the visible `whoami` summary and expanded about text.
- The toolkit replaces `C/C++` with `Prisma` and widens the chip from 56 to 61 units.
- The scoped `.toolkit rect` rule fixes an existing SVG inheritance issue that made toolkit labels gray-on-gray: rectangles now explicitly use `fill: none`, while text inherits the muted foreground color.

No README, prototype, backup, logo, animation, or standalone PNG changes are required.

## Validation

Executed checks:

```powershell
git diff --check
```

Result: passed; only Git's existing LF-to-CRLF warning was emitted.

```powershell
$svg = [xml][System.IO.File]::ReadAllText((Resolve-Path 'assets/hero.svg'))
# Select all SVG image nodes and decode every base64 payload.
```

Result: XML parsed successfully; all 11 embedded images were present and decoded.

The SVG was rendered at its native `1120 x 720` dimensions with headless Chrome. Visual verification confirmed:

- the bio stays within the left pane;
- the emphasized and muted bio segments do not overlap;
- all four about lines fit within the marked lower-left area and remain above the footer divider;
- all five toolkit labels are visible and contained by their chips;
- the widened Prisma chip remains inside the right pane;
- all 11 logos still render.

There are no repository-provided automated tests or build commands.

## Risks and Open Questions

- GitHub is the definitive renderer; its SVG sanitizer, font fallback, cache, and animation behavior can differ from local Chrome.
- `European fintech` is supported by the CV but is intentionally broader than listing employers or disputed roles and dates.
- PostgreSQL is represented in the icon cloud rather than a core chip. Add a sixth chip only if the hero must explicitly distinguish database from ORM experience.
- The static SVG does not reflow on narrow screens; the full composition scales down uniformly, matching existing behavior.

## Rollback

The implementation is isolated to `assets/hero.svg`. Reverting that file restores the former bio, `C/C++` chip, and prior chip-fill behavior. No migration or persisted-data handling is involved.
