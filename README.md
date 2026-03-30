# 🤖 VS Code Development Expert Agent

> A GitHub Copilot agent configuration that enforces professional development standards — automatically, on every task.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![VS Code](https://img.shields.io/badge/VS%20Code-1.90%2B-007ACC?logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-required-black?logo=github)

---

## ⚠️ Disclaimer

**Use at your own risk.**

This configuration modifies how GitHub Copilot behaves in your VS Code environment. It is provided as-is, without any warranty of any kind — express or implied. The author is not responsible for any issues, data loss, or unintended behavior that may result from using this setup. Always review AI-generated suggestions before applying them to production systems.

See [LICENSE](./LICENSE) for full terms.

---

## What is this?

This repository contains a ready-to-use VS Code workspace configuration that turns GitHub Copilot into a **professional development expert agent** — one that knows and enforces your team's quality standards without being told every time.

Once set up, the agent will:

- ✅ Always document before or alongside implementation
- ✅ Validate requirements and affected files before making changes
- ✅ Remind you to create backups before edits
- ✅ Immediately suggest rollback on failure
- ✅ Write commit messages following [Conventional Commits](https://www.conventionalcommits.org/)
- ✅ Maintain versioning consistently across README, CHANGELOG, and code
- ✅ Stop and ask instead of guessing or improvising
- ✅ Propose unit tests for new or changed code

---

## Repository Structure

```
.
├── .github/
│   └── copilot-instructions.md   ← The agent prompt (your standards, always active)
├── .vscode/
│   ├── settings.json             ← VS Code + Copilot workspace config
│   └── extensions.json           ← Recommended extensions for your team
├── README.md                     ← This file
├── CHANGELOG.md                  ← Version history
└── LICENSE                       ← MIT License
```

---

## Requirements

| Requirement | Min. Version | Notes |
|---|---|---|
| [Visual Studio Code](https://code.visualstudio.com/) | 1.90+ | Free |
| [GitHub Copilot](https://github.com/features/copilot) | Individual / Business | Paid subscription required |
| [Git](https://git-scm.com/) | 2.x | Free |

> **Note:** GitHub Copilot Free tier does not fully support Agent mode. An Individual or Business subscription is required.

---

## Setup

### Option A — Use as a template for a new project

1. Click **"Use this template"** on GitHub to create your own repository.
2. Clone it locally and open the folder in VS Code.
3. Done — the agent is active.

### Option B — Add to an existing project

Copy the following into your project root (keeping the folder structure):

```
your-project/
├── .github/
│   └── copilot-instructions.md
├── .vscode/
│   ├── settings.json
│   └── extensions.json
```

> If `.github/` or `.vscode/` already exist in your project, add only the missing files and manually merge any existing `settings.json`.

### Install recommended extensions

When you open the project in VS Code, a prompt will appear:

> *"Do you want to install the recommended extensions for this repository?"*

Click **Install All**.

Or install manually:
```
Ctrl+Shift+P → "Extensions: Show Recommended Extensions"
```

### Verify the agent is working

1. Open Copilot Chat: `Ctrl+Shift+I`
2. In the chat dropdown at the top, select **"Agent"** (not "Ask" or "Edit")
3. Type: *"What development standards apply in this project?"*
4. The agent should respond with the full standards. ✓

---

## The Development Standards (Summary)

The full rules are embedded in `.github/copilot-instructions.md`. Here's the short version:

| Rule | Principle |
|---|---|
| 🚫 Never guess | Only make statements based on verifiable facts |
| 📄 Docs first | README and CHANGELOG are updated before or alongside code |
| 🔍 Validate before changing | Understand requirements and affected files first |
| 💾 Backup before editing | Always note the backup path or branch |
| ↩️ Rollback on failure | Revert immediately, then analyze |
| 🏷️ Always version | Semantic Versioning everywhere, consistently |
| 💬 Always commit | Conventional Commits format, every meaningful change |
| 🧪 Test if possible | Suggest and generate tests proactively |
| 🛑 Stop, don't improvise | Ask when uncertain — never bluff |

### Conventional Commits format

```
<type>(<scope>): <short description>

Examples:
feat(auth):      Add SSO login
fix(api):        Handle timeout errors correctly
docs(readme):    Update setup instructions
refactor(utils): Consolidate helper functions
chore(deps):     Update dependencies
```

### Semantic Versioning

```
Major.Minor.Patch

Patch  → Bug fixes, small corrections
Minor  → New features, backward-compatible
Major  → Breaking changes
```

---

## Included Extensions

The `.vscode/extensions.json` recommends the following extensions to all team members:

| Extension | Purpose |
|---|---|
| `github.copilot` | AI code completion |
| `github.copilot-chat` | Copilot Chat & Agent mode |
| `eamodio.gitlens` | Enhanced Git history, blame, compare |
| `mhutchie.git-graph` | Visual Git branch graph |
| `vivaxy.vscode-conventional-commits` | Commit message picker (Conventional Commits) |
| `esbenp.prettier-vscode` | Code formatter |
| `dbaeumer.vscode-eslint` | JavaScript/TypeScript linting |
| `ms-python.python` | Python support |
| `yzhang.markdown-all-in-one` | Markdown editing |
| `davidanson.vscode-markdownlint` | Markdown linting |
| `gruntfuggly.todo-tree` | TODO/FIXME tracker |
| `streetsidesoftware.code-spell-checker` | Spell check in code |

---

## Customizing for Your Project

The agent behavior is fully controlled by `.github/copilot-instructions.md`.  
You can extend it with project-specific rules:

```markdown
## Project-Specific Rules

- Framework: React 18 with TypeScript
- Styling: Tailwind CSS only — no plain CSS
- API layer: always abstract through `src/api/`
- Allowed packages: see `ALLOWED_PACKAGES.md`
- Language: respond in English
```

---

## Troubleshooting

**Agent doesn't know the standards:**
- Verify `.github/copilot-instructions.md` exists at the correct path (not inside `.vscode/`)
- Confirm `settings.json` contains `"github.copilot.chat.codeGeneration.useInstructionFiles": true`
- Restart VS Code

**Agent mode not available:**
- Make sure `github.copilot-chat` extension is installed and up to date
- Agent mode requires a paid Copilot subscription

**Extensions not suggested:**
- A workspace folder must be open (not just a single file) for `extensions.json` to take effect

---

## Contributing

Contributions, issues, and suggestions are welcome.  
Please open an issue first before submitting a pull request.

When contributing, please follow the same standards this project enforces:
- Conventional Commits for all changes
- Update `CHANGELOG.md` with your changes
- Update `README.md` if behavior changes

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for the full version history.

---

## License

MIT License — see [LICENSE](./LICENSE) for details.

**Use at your own risk.** This project is provided without warranty of any kind.

---

*Created by [Alex Rosbach](https://github.com/AlexRosbach)*
