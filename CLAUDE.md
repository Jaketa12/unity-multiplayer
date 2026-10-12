# unity-multiplayer

Unity project for **Sinister Silence**, a multiplayer game.

## Layout

The Unity project is NOT at the repo root. It lives in `Sinister Silence game/`
(note the spaces — always quote this path in shell commands):

- `Sinister Silence game/Assets/` — all game content; scripts go under `Assets/Scripts/`
- `Sinister Silence game/ProjectSettings/` — committed; edit via the Unity Editor, not by hand
- `Sinister Silence game/Packages/manifest.json` — package dependencies

`Library/`, `Temp/`, `Build/`, `Logs/` and `UserSettings/` are gitignored and must stay that way.

## Environment

- Unity Editor `2021.3.37f1` (see `ProjectSettings/ProjectVersion.txt`). Do not bump
  the editor version or package versions without being asked.
- No netcode/multiplayer package is installed yet. Ask before choosing one rather
  than assuming Netcode for GameObjects, Mirror, Photon, or anything else.
- The Unity Editor is not available in cloud sessions: scripts can be written and
  reviewed, but they cannot be compiled or run here. Say so instead of claiming a
  change was verified.

## Conventions

- `.meta` files are part of the project. When adding, moving, or deleting an asset,
  the matching `.meta` file moves with it; never delete one on its own and never
  edit a GUID by hand.
- Scenes and prefabs are binary-ish YAML and merge badly. Prefer creating a new
  scene or prefab over hand-editing an existing one, and flag any scene change in
  your summary so it gets a careful look.
- C#: four-space indent, `PascalCase` for types, methods, and public members,
  `_camelCase` for private fields, `[SerializeField] private` over public fields.
- One `MonoBehaviour` per file; the filename matches the class name exactly, or
  Unity will not attach the component.
- Networked code: keep authority explicit. Server-authoritative by default; never
  trust client input for game state.

## Working agreements

- Commit the Unity project files, not build output.
- Keep diffs scoped to the request. Don't reformat or reorganize `Assets/` on the side.
