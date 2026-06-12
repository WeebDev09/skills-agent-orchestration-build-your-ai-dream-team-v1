# Project Pulse — Implementation Plan

Summary

- Goal: Build Mona's Project Pulse dashboard — a responsive frontend dashboard that surfaces active projects, status badges, priorities, and quick filters.
- Outcome: A runnable static frontend preview in `app/` showing an initial set of project cards, clear status indicators, and styling hooks for later integration.

Ordered Implementation Steps

1. Planner: Research & file-scope plan (this document) — confirm data shape and acceptance criteria.
2. Orchestrator: Break plan into phases and assign files to agents.
3. Designer: Create visual direction and CSS hooks in the assigned style files.
4. Coder: Implement markup, layout, and minimal data fixtures in `app/`.
5. Coder: Add runnable support (`.vscode/launch.json`) per repo guidance so the preview opens `app/index.html`.
6. Integration & Validation: Designer + Coder validate accessibility, responsiveness, and visual parity.

File Assignments

- `docs/project-pulse-plan.md` — Planner (this file)
- `.github/agents/*` — Orchestrator (coordination only)
- `app/index.html`, `app/styles.css`, `app/scripts.js` — Coder (implementation)
- `app/components/project-card.html` or `app/partials/` — Designer & Coder (visual + markup)
- `.vscode/launch.json` (optional) — Coder (runnable preview)

App file assignments (detailed)

- `app/index.html` — Main dashboard entry point. Renders the project list, header, filters, and placeholders for empty states.
- `app/styles.css` — Core styling, responsive layout, and deterministic CSS hooks such as `.dashboard` and `.project-card`. Designer-owned with Coder integration.
- `app/scripts.js` — Minimal client logic to load fixtures, render project cards, and implement filters and interactions.
- `app/data/projects.json` — Deterministic static fixtures for initial development and validation (fields: `id`, `name`, `status`, `priority`, `owner`, `due_date`, `tags`).
- `app/components/project-card.html` — Markup/template for a single project card (or a JS template in `scripts.js`). Designer + Coder collaborate on structure.
- `app/images/` — Icons and badge assets used by the dashboard.
- `app/vendor/` — Optional third-party assets (normalize/reset, tiny helper libs). Keep vendor files explicit and minimal.
- `.vscode/launch.json` — Launch configuration to open `app/index.html` as a preview (`cwd` set to `${workspaceFolder}/app`).

Ownership notes: Designer focuses on `app/styles.css` and `app/components/*`; Coder owns `app/index.html`, `app/scripts.js`, `app/data/*`, and `.vscode/launch.json`.

Dependencies and Sequencing

- Step 1 (Planner) must complete before Orchestrator phases are assigned.
- Designer and Coder work can run in parallel after the Orchestrator assigns non-overlapping file scopes (e.g., Designer: `app/styles.css`; Coder: `app/index.html`, fixtures).
- `.vscode/launch.json` creation depends on Coder implementing `app/index.html`.

Parallelizable Work

- Designer: visual mockups and CSS scaffolding.
- Coder: static markup and data fixtures.
- Accessibility testing can run in parallel with visual polish.

Edge Cases & Risks

- Unknown data shape from backend — mitigate by using deterministic fixtures and clear data contract in this plan.
- Conflicting file scopes — Orchestrator must explicitly assign file ownership for each phase.
- Browser layout differences — test at common breakpoints and include fallbacks for reduced motion and font-size overrides.

Validation Expectations

- Visual: First view clearly looks like a Project Pulse dashboard with project cards and status badges.
- Accessibility: Color contrast meets WCAG AA for primary UI elements; keyboard focus order is logical.
- Functionality: Filters and priority indicators work with static fixtures; page opens via launch config.
- Tests: Manual checklist and a small smoke test opening `app/index.html` in a browser.

Open Questions

- Do you want real backend integration in this exercise, or should we keep static fixtures and document the API contract for later work?
- Which breakpoints (mobile/tablet/desktop) are highest priority for the initial view?

Next Steps

- Confirm answers to the open questions.
- If confirmed, I can: (A) implement the `app/` scaffold and CSS hooks, or (B) stage/commit/push this plan now.
