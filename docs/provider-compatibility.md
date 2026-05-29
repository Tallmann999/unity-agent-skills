# Provider Compatibility

The portable skill folder is the source of truth:

```text
.agents/skills/<skill-name>/
├── SKILL.md
├── references/
├── scripts/
└── assets/
```

Provider-specific files belong in `agents/`. For OpenAI-compatible runtimes this repository includes `agents/openai.yaml` with display metadata and invocation policy. Core behavior must remain in `SKILL.md`, references, scripts, and templates.

## OpenAI-compatible runtimes

Use `.agents/skills/` for discovery when supported. `agents/openai.yaml` may be used by packaging or UI layers for display names and default prompts.

## Claude Code and other runtimes

Export, copy, or symlink the same skill folder into the runtime-specific skills directory. Do not fork the behavior into a second copy unless you have a sync process.

## Synchronization caveat

There is no automatic synchronization between repo-local, personal, and provider-specific locations. Prefer symlinks or scripted copy during release so that every runtime consumes the same core files.
