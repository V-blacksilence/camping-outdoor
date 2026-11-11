# AGENTS.md — Camping & Outdoor Vietnam

> Project-level operating rules for Google Antigravity. This file is continuously active. Keep it concise; place detailed specifications in `docs/` and task procedures in `.agents/skills/`.

## 1. Mission and product boundaries

Build a maintainable, mobile-first Camping & Outdoor product for Vietnam, supporting Android and iOS from the beginning, with Vietnamese and English localization.

Product pillars:
- **Explore & Plan:** verified outdoor/camping places, map discovery, filters, place profiles, reviews, trip planning and practical trip information.
- **Community & Connect:** contributions, reviews, groups and events. Add social features only after core discovery and commercial demand are validated.

Priority order:
1. Validate a credible early revenue path.
2. Deliver a narrow, useful MVP.
3. Establish reliable place, access and permission data.
4. Acquire and retain initial users.
5. Grow community and expand the outdoor ecosystem.

Geographic focus: Northern Vietnam first. Consider Southern Vietnam only after documented supply and demand research shows a material Northern Vietnam gap. Do not assume a destination is a legal campsite because it is popular for sightseeing.

## 2. Mandatory human approval gates

AI agents are assistants, not project owners. The project owner retains final authority.

### Agents may do without approval
- Inspect repository files and project configuration.
- Read documentation and research public information.
- Analyze requirements, risks, costs and alternatives.
- Draft plans, documentation, wireframes, tests and proposed code diffs.
- Run non-destructive local checks that do not install dependencies or alter project state.

### Explicit approval is required before
- Creating or changing major architecture or core technology choices.
- Installing/upgrading significant dependencies or changing lockfiles.
- Creating, deleting, moving, overwriting or bulk-editing important files.
- Database schema changes, migrations, seed-data changes or destructive queries.
- Authentication, authorization, privacy, security or permissions changes.
- Enabling paid services, paid APIs, billing, subscriptions or purchases.
- Sending external messages, publishing, deploying, releasing or submitting apps.
- Accessing, exporting, exposing or processing sensitive user data.
- Any action with external side effects or irreversible consequences.

### Approval protocol
For every gated task:
1. **ANALYZE** — inspect relevant files, state and constraints.
2. **PLAN** — state objective, exact files/systems affected, alternatives, risks, dependencies, cost and rollback.
3. **PRESENT** — show the proposed diff or implementation plan and verification steps.
4. **WAIT** — stop. Do not execute until the owner gives explicit approval for that specific scope.
5. **IMPLEMENT** — do only the approved work. If scope changes, stop and request approval again.
6. **TEST** — run relevant checks and report actual results.
7. **REVIEW** — inspect the diff, security implications and regressions.
8. **REPORT** — list changed files, tests, known limitations and next decision.

A request to research, explain, plan, review or propose is not implementation permission. Approval for one task is not approval for another. Silence, ambiguous wording, or a previous approval is not approval.

## 3. First-run and repository discipline

Before making changes:
- Inspect the repository tree, Git status, existing README, package manifests, lockfiles, tests, environment templates and current architecture.
- Identify the actual Antigravity surface/version (App, CLI or IDE) and verify applicable documentation.
- Identify existing conventions and preserve them unless a change is approved.
- Report missing repository access or missing context; never pretend an inspection occurred.
- Do not overwrite existing instructions. Reconcile conflicts and ask the owner where necessary.

Do not start full application development during project setup. The first phase is research, documentation and recommendations only. Stop after presenting findings and wait for approval.

## 4. Antigravity configuration conventions

Use documented Antigravity mechanisms only; do not invent agent configuration files or orchestration features.

- Workspace instructions: root `AGENTS.md` (or documented `GEMINI.md` alternative). Keep this file concise and always relevant.
- Modular rules: `.agents/rules/*.md`. Each rule file must use valid YAML frontmatter with a supported `trigger` (`always_on`, `model_decision`, `glob`, or `manual`); include required `description`, and `globs` for `glob`.
- Skills: `.agents/skills/<skill-name>/SKILL.md`, with YAML frontmatter containing a clear `description`. Use focused skills for repeatable multi-step procedures and progressive disclosure.
- Legacy Workflows are deprecated in current Antigravity documentation. Prefer Agent Skills for new reusable procedures; migrate old workflows only after inspecting them and obtaining approval if files will change.
- Use subagents/parallel agents only where the installed Antigravity surface supports them. Treat role names in project documentation as logical responsibilities, not proof that separate autonomous agents are configured.
- Do not create `.agents/`, skill bundles, hooks, MCP configuration or agent definitions until repository inspection and an approved setup plan.

## 5. Logical agent responsibilities

Delegate only when the installed environment supports it and the task benefits from delegation. All agents inherit the approval policy above.

| Role | Responsibility |
|---|---|
| Project Manager | Scope, dependencies, milestones, decision tracking |
| Product Manager | User needs, requirements, user stories, acceptance criteria |
| Market Research | Customer discovery, competitor and partner research |
| UX/UI | Mobile flows, design system, accessibility, localization |
| Software Architect | Stack evaluation, architecture, API and data boundaries |
| Mobile Developer | Android/iOS client, navigation, state, device integrations |
| Backend Developer | API, auth, database, business logic, notifications |
| AI Developer | Optional recommendation and planning features; evaluate cost and reliability |
| Data Agent | Place provenance, validation, duplicates, freshness and confidence |
| QA Agent | Unit, integration, device, regression and security testing |
| Business & Growth | Partner validation, revenue experiments, acquisition and retention |

Agents must communicate assumptions, evidence, unresolved questions and proposed handoffs. No agent may approve its own gated changes.

## 6. Product and MVP principles

Build for a focused first release; do not implement the full product vision at once.

**MVP candidate scope (subject to product-owner approval):**
- Account/authentication with minimal data collection.
- Search and map-based discovery.
- Place detail pages and filters.
- Save/favorite places.
- Admin review and place-data management.
- Contact/booking redirection to verified operators.

**Later, after validation:** trip planning, cost estimates, user reviews, place contributions and basic weather information.

**Future:** AI recommendations, groups, companion matching, advanced social feed, offline maps and premium ecosystem.

For each feature, define target user, problem, measurable outcome, dependencies, privacy/safety implications, acceptance criteria and an explicit MVP priority. Prefer partner lead generation or booking referrals as an early revenue experiment before building complex payment infrastructure.

## 7. Place data, legality and safety

Never fabricate places, coordinates, prices, facilities, access conditions, operator details, reviews or legal status.

Every place record should support:
- Stable ID, name, category and coordinates.
- Access route and access restrictions, where verified.
- Facilities and available services.
- Price range, currency and source, with date checked.
- Permission/legal status and the authority/operator evidence supporting it.
- Data source, source URL/reference, verifier, last-verified timestamp and confidence.
- Status lifecycle: `unverified`, `pending_review`, `verified`, `restricted`, `closed`, `rejected`.

Do not label a place “legal”, “safe”, “open” or “available” based only on user posts, popularity, map presence or AI inference. Require human verification from the landowner/operator or relevant authority for permission and current access. Clearly show uncertainty and last verification date. Provide report, correction, moderation and takedown paths.

Protect exact private locations, user location history and personal information. Request device permissions only when needed, explain the purpose, minimize retention and provide graceful alternatives when permission is denied.

Outdoor safety is a product requirement: show operator/authority contacts and verified restrictions where available; do not encourage trespassing, unsafe routes, risky challenges or unsupervised meetups. Design age-appropriate community protections, moderation, reporting and privacy controls. Do not enable direct stranger meetups involving minors.

## 8. Mobile engineering standards

- Design and test Android and iOS from the beginning; use a shared codebase where appropriate.
- Evaluate React Native + Expo against Flutter before selecting. No stack is approved by this file.
- Treat maps, geocoding, routing, weather, push notifications, storage and analytics as vendor decisions requiring cost, terms, privacy and lock-in review.
- Handle denied permissions, weak/no network, slow devices, interrupted uploads and stale cached data.
- Support Vietnamese and English using a real localization system; do not hardcode user-facing strings.
- Use accessible typography, touch targets, loading/empty/error states and clear permission explanations.
- Keep secrets out of source control and client bundles. Validate inputs on both client and server.
- Separate development, staging and production environments.
- Add tests for business rules, permissions, location-data quality, API failures and critical user journeys.
- Do not claim offline maps or background location work until tested on physical Android and iOS devices.

## 9. Architecture and code quality

- Inspect before choosing patterns; prefer the smallest architecture that meets validated needs.
- Keep UI, domain logic, data access and external providers separated.
- Use typed contracts and runtime validation at trust boundaries.
- Avoid unnecessary dependencies and premature microservices.
- Document significant decisions in `docs/DECISION_LOG.md` using context, options, decision, consequences, owner and date.
- Keep migrations reversible where practical; require approval and backups for destructive operations.
- Never use production credentials or real personal data in development tests.
- Never invent test results, production data or completed work.

## 10. Security, privacy and moderation

Threat-model authentication, authorization, location data, uploads, user-generated content, admin access and partner integrations before release.

Apply least privilege, secure session handling, server-side authorization, rate limits, abuse reporting, moderation queues, audit logs for admin actions and safe file-upload validation. Do not expose service-role keys or privileged credentials to mobile clients. Define retention and deletion behavior before collecting sensitive location history.

## 11. Commercial validation

Prioritize evidence over assumptions. Test partner interest and willingness to pay before building monetization infrastructure.

Evaluate, without presuming viability:
- Referral/booking commissions.
- Paid, clearly labelled operator promotion.
- Qualified partner leads.
- Trip-planning services.
- Premium features after repeat usage is demonstrated.
- Outdoor brand partnerships.

For each experiment, define customer segment, value proposition, partner/user evidence, conversion metric, cost, operational burden and stop/continue threshold. Clearly distinguish signed partners, contacted prospects and speculative leads.

## 12. Documentation map

Keep detailed content outside this file. Create only documents with meaningful, evidence-backed content.

Recommended:
- `README.md` — project purpose, setup and current status.
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/PRODUCT_ROADMAP.md`
- `docs/MARKET_RESEARCH.md`
- `docs/TECH_STACK_DECISION.md`
- `docs/ARCHITECTURE.md`
- `docs/DATABASE_SCHEMA.md`
- `docs/API_SPECIFICATION.md`
- `docs/DESIGN_SYSTEM.md`
- `docs/AI_AGENT_WORKFLOW.md`
- `docs/SECURITY.md`
- `docs/TESTING.md`
- `docs/DECISION_LOG.md`
- `docs/BUSINESS_MODEL.md`
- `agent-instructions/` — only if separate role-specific instructions are needed.
- `.agents/skills/` — only for verified, reusable multi-step procedures.

Do not create empty placeholders or duplicate this file across multiple locations.

## 13. Required task report

For every completed implementation task, report:
- Requested scope and approval reference.
- Files created, modified and deleted.
- Important decisions and assumptions.
- Commands/tests actually run and their results.
- Security, data, cost and operational implications.
- Known defects, unresolved questions and rollback considerations.
- Recommended next task.

## 14. Definition of done for project setup

Project setup is not complete until repository and Antigravity configuration have been inspected; instruction conventions verified; the owner has reviewed the technology and architecture recommendation; MVP boundaries and approval gates are documented; and the owner has accepted the setup.

Until that acceptance, do not scaffold or implement the application.

**Final principle:** AI agents may research, propose and execute approved work. The human project owner retains control of product direction, architecture, data, security, spending, releases and deployment.
