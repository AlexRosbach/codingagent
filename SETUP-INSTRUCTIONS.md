# Setup Instructions

## Folder Renaming Required

The ZIP contains two folders with modified names to make them visible on all systems.
Before using, rename them as follows:

| Folder/File in ZIP    | Rename to      |
|-----------------------|----------------|
| `dotgithub/`          | `.github/`     |
| `dotvscode/`          | `.vscode/`     |
| `gitignore.txt`       | `.gitignore`   |

## Final structure in your project root

```
your-project/
├── .github/
│   └── copilot-instructions.md   ← Agent prompt (the core file)
├── .vscode/
│   ├── settings.json             ← VS Code + Copilot config
│   └── extensions.json           ← Recommended extensions
├── README.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

## Quick setup

### Windows (PowerShell)
```powershell
Rename-Item "dotgithub" ".github"
Rename-Item "dotvscode" ".vscode"
Rename-Item "gitignore.txt" ".gitignore"
```

### Mac / Linux (Terminal)
```bash
mv dotgithub .github
mv dotvscode .vscode
mv gitignore.txt .gitignore
```

After renaming, open the folder in VS Code — the agent is active immediately.

See README.md for full setup instructions.
