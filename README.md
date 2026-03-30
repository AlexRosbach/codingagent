# VS Code Development Expert Agent

![Version](https://img.shields.io/badge/version-1.2.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![VS Code](https://img.shields.io/badge/VS%20Code-1.99%2B-007ACC?logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-required-black?logo=github)

A multi-agent template for GitHub Copilot in VS Code. Drop it into any project and Copilot becomes a development expert that actually follows your rules — without you having to repeat yourself every time.

> **Use at your own risk.** No warranties, no guarantees. See [LICENSE](./LICENSE).

---

## What it does

A lead agent orchestrates three specialized subagents that run automatically based on the task:

| Agent | Invocation | Responsibility |
|---|---|---|
| `@dev-expert` | Main entry point | Orchestrator — analyzes tasks, delegates, synthesizes results |
| `@doc-writer` | Auto-delegated or direct | README, CHANGELOG, JSDoc, inline comments |
| `@code-reviewer` | Auto-delegated or direct | Correctness, performance, naming, error handling, test coverage |
| `@security` | Auto-delegated or direct | OWASP Top 10, secrets, injection, auth flaws, dependency audit |

The orchestrator decides who does what:

```
User: "Add a login endpoint"

dev-expert
 ├── implements the feature
 ├── delegates docs   → @doc-writer   (updates README, JSDoc)
 ├── delegates review → @code-reviewer (checks correctness, naming)
 └── delegates audit  → @security     (checks for auth/injection issues)
```

All agents share the same non-negotiable standards:

- Never guess — only act on verifiable facts
- Documentation before or alongside code, never after
- Validate requirements and affected files before touching anything
- Backup before edits, rollback immediately on failure
- Semantic Versioning across README, CHANGELOG, and code
- Conventional Commits on every meaningful change
- Stop and ask when something is unclear — no improvising

---

## Requirements

- VS Code 1.99+
- GitHub Copilot subscription (Individual or Business)
- Git 2.x

---

## Setup

**New project — use this as a template:**
Click "Use this template" on GitHub, clone, open in VS Code. Done.

**Existing project — copy these files:**

```
your-project/
├── .github/
│   └── agents/
│       ├── dev-expert.agent.md       ← Orchestrator
│       ├── doc-writer.agent.md       ← Documentation subagent
│       ├── code-reviewer.agent.md    ← Code review subagent
│       └── security.agent.md         ← Security audit subagent
├── .vscode/
│   ├── settings.json
│   └── extensions.json
└── .gitignore
```

When VS Code prompts to install recommended extensions, click **Install All**.

---

## Using the agents

Open Copilot Chat (`Ctrl+Shift+I`).

**Normal use — let the orchestrator handle everything:**

```
@dev-expert Add a password reset flow
```

The orchestrator automatically delegates documentation, review, and security audit.

**Direct subagent access — when you know exactly what you need:**

```
@doc-writer Update the README for the new config options
@code-reviewer Review src/api/auth.ts for correctness
@security Audit the login endpoint for OWASP issues
```

**Context variables that improve results:**

| Variable | Use case |
|---|---|
| `#codebase` | Let the agent search the full project |
| `#problems` | Include current errors/warnings from the Problems panel |
| `#changes` | Include current Git diff |
| `#terminalLastCommand` | Include last terminal output (e.g. failed test run) |
| `#file` | Reference a specific file |

Example:
```
@dev-expert #changes Review everything I changed today and check for issues
```

---

## Customizing

**Add project-specific rules** at the bottom of `.github/agents/dev-expert.agent.md`:

```markdown
## Project-Specific Rules

- Framework: React 18 with TypeScript
- Styling: Tailwind CSS only
- Always respond in German
```

**Adjust subagent behavior** by editing the relevant agent file directly:
- Documentation standards → `doc-writer.agent.md`
- Review criteria → `code-reviewer.agent.md`
- Security checks → `security.agent.md`

**Add more subagents** by creating new `.agent.md` files and registering them in the orchestrator's `agents:` list:

```yaml
# dev-expert.agent.md frontmatter
agents: ['doc-writer', 'code-reviewer', 'security', 'your-new-agent']
```

---

## Troubleshooting

**`@dev-expert` not showing up** — confirm the file is at `.github/agents/dev-expert.agent.md` and VS Code is 1.99+. Restart VS Code.

**Subagents not being invoked** — make sure `settings.json` is in place and reload the window (`Ctrl+Shift+P` → `Developer: Reload Window`).

**Agent ignores the standards** — verify the `agents:` field in `dev-expert.agent.md` frontmatter lists all subagent names exactly as their `name:` field declares them.

**Subagent can't call another subagent** — check that `chat.subagents.allowInvocationsFromSubagents` is `true` in `.vscode/settings.json`.

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

---

## License

MIT — see [LICENSE](./LICENSE). Use at your own risk.

*by [Alex Rosbach](https://github.com/AlexRosbach)*
