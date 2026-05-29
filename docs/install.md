# Install

## Repo-local use

Place this repository inside a Unity workspace, or keep it as the workspace root. Tools that support repo-local skill discovery should read:

- `AGENTS.md`
- `.agents/skills/*/SKILL.md`
- `.agents/skills/*/references/`
- `.agents/skills/*/scripts/`

Use explicit invocation for reliable routing:

```text
Use $unity-architecture-guardian to review asmdef boundaries.
```

## Personal install

Copy a skill directory into the personal skills directory:

```bash
mkdir -p "$HOME/.agents/skills"
cp -R .agents/skills/unity-architecture-guardian "$HOME/.agents/skills/"
```

Repeat for each skill you want available globally.

## Symlink approach

Symlinks keep one source of truth while exposing skills to a personal runtime:

```bash
mkdir -p "$HOME/.agents/skills"
ln -s "$(pwd)/.agents/skills/unity-architecture-guardian" "$HOME/.agents/skills/unity-architecture-guardian"
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$HOME/.agents/skills"
New-Item -ItemType SymbolicLink -Path "$HOME/.agents/skills/unity-architecture-guardian" -Target "$(Get-Location)/.agents/skills/unity-architecture-guardian"
```

## Legacy Codex skills

Some older Codex setups may read `$HOME/.codex/skills` instead of `$HOME/.agents/skills`. Treat that as a deployment layer only: copy or symlink the same core skill folders there, but keep `.agents/skills/` as the repository source of truth.
