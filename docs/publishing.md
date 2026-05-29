# Publishing Checklist

Before publishing this repository on GitHub or exporting skills:

- Each skill has a valid `SKILL.md`.
- The `name` frontmatter exactly matches the skill directory name.
- Descriptions are short and trigger-friendly.
- `AGENTS.md` exists and routes work to the three skills.
- `README.md` explains onboarding without duplicating all core behavior.
- `LICENSE` exists.
- Required references exist for each skill.
- Required scripts exist and run without Unity Editor.
- Required assets/templates exist for each skill.
- `samples/unity-skill-sandbox/` exists.
- `evals/cases.jsonl` and `evals/expected/` exist.
- CI smoke validation passes.
- No Unity `.meta` files were created manually.

Recommended release flow:

1. Run local script smoke tests.
2. Run the CI validation job in GitHub Actions.
3. Tag a version.
4. Copy or symlink skill folders into personal/runtime-specific skill directories only after the source tree is validated.
