# 17 — A-12 Content Quality Operations: UX Wireframe

> **2026-11-27 · HTML LOW-FI DRAFT / AWAITING REVIEW**  
> Standalone interactive demo: `A-12-content-quality-operations.html` attached in conversation. **No Figma A-12 frame**, no real review backend, notification service or learning-evidence updates. **A-12 remains FUTURE / scope review**, not automatically included in MVP.

## 1. Confirmed decisions reused

- **D-011 / EC-03:** When an already-used question is confirmed incorrect, correct and notify as needed, revisit affected results, support the case where **many questions were wrong**. Detailed severity, quarantine/triage criteria remain OPEN.
- **D-045 / ADM-05:** Account administration and educational-content review must have distinct permissions.
- **D-046 / ADM-D01:** Initial roles: `SUPER_ADMIN`, `ACCOUNT_ADMIN`, `CONTENT_REVIEWER`, `SUPPORT_OPERATOR`.
- **D-051 Permission Matrix:** `CONTENT_REVIEWER` can triage/review and approve content; `ACCOUNT_ADMIN` cannot. `SUPER_ADMIN` may triage/approve only after conditional `🔒` policy, not automatically; `SUPPORT_OPERATOR` may triage only under `🔒`, not approve.
- **AD-08/AD-09:** Enforcement of resource scope/ticket constraints, no review of content outside scope. Child learning record access separately governed by `🔒`; **no direct editing of raw attempts or mastery by any Admin role**.
- **D-062:** Prevent unexpected Layout Shift across child/parent/admin.
- Parent reporting and content correction are cross-portal UX flows; **P-13 Question Report Status & Correction** remains separate and not designed in A-12.

## 2. Proposed A-12 flow

```text
Parent reports question (P-13; future detailed wireframe)
  ↓
A-12 Question Reports queue (role/scope filtering)
  ↓
Content Reviewer selects report
  ↓
Triage (question/version, curriculum, answer, explanation, provenance)
  ↓
Suspected harmful/incorrect question → quarantine for future sessions
  ↓
Review and propose corrected question/version
  ↓
Impact assessment (linked sessions; aggregate preview; no raw child data by default)
  ↓
Separate approved correction workflow for learning evidence
  ├─ re-evaluate affected outcomes without overwriting raw attempts/mastery
  ├─ protect existing rewards and avoid punishing children for system error
  ├─ notify parents, with notice/correction history
  └─ audit affected question/content/result versions
  ↓
Close report after approval and verification
```

**Critical boundary:** The demo only changes the *report status in memory*. It does **not** version real questions, quarantine content production-wide, recompute results, alter child data, or send parents messages. `RESOLVED` in demo is not proof of completed backend correction workflow.

## 3. Wireframe regions

- Header and in-scope counts: reports, new/triaged, high-severity, resolved.
- Search/filter toolbar: report ID, question ID, topic, subject, severity, review status.
- Stable-column Question Reports table with fixed-size 38×38 Eye icon, selected row highlighting and overflow scrolling.
- Selected report details: question, answer, expected answer, source (AI vs bank), issue, severity, status, **aggregate estimated related sessions**.
- Actions with reason and acknowledgement: **Triage / Quarantine / Propose Correction / Resolve**; review actions only for authorized reviewer.
- Scoped audit preview; simulated role/scope/event lab; explicit authorization and conflict/unknown-network messages.
- Example question reports for multiplication, Vietnamese and Natural & Social Science; no child names, raw attempts or sensitive mastery.
- UX stability rule D-062 applies to buttons/table/feedback/dialog.

## 4. Demonstration scenarios

| Condition | Behavior |
|---|---|
| Content Reviewer assigned to Math | Triage, quarantine, propose correction for Math within scope |
| Content Reviewer scoped to all | Can review all demo subjects |
| Account Admin | No content review or approval |
| Super Admin with conditional scope | Demonstrated only with deliberately enabled `all` sample scope; not general grant |
| Support Operator | Mock read-only triage view under ticket-limited scope, **not an authorization policy** |
| Privilege revoked / scope denied | Hide counts, list and details; disable modifications |
| Concurrent update | Explicit 409 Conflict; reload before retry |
| Network result uncertain | Query authoritative state before retry; do not create duplicate corrections |
| Multiple wrong questions | Block single-question correction and require batch impact assessment concept |
| High severity report | Visible risk marker; quarantine workflow available when reviewer authorized |
| Correction pending | Cannot directly edit raw attempts/mastery; only advance mock report state |
| Empty/search no match | Clear no-results state and stable layout |

## 5. Proposals for review — NOT CONFIRMED

| ID | Proposal | Status |
|---|---|---|
| **AW-42** | A-12 layout: permission-aware question-report queue, filters, selected report review detail, aggregated impact and audit preview. | **PROPOSED** |
| **AW-43** | Review progression `NEW → TRIAGED → QUARANTINED / CORRECTION_PENDING → RESOLVED`, with separate safety quarantine and explicit professional review. Exact backend state machine OPEN. | **PROPOSED** |
| **AW-44** | Before closing a confirmed content defect, require **impact assessment and correction workflow** for already-used questions; keep raw learning evidence immutable, calculate amendments in a separate auditable process and notify parents as appropriate. | **PROPOSED UX**, EC-03 principle CONFIRMED |
| **AW-45** | Context-specific role/scope controls, mandatory reason/acknowledgement, bulk-error escalation, conflict/network/permission states and Layout Shift minimization. | **PROPOSED UX**, underlying security/layout principles CONFIRMED |

## 6. Open questions — do not silently close

- Is A-12 in MVP, later phase, or a separate Content Review Console?
- Which questions (including AI-generated) require pre-publication review? Curriculum approval/version, source provenance and explanation standards?
- How to define severity, quarantine rules, escalation SLA, reviewer-of-own-change separation and policy for many incorrect questions at once?
- Exact correction algorithm for affected learning evidence/mastery/rewards/spaced repetition; parent notification frequency and message policy.
- Exact `🔒` authorization policies for Super Admin and Support Operator; scope handling, which metadata may be viewed without child-data permission.
- Content event versions, immutable audit, before/after diff and incident linking.
- How P-13 Parent Question Report Status & Correction joins the lifecycle; this wireframe does not replace P-13.
- Accessibility, production responsive QA, measured CLS, actual API/backend implementation and Figma frame.

## 7. Current progress and approval boundary

- **A-01…A-11:** low-fidelity UX approved (Figma A-01/A-02; other HTML low-fi).
- **A-12:** HTML interactive low-fi **DRAFT / NEEDS REVIEW**, AW-42…AW-45 PROPOSED.
- Completing A-12 review will complete the **current 12-screen Admin Portal inventory at low-fi level**, **not** the full product UX phase or all outstanding technical decisions.
- No Figma frame for A-12 and no functional content-moderation backend delivered.

Links: [Admin Portal & Permission Matrix](./04-admin-portal.md), [Screen Inventory](./03-screen-inventory.md), [A-10 Audit](./15-admin-audit-history-wireframe.md), [Global Layout Stability](./11-global-layout-stability-guidelines.md), [Decision Log](../idea-summarize/06-decisions-and-open-questions.md).


## 8. Reviewer feedback and UX V2 correction (2026-11-27) — DRAFT, NOT YET APPROVED

**Feedback:** User asked why no visible step to fix wrong answer, e.g. `2 × 4 = ?` has saved answer `6` but correct answer `8`, and what distinguishes **Triage** from **Quarantine**. This is a **request for design correction and explanation**, **not approval** of A-12 or AW-42…AW-45.

### Triage vs quarantine: two independent concerns

- **Triage** = inspect/verify a reported defect, classify impact, severity, ownership, and next step. A question can remain under review; triage itself does not change the question or stop serving it.
- **Quarantine** = make a risky question/version ineligible for **new sessions**. Quarantine is a protective serving-policy action, not a fix or evidence reassessment. It may be initiated before complete triage when clearly unsafe/wrong; must be authorized and audited. Already-started/offline sessions require an additional content-policy mechanism (OPEN).
- Production should **not conflate workflow and serving status**: recommended separate `review_status` from `serving_status`, rather than a single ambiguous status field. Earlier low-fi states `NEW/TRIAGED/QUARANTINED/CORRECTION_PENDING/RESOLVED` are illustrative, not final backend schema.

### A-12 V2 correction editor and separate impact step

The updated standalone HTML `A-12-content-quality-operations-v2.html` is now linked in the conversation. The local flow illustrates:

1. **Triage** and optionally **Quarantine** original `questionId=Q-MUL-0021` v1, stored answer `6`.
2. **Propose Correction** with explicit editable **correct answer `8`** and **explanation `2 × 4 = 8`**, saved as an **in-memory proposed v2** without overwriting v1.
3. **Assess learning impact** separately: show the estimated 37 related sessions, create an *in-memory mock amendment preview*. The preview does not contain per-child scores and is not a computed grade adjustment.
4. **Approve/close content review** only after the proposed correction and impact preview exist. Closing in demo represents an updated **mock content version only**; it does **not** publish to real sessions, recalculate grades/mastery, grant/withdraw rewards, or notify parents.

**Required real system flow not implemented in HTML:** create immutable versioned correction; find actual affected attempts by question version; re-evaluate original answers with verified new answer; build proposed learning-evidence amendments (with version links, provenance, reason, approval); decide impacts to mastery/spaced repetition/rewards; notify parents; audit and retry idempotently; handle multiple wrong questions via incident/batch workflow. The original attempts and old grading evidence remain unchanged. Correction of displayed answer and correction of historical results are **two distinct workflows**.

### Additional V2 design proposal — NOT CONFIRMED

- **AW-46 (PROPOSED):** A-12 must have an explicit correction editor (old/new answer and explanation, immutable new question version) **and** a distinct post-correction impact-assessment/amendment-approval step before a confirmed defect can be fully resolved. Quarantine/triage must be described separately; production should track review and serving states independently. User feedback identified this omission; the detailed solution remains pending user approval.

The V2 demo is **UX-only**, no real learning-outcome recalculation. **AW-42…AW-45 and AW-46 remain PROPOSED; A-12 remains DRAFT / NOT APPROVED**.
