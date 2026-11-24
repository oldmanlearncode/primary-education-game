# 11 — Global UX Rule: Minimize Unexpected Layout Shift

> **GLOBAL UX RULE — CONFIRMED (D-062, 2026-11-24)**  
> Applies to **the entire Little Explorers product**: Child World, Parent Portal, Admin Portal, all components, overlays, loading states, responsive layouts and future features.  
> User's direction: **“Tôi muốn toàn bộ dự án áp dụng rule tránh Layout Shift, giải pháp có thể tuỳ tình huống. nhưng luôn luôn cố gắng tránh Layout Shift.”**

## 1. Objective and boundaries

**Always proactively minimize unexpected layout shifts.** No single implementation technique is mandatory. Select context-appropriate solutions based on screen purpose, accessibility, responsive constraints and technical feasibility.

- **Unexpected jumps are defects to prevent and review**, particularly those that move a target during interaction or cause accidental selection.
- **Intentional, user-initiated reflow** is allowed when necessary (expand/collapse, responsive resizing, user-adjusted text size, opening meaningful sections). Make transitions comprehensible and preserve focus.
- Avoid sacrificing readability, responsive behavior, localization or accessibility solely to force a fixed pixel dimension.
- Apply the principle during **UX design, front-end implementation, code review, QA and regression testing**, not only to mockups.

## 2. Design checklist for all product areas

| Situation | Typical mitigation (select as appropriate) |
|---|---|
| Table action label changes (e.g. Xem → Đang xem) | Fixed-size icon button; stable accessible label/tooltip; highlight row via background/inset decoration; reserve width |
| Table cells/status badges change | Predictable column widths (`table-layout: fixed` with colgroup when useful), ellipsis/truncation + full value access, responsive horizontal scroll |
| Async list/table data | Size-preserving skeleton, stable table header/rows or minimum-height loading region; avoid replacing small spinner with large content abruptly |
| Images and media | Known `width`/`height`, `aspect-ratio`, placeholders; avoid loading unbounded elements into document flow |
| Fonts / localization | Suitable fallback metrics and explicit text container strategy; test longer translations, text zoom and slow-font loading |
| Validation / error messages | Reserved or predictably sized error region; avoid pushing submit targets unexpectedly |
| Buttons, tabs, pagination, counters | Constant hit-target dimensions, avoid changing button labels' length if possible; use status region separate from controls |
| Expandable panels, tooltips, menus, dialogs | Popover/overlay when appropriate; intentional accessible expansion where necessary; avoid overlays changing the document flow unexpectedly |
| Notifications and banners | Overlay/toast or reserved banner slot; avoid unexpectedly pushing active content down |
| Child game feedback and animations | Prefer `transform`/`opacity` for visual movement; preserve target positions during play; avoid mis-taps |
| Parent progress dashboard charts | Reserve chart dimensions and axes/legend space while awaiting data; preserve card sizes |
| Mobile/responsive layout | Predictable breakpoints; deliberate, accessible reflow; avoid clipping important content or text |

**Note:** `table-layout:fixed` is an option, **not a universal rule**. Tables must remain readable and scrollable when narrow.

## 3. Acceptance criteria (apply per change)

1. Switching selected/active/disabled/loading/error state must not unexpectedly resize neighboring controls or table columns.
2. Navigating or selecting a row must not move another click target beneath the pointer/keyboard focus.
3. Async data, fonts and images should have predictable reserved space wherever practicable.
4. All applicable layouts must be reviewed on desktop and mobile/tablet sizes, long emails/localized text, browser text zoom and slow loading.
5. In implementation, monitor actual **Cumulative Layout Shift (CLS)** when meaningful. Use Web Vitals/Performance tools where feasible. Distinguish user-initiated intentional changes from unexpected shifts. Numeric performance budgets are **OPEN** until a dedicated performance review; do not assert a universal zero-shift threshold.
6. Any intentionally accepted shift should be documented with rationale, user benefit, accessibility considerations and alternative explored.

## 4. AW-21 — Admin tables (specific confirmed application)

**AW-21 CONFIRMED:** A-07 replaces text toggle `Xem` → `Đang xem` with a **constant-size SVG Eye icon**, accessible `aria-label` and tooltip; selection shown via row highlight, not lengthening label. Stable column sizing and responsive overflow are required. Apply the same interaction pattern to A-03 and future admin data tables when appropriate.

**HTML demo updates (2026-11-24):**
- `A-07-invitation-management.html`: 38×38 px SVG Eye button, `aria-pressed`, row highlight, stable colgroup + fixed table layout, horizontal scroll at narrow widths.
- `A-03-parent-account-list.html`: 38×38 px SVG Eye button, stable colgroup + fixed table layout.
- These are **standalone HTML UX demos only** and are not product/backend code. They should be used as references when Figma/frontend implementation resumes.

## 5. Governance

- **Decision ID:** D-062 / UX-GLOBAL-01 (global minimize unexpected Layout Shift rule) and AW-21 (Admin table specific).
- **CONFIRMED by user:** 2026-11-24.
- **Applies to:** all screens; not contingent upon the approval status of individual wireframes.
- **A-07 AW-17…AW-20 remain PROPOSED** until explicitly reviewed; this decision confirms **AW-21**, not those unrelated proposals.
- Update/review this guidance whenever new UI patterns are introduced. A screen can be approved at wireframe level without declaring all CLS testing passed; verify during implementation.

Cross-references: [A-07 Invitation Management](./10-admin-invitation-management-wireframe.md), [A-03 Parent Account List](./07-admin-parent-account-list-wireframe.md), [Decision Log](../idea-summarize/06-decisions-and-open-questions.md).
