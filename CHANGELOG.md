# Changelog

All notable changes to this project are documented here.  
Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [Unreleased]

---

## [1.3.0] – 2026-03-30

### Added
- `feature-builder.agent.md` as a dedicated specialist for new feature implementation
- `bugfixer.agent.md` as a dedicated specialist for root-cause-driven bug fixing
- `test-writer.agent.md` as a dedicated specialist for test and regression coverage
- `PROJECT-WORKSPACE-MEMORY.md` as a local workspace memory file for project-specific context
- `PROJECT-BOOTSTRAP-QUESTIONS.md` as the source of grouped first-run project questions
- `PROMPT-EXAMPLES.md` with practical day-to-day prompt examples for VS Code Copilot use

### Changed
- `dev-expert.agent.md` rewritten into a leaner orchestrator with mandatory first-run bootstrap, local project memory handling, and clearer delegation rules
- `code-reviewer.agent.md` tightened toward practical diff/file review with clearer priorities and less generic phrasing
- `security.agent.md` tightened toward practical auth, secrets, injection, configuration, and dependency risk review
- `README.md` rewritten for Version 1.3.0, including the new agent layout, bootstrap flow, local project memory, and practical prompt usage
- `SETUP-INSTRUCTIONS.md` updated to fully reflect the intentional `dotgithub` / `dotvscode` / `gitignore.txt` packaging model and the expanded agent structure
- `gitignore.txt` updated so `PROJECT-WORKSPACE-MEMORY.md` stays local by default unless explicitly shared
- `dotvscode/settings.json` uses both the main agent instructions and `PROJECT-WORKSPACE-MEMORY.md` as Copilot instruction inputs

---

## [1.2.0] – 2026-03-30

### Added
- `doc-writer.agent.md` — documentation subagent for README, CHANGELOG, JSDoc, and inline comments
- `code-reviewer.agent.md` — code review subagent covering correctness, performance, naming, error handling, and test coverage (BLOCKER/MAJOR/MINOR/NOTE severity model)
- `security.agent.md` — security audit subagent with full OWASP Top 10 checklist, secrets scan, input validation, and dependency audit (CRITICAL/HIGH/MEDIUM/LOW severity model)
- Orchestrator pattern in `dev-expert.agent.md`: `agents:` frontmatter field registers all three subagents; new delegation table and updated workflow

### Changed
- `dev-expert.agent.md` promoted to orchestrator; added subagent delegation section with trigger table and delegation rules
- `.vscode/settings.json` extended with `chat.subagents.allowInvocationsFromSubagents`, `codeGeneration.instructions`, `testGeneration.instructions`, `reviewSelection.instructions`, and `pullRequestDescriptionGeneration.instructions`
- README updated to v1.2.0: new architecture overview table, orchestrator flow diagram, direct subagent usage, context variable reference, extended troubleshooting

---

## [1.1.0] – 2026-03-30

### Added
- `.github/agents/dev-expert.agent.md` — primary agent using the VS Code `.agent.md` format
- Agent frontmatter: `name`, `description`, `argument-hint`, `tools` configuration
- Support for direct agent invocation via `@dev-expert` in Copilot Chat
- Documentation for multi-agent setup (extending with additional `.agent.md` files)

### Changed
- `.github/copilot-instructions.md` repurposed as backwards-compatibility fallback
- README updated to reflect new agent format and VS Code 1.99+ requirement
- Version badge updated to 1.1.0

---

## [1.0.0] – 2026-03-30

### Added
- Initial release of the VS Code Development Expert Agent
- `.github/copilot-instructions.md` — agent prompt with 8 core development principles
- `.vscode/settings.json` — Copilot Agent mode configuration and workspace defaults
- `.vscode/extensions.json` — 17 recommended team extensions
- `README.md` — full English setup guide with badges, troubleshooting, and customization
- `CHANGELOG.md` — this file
- `LICENSE` — MIT License with explicit "use at your own risk" clause
- `.gitignore`
- Conventional Commits as the mandatory commit format
- Semantic Versioning (Major.Minor.Patch) as the project-wide standard
- 8-step workflow: Understand → Analyze → Backup → Implement → Test → Document → Commit → Report
