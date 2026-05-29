# Testing

## Manual routing checks

1. Confirm the agent reads `AGENTS.md`.
2. Confirm the runtime sees `.agents/skills/`.
3. Invoke each skill explicitly with `$skill-name`.
4. Check that the response follows the skill output contract.

Example prompts:

```text
Use $unity-architecture-guardian to review samples/unity-skill-sandbox/Assets/Game/Core.
Use $unity-prefab-assembler to plan a pooled projectile prefab.
Use $unity-ui-toolkit-builder to plan a settings screen.
```

## Deterministic scripts

Run scripts directly against the sandbox:

```bash
python .agents/skills/unity-architecture-guardian/scripts/scan_asmdefs.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/validate_naming.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/build_component_map.py samples/unity-skill-sandbox --format markdown
```

The prefab and UI skills include the subset of scripts they use. Scripts are read-only and do not require Unity Editor.

## Eval cases

`evals/cases.jsonl` contains baseline prompts and required terms. A simple eval runner can execute each prompt, capture the response, and score whether every `must_include` term appears.

The expected directory is intentionally separate:

```text
evals/expected/
```

Store captured golden responses there when the runtime and scoring process are chosen.
