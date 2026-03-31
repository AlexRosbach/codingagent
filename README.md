# VS Code Development Expert Agent

![Version](https://img.shields.io/badge/version-1.3.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![VS Code](https://img.shields.io/badge/VS%20Code-1.99%2B-007ACC?logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-required-black?logo=github)

Version **1.3.0** is a more practical multi-agent template for GitHub Copilot in VS Code.
It keeps the intentional packaging style (`dotgithub`, `dotvscode`, `gitignore.txt`), adds first-run project bootstrap with local workspace memory, and expands the agent system with dedicated roles for features, bugfixes, and tests.

The goal is simple:
**less generic Copilot behavior, more project-aware support with less repetitive prompting.**

> **Use at your own risk.** No warranties, no guarantees. See [LICENSE](./LICENSE).

---

## What is new in 1.3.0

### Major improvements
- `dev-expert` was rewritten to be **leaner and more practical**
- first-run **project bootstrap questions** are now mandatory
- answers are stored in a local memory file: `PROJECT-WORKSPACE-MEMORY.md`
- three new specialist agents were added:
  - `feature-builder`
  - `bugfixer`
  - `test-writer`
- `code-reviewer` and `security` were tightened to be more practical and less generic
- setup/docs were updated to fully match the intentional `dotgithub` / `dotvscode` / `gitignore.txt` packaging model
- new helper docs were added:
  - `PROJECT-BOOTSTRAP-QUESTIONS.md`
  - `PROMPT-EXAMPLES.md`

### Why this version is better
This version is designed to use more of Copilot's practical potential in VS Code:
- one-time project context capture
- reusable local project memory
- stronger role separation
- clearer day-to-day prompt patterns
- less overgrown orchestrator behavior

---

## Agent system

| Agent | Invocation | Responsibility |
|---|---|---|
| `@dev-expert` | Main entry point | Lean orchestrator, first-run bootstrap, task routing |
| `@feature-builder` | Direct or delegated | New feature implementation |
| `@bugfixer` | Direct or delegated | Root-cause bug fixing |
| `@test-writer` | Direct or delegated | Tests and regression coverage |
| `@doc-writer` | Direct or delegated | README, CHANGELOG, JSDoc, inline docs |
| `@code-reviewer` | Direct or delegated | Correctness, maintainability, performance, test gaps |
| `@security` | Direct or delegated | Auth, secrets, injection, config, dependency risk |

### Typical flow
```text
User: @dev-expert Add a password reset flow

1. dev-expert checks project memory
2. if first run: asks grouped bootstrap questions once
3. stores the confirmed answers locally
4. delegates implementation to feature-builder
5. delegates tests to test-writer if needed
6. delegates review/security/docs when useful
7. returns a practical summary
```

---

## Important packaging note

This repository intentionally uses:
- `dotgithub`
- `dotvscode`
- `gitignore.txt`

instead of real dot names.

That is **intentional** and kept on purpose.
It makes packaging, upload, reuse, and copying easier.

Before using the template in a real project, rename them to:
- `.github`
- `.vscode`
- `.gitignore`

See [SETUP-INSTRUCTIONS.md](./SETUP-INSTRUCTIONS.md).

---

## Requirements

- VS Code 1.99+
- GitHub Copilot subscription (Individual or Business)
- Git 2.x

---

## Files included

```text
repo-root/
├── dotgithub/
│   └── agents/
│       ├── dev-expert.agent.md
│       ├── feature-builder.agent.md
│       ├── bugfixer.agent.md
│       ├── test-writer.agent.md
│       ├── doc-writer.agent.md
│       ├── code-reviewer.agent.md
│       └── security.agent.md
├── dotvscode/
│   ├── settings.json
│   └── extensions.json
├── gitignore.txt
├── PROJECT-WORKSPACE-MEMORY.md
├── PROJECT-BOOTSTRAP-QUESTIONS.md
├── PROMPT-EXAMPLES.md
├── README.md
├── CHANGELOG.md
└── LICENSE
```

---

## First-run bootstrap behavior

On the first meaningful `@dev-expert` call, the agent should:
1. check whether `PROJECT-WORKSPACE-MEMORY.md` is missing or incomplete
2. read `PROJECT-BOOTSTRAP-QUESTIONS.md`
3. ask a short grouped question set
4. write confirmed answers into `PROJECT-WORKSPACE-MEMORY.md`
5. reuse that memory on later tasks instead of re-asking baseline project questions

### The bootstrap should capture
- stack and runtime
- install / dev / build / test / lint commands
- important folders and entrypoints
- architecture rules
- coding / naming / docs / testing preferences
- security and deployment constraints
- definition of done

### What the bootstrap should not do
- ask the same baseline project questions every time
- invent facts and store them as if confirmed
- produce a huge interrogation

---

## Setup

### Existing project
1. Copy this package into your project root.
2. Rename:
   - `dotgithub` → `.github`
   - `dotvscode` → `.vscode`
   - `gitignore.txt` → `.gitignore`
3. Open the project in VS Code.
4. Install recommended extensions.
5. Open Copilot Chat.
6. Start with `@dev-expert`.
7. Answer the bootstrap questions once.
8. Let the agent keep that context in `PROJECT-WORKSPACE-MEMORY.md`.

### New project
Same process. This package is designed to be reusable as a practical starter template.

---

## Best prompt patterns

See [PROMPT-EXAMPLES.md](./PROMPT-EXAMPLES.md).

Quick examples:

### First run
```text
@dev-expert Help me bootstrap this project for future work.
```

### Build a feature
```text
@dev-expert #codebase Add a password reset flow that matches the existing API style.
```

### Fix a bug
```text
@bugfixer #problems #terminalLastCommand Fix the failing login timeout behavior.
```

### Write tests
```text
@test-writer #changes Add tests for the logic changed in this diff.
```

### Review a diff
```text
@code-reviewer #changes Review today’s diff for correctness, readability, and test gaps.
```

### Security audit
```text
@security #file Audit this endpoint for auth, injection, and secret handling.
```

---

## Project memory file

`PROJECT-WORKSPACE-MEMORY.md` is the local project memory.

It should hold:
- stack
- commands
- key architecture facts
- coding conventions
- testing expectations
- security and deployment constraints
- product / team preferences

By default, this file is ignored via `gitignore.txt`, so it can stay local.
If you want the whole team to share it, remove that ignore rule.

---

## Workspace integration

`dotvscode/settings.json` includes both:
- the main orchestrator agent instructions
- the local workspace memory file

That way Copilot can use both generic agent behavior and the project's stored local context.

---

## What changed compared to earlier versions

### Before
- one orchestrator with docs/review/security support
- useful, but still too generic
- no real project memory
- no dedicated feature / bugfix / test roles

### In 1.3.0
- leaner orchestrator
- local project bootstrap memory
- stronger role specialization
- better everyday prompt examples
- more practical VS Code Copilot workflow

---

## Troubleshooting

**`@dev-expert` not showing up**
- check that `dotgithub` was renamed to `.github`
- restart VS Code

**Specialist agents not showing up**
- confirm all `.agent.md` files are in `.github/agents/`
- reload the VS Code window

**Bootstrap questions never happen**
- check whether `PROJECT-WORKSPACE-MEMORY.md` still says `Bootstrap completed: no`
- if needed, clear or reset the file and call `@dev-expert` again

**Copilot ignores project context**
- confirm `.vscode/settings.json` exists after rename
- confirm `PROJECT-WORKSPACE-MEMORY.md` exists in the project root

**The project memory should be shared with the team**
- remove `PROJECT-WORKSPACE-MEMORY.md` from `.gitignore`
- commit the file normally

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

---

## License

MIT — see [LICENSE](./LICENSE). Use at your own risk.

*by [Alex Rosbach](https://github.com/AlexRosbach)*
