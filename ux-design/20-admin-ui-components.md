# 20 — AP-F02 Admin UI Components
2026-11-27 · **Component baseline DRAFT / awaiting review**, following confirmed AFR-D01…04. No approved screens replaced.
## Deliverables
Conversation artifacts AP-F02-showcase.html (standalone) and AP-F02-admin-ui-components.zip (index.html, shared/styles.css, shared/components.js, showcase.js). Prototype only, no framework commitment or backend.
## Patterns
- Shell, sidebar, header, card/detail panel.
- Search/filter/reset, paginated table with fixed colgroup, 38px Eye icon, selected row background and accessible labels.
- Separate account/token/delivery badges; SENT does not imply activation.
- Reserved feedback region, loading skeleton, empty/error/denied/partial-success states.
- Native modal confirmation with reason and acknowledgment; warning visible before decision. MFA and authorization not implemented here.
- Progressive disclosure: report history hidden until opened, nested event detail, six-item audit preview and full searchable paginated audit.
- All fixtures in memory, no secrets or real account modifications.
## QA
Node syntax check passed both JS files. Browser regression, actual CLS and accessibility audit remain pending AP-F05. Showcase uses illustrative fixture data, colors, dimensions and Vietnamese labels, not final visual design. Full A-12 filters and policy constraints remain in approved screen specifications, not replaced by simplified showcase.
## Next
Review component baseline, then AP-F03 login states and role dashboard variants; integration of all screens/shared data AP-F04; QA AP-F05, documentation AP-F06, Figma AP-F07, acceptance AP-F08.