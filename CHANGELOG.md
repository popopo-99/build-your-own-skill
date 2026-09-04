# Changelog

All notable changes to this project will be documented in this file.

## V0.2.0 — 2026-09-04

### Added

- Strict Write Gate.
- Knowledge Provenance:
  - USER-DERIVED
  - INFERRED
  - PROPOSED
- Behavioral tests for ambiguous Build authorization.
- Behavioral test preventing AI suggestions from being presented as user-derived knowledge.

### Changed

- Discovery / Design / Review now remain read/design-only until explicit Build authorization.
- Ambiguous responses such as “继续 / 好 / 可以 / 下一步” no longer authorize file writes.
- Important inferred or proposed rules must disclose their source before becoming core Workflow, Hard Constraints, Router logic, or important quality standards.
- Updated existing behavioral test wording to remove ambiguous Build authorization.

## V0.1.0 — 2026-09-04

Initial testable release of Build Your Own Skill.

### Added

- Core Skill Builder architecture and stage-aware entry flow.
- Discovery system for repeated problems and tacit knowledge extraction.
- Scope definition, Skill Statement, and Skill Canvas guidance.
- Workflow and professional knowledge extraction methods.
- Minimum necessary architecture and progressive disclosure guidance.
- Testing, self-check, repair, and Skill Doctor guidance.
- Beginner-ready Skill Canvas, basic Skill, and publishing templates.
- `brand-visual-director` teaching example.
- Behavioral test cases for beginner, expert, import, review, failure, and overengineering scenarios.
- Chinese-first README and long-term repository maintenance rules.
