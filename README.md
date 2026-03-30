# VS Code Development Expert Agent

![Version](https://img.shields.io/badge/version-1.1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![VS Code](https://img.shields.io/badge/VS%20Code-1.99%2B-007ACC?logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-required-black?logo=github)

As you can imagine, this is a WIP. It includes only my personal permanent standards, which I used to implement in all my agents. This is why I created this template.

Drop it into any project and GitHub Copilot becomes a development expert that actually follows your rules — without you having to repeat yourself every time.

> **Use at your own risk.** No warranties, no guarantees. See [LICENSE](./LICENSE).

---

## What it does

The agent enforces a fixed set of development standards on every task:

- Never guess — only act on verifiable facts
- Documentation before or alongside code, never after
- Validate requirements and affected files before touching anything
- Flag backups before edits, rollback immediately on failure
- Semantic Versioning across README, CHANGELOG, and code
- Conventional Commits on every meaningful change
- Stop and ask when something is unclear — no improvising

The full ruleset lives in `.github/agents/dev-expert.agent.md`.

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
│       └── dev-expert.agent.md
├── .vscode/
│   ├── settings.json
│   └── extensions.json
```

When VS Code prompts to install recommended extensions, click **Install All**.

---

## Using the agent

Open Copilot Chat (`Ctrl+Shift+I`), then either:

- Type `@dev-expert` to invoke it directly
- Or select **Agent** in the dropdown and pick `dev-expert`

---

## Customizing

Add project-specific rules at the bottom of `.github/agents/dev-expert.agent.md`:

```markdown
## Project-Specific Rules

- Framework: React 18 with TypeScript
- Styling: Tailwind CSS only
- Always respond in German
```

Need more agents? Just add more files:

```
.github/agents/
├── dev-expert.agent.md
├── code-reviewer.agent.md
└── docs-writer.agent.md
```

---

## Troubleshooting

**`@dev-expert` not showing up** — confirm the file is at `.github/agents/dev-expert.agent.md` and VS Code is 1.99+. Restart VS Code.

**Agent ignores the standards** — make sure `settings.json` is in place and reload the window (`Ctrl+Shift+P` → `Developer: Reload Window`).

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

---

## License

MIT — see [LICENSE](./LICENSE). Use at your own risk.

*by [Alex Rosbach](https://github.com/AlexRosbach)*
