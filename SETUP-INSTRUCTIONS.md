# How to set up

After extracting the ZIP, rename the following folders and file:

| What you see            | Rename to      |
|-------------------------|----------------|
| `[1] rename-to-.github` | `.github`      |
| `[2] rename-to-.vscode` | `.vscode`      |
| `[3] rename-to-.gitignore` | `.gitignore` |

Your final project structure should look like this:

```
your-project/
├── .github/
│   └── agents/
│       └── dev-expert.agent.md
├── .vscode/
│   ├── settings.json
│   └── extensions.json
├── .gitignore
├── README.md
├── CHANGELOG.md
└── LICENSE
```

## Windows (PowerShell)

```powershell
Rename-Item "[1] rename-to-.github" ".github"
Rename-Item "[2] rename-to-.vscode" ".vscode"
Rename-Item "[3] rename-to-.gitignore" ".gitignore"
```

## Mac / Linux (Terminal)

```bash
mv "[1] rename-to-.github" .github
mv "[2] rename-to-.vscode" .vscode
mv "[3] rename-to-.gitignore" .gitignore
```

After renaming, open the folder in VS Code and install the recommended extensions when prompted.
