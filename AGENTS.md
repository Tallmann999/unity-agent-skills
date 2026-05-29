# AGENTS.md

## Project overview
This repository contains reusable Unity agent skills under `.agents/skills/`.

## Mandatory routing
- Use `$unity-architecture-guardian` for architecture review, asmdef boundaries, OOP/SOLID checks, and runtime/editor/tests partitioning.
- Use `$unity-prefab-assembler` when creating or restructuring prefabs, component composition, and ScriptableObject-to-Prefab patterns.
- Use `$unity-ui-toolkit-builder` for UI Toolkit screens, UXML/USS structure, bindings, and screen composition.

## Mandatory checks before marking work complete
- If runtime code changed, run architecture and naming validation scripts where applicable.
- If prefab composition changed, regenerate or review component map.
- If UI Toolkit files changed, validate naming and required references.

## Unity conventions
- Keep MonoBehaviours thin.
- Move business logic into plain C# classes when possible.
- Prefer ScriptableObjects for shared static/configuration data.
- Runtime code must not depend on Editor assemblies.
- Do not create Unity `.meta` files manually unless explicitly required.
