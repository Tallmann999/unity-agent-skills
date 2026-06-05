# Unity Agent Skills

Переиспользуемые локальные скиллы для кодовых агентов, работающих с Unity-проектами. Основной источник информации находится в `.agents/skills/`, с компактной маршрутизацией в `AGENTS.md`, детерминированными helper scripts, небольшой Unity-like sandbox и базовыми eval cases.

## Включенные скиллы

* `unity-architecture-guardian`: ревью архитектуры, границы `asmdef`, разделение runtime/editor/tests, риски по OOP/SOLID, нейминг и карты компонентов.
* `unity-prefab-assembler`: планы сборки префабов, владение компонентами, сериализованные ссылки, границы конфигураций через ScriptableObject и настройка связей в инспекторе.
* `unity-ui-toolkit-builder`: планирование экранов UI Toolkit, структура UXML/USS, границы биндинга, ответственности контроллеров и риски жизненного цикла UI.

## Использование внутри репозитория

Держите этот репозиторий в корне Unity-проекта или подключите его в рабочее пространство Unity-проекта. Агенты, которые поддерживают локальное обнаружение внутри репозитория, должны читать `AGENTS.md` и находить скиллы в `.agents/skills/`.

Вызывайте нужный скилл явно, когда он нужен:

```text
Use $unity-architecture-guardian to review Assets/Game/Core.
Use $unity-prefab-assembler to plan an enemy turret prefab.
Use $unity-ui-toolkit-builder to design a settings menu screen.
```

## Персональная установка

Для инструментов, которые читают персональные скиллы, скопируйте или создайте symlink для каждой папки скилла из `.agents/skills/` в `$HOME/.agents/skills/`. Варианты установки и заметки по устаревшему `.codex/skills` смотрите в `docs/install.md`.

## Проверка

Запускайте детерминированные скрипты без Unity Editor:

```bash
python .agents/skills/unity-architecture-guardian/scripts/scan_asmdefs.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/validate_naming.py samples/unity-skill-sandbox
python .agents/skills/unity-architecture-guardian/scripts/build_component_map.py samples/unity-skill-sandbox --format markdown
```

GitHub Actions запускает проверки структуры и smoke tests для скриптов в `.github/workflows/validate.yml`.

## Sandbox и evals

* Sandbox: `samples/unity-skill-sandbox/`
* Eval cases: `evals/cases.jsonl`
* Папка с ожидаемыми результатами: `evals/expected/`

Sandbox намеренно сделан минимальным. Он нужен для проверки соглашений по папкам, скриптов и ответов скиллов, а не для поставки полноценной игры.
