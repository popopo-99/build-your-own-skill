# AGENTS.md

## Project Goal

Build Your Own Skill helps people turn professional experience, tacit knowledge, workflows, failure lessons, and quality standards into reusable, testable AI Skills. The product must remain usable by people who do not code.

Its first identity is a working Skill that helps people build Skills. Documentation supports that product; it does not replace it.

## Repository Boundary

This repository is:

`popopo-99/build-your-own-skill`

Never write to:

`popopo-99/zy-cinematic-realism`

Never modify, move, rename, or delete files outside the current repository root. Material in another repository may be treated only as read-only reference when the user authorizes it.

Before editing, verify the repository root, remote, branch, status, and existing files. Stop if the remote is not `popopo-99/build-your-own-skill`.

## Architecture Principles

- Keep `SKILL.md` concise and focused on orchestration.
- Move substantial conditional knowledge into focused references.
- Link every reference from a clear reading condition; do not duplicate rules across files.
- Use the minimum necessary architecture.
- Do not introduce Router, scripts, tools, APIs, databases, frontends, or build systems without a demonstrated use case.
- Do not require code for a basic Skill.
- Treat templates and examples as teaching aids, not universal defaults.

## Product & Editing Rules

- Preserve Discovery as the default for vague ideas; do not immediately generate `SKILL.md`.
- Infer information from the conversation before asking users.
- Ask only 1–3 high-value questions at a time; do not create a rigid questionnaire.
- Extract the user's real workflow and tacit decisions rather than inventing a professional-sounding process.
- Prefer one clear V0.1 problem over a universal Skill.
- Separate Hard Constraints from Preferences.
- Define observable outputs, checks, and repair behavior.
- Preserve beginner usability and adapt depth for expert users.
- If a user provides an existing Skill, diagnose and make the minimum justified change.
- Do not change behavior without considering affected tests.
- Keep the primary user documentation Chinese-first. Introduce technical terms as Chinese plus English on first use when helpful.
- Avoid unnecessary repetition across `README.md`, `SKILL.md`, and references.

## Testing

- Cover standard, minimal, missing, conflicting, bad-input, beginner, expert, modification, failure, and long-context behavior as appropriate.
- Test Trigger, Routing, Instruction Following, Quality, Consistency, Constraints, Output, and Repair.
- Validate frontmatter and relative links when a compatible local validator is available.
- Do not install unknown dependencies or modify the global environment only for validation.
- Inspect the full `git diff`, diff summary, and `git status` before completion.

## Git Safety

- Do not commit, push, force push, delete branches, create releases, or change repository visibility unless the user explicitly asks.
- Preserve unrelated user changes and report any overlap or conflict.
- Confirm that all changed files are inside this repository.

## License Safety

- Do not add, remove, select, or modify a License automatically.
- If no License exists, report that the project author must decide.
- For derived work, inspect the source License, preserve required attribution, and describe modifications without making unsupported legal conclusions.
