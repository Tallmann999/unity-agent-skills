# Unity Agent Skills

Reusable repo-local skills for code agents working with Unity projects. The source of truth lives in `.agents/skills/`, with compact root routing in `AGENTS.md`, deterministic helper scripts, a tiny Unity-like sandbox, and baseline eval cases.

## Included skills

- `unity-architecture-guardian`: architecture review, asmdef boundaries, runtime/editor/tests partitioning, OOP/SOLID risks, naming, and component maps.
- `unity-prefab-assembler`: prefab composition plans, component ownership, serialized references, ScriptableObject config boundaries, and inspector wiring.
- `unity-ui-toolkit-builder`: UI Toolkit screen planning, UXML/USS structure, binding boundaries, controller responsibilities, and UI lifecycle risks.

## Repo-local usage

Keep this repository at the root of, or linked into, a Unity project workspace. Agents that support repo-local discovery should read `AGENTS.md` and discover skills under `.agents/skills/`.

Invoke a skill explicitly when needed:

```text
Use $unity-architecture-guardian to review Assets/Game/Core.
Use $unity-prefab-assembler to plan an enemy turret prefab.
Use $unity-ui-toolkit-builder to design a settings menu screen.
```

## Personal install

For tools that read personal skills, copy or symlink each skill directory from `.agents/skills/` into `$HOME/.agents/skills/`. See `docs/install.md` for options and legacy `.codex/skills` notes.

## Validation

Run deterministic scripts without Unity Editor:

```bash
python .agents/skills/unity-architecture-guardian/scripts/scan_asmdefs.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/validate_naming.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/build_component_map.py samples/unity-skill-sandbox --format markdown
```

GitHub Actions runs structure checks and smoke tests for the scripts in `.github/workflows/validate.yml`.

## Sandbox and evals

- Sandbox: `samples/unity-skill-sandbox/`
- Eval cases: `evals/cases.jsonl`
- Expected outputs directory: `evals/expected/`

The sandbox is intentionally minimal. It exists to test folder conventions, scripts, and skill responses, not to ship a game.
