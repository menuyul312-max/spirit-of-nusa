# Project Status — Spirit of Nusa

Updated: 2026-10-26. Maintainer role: Integrator.

## GitHub state verified on 2026-10-26

- `main`: initialized with an introductory README (commit `a1064ead7e2aac378905e5c6db9f79bdfdbf1642`).
- `integrator/bootstrap-source`: integration-preparation branch; source import pending.
- The README-only `main` does **not** contain a runnable Godot project.
- Do not merge this branch as proof that T089 or Android gameplay is complete.

## Local artifact audit

Source artifact: `Spirit_of_Nusa_T089_Terrain_Polish.zip` provided in the ChatGPT project.

Local checks performed by integrator against the extracted archive:
- `python tools/validate.py`: passed.
- `python -m unittest discover -s tests -p 'test_*.py'`: 18/18 tests passed.
- 43 Python source files parsed successfully.
- Three shader-source replacement anchors used by the T089 showcase were present in the provided archive.
- T088 and T089 screenshots differed when compared locally.

Not yet verified by integrator:
- Godot runtime launch, Godot GDScript unit tests, GPU rendering, Android installation, FPS and RAM.
- Baseline source code is **not** in GitHub yet.

## T089 scope and prerequisites

T089 proposes a **separate terrain showcase** (not a replacement for the playable island scene): grassy areas, sand, cliffs, shore, river mouth, pond and stylized waterfall.

Main proposed paths:
- `game/scripts/terrain/terrain_showcase.gd` and associated UID.
- `game/scenes/terrain_showcase/terrain_showcase.tscn` and README.
- `tests/test_terrain_showcase.gd`.
- `review/T-089/` evidence and notes.

Requires existing terrain, meshing, grass and water systems. Do not merge isolated showcase files without their dependencies.

## Integration gates

1. Import and audit the full, correct baseline project to a separate branch.
2. Verify source exclusions and licenses; never commit generated data or signing secrets.
3. Run `python tools/validate.py` and full Python unit tests.
4. Run Godot headless tests and the showcase scene; review runtime errors.
5. Verify the playable island scene still works.
6. Review shader-string replacement fragility and possible far-horizon artifacts.
7. Test on target Android hardware: frame time, memory, GPU appearance.
8. Open/complete code-review PR; merge only after explicit approval.

## Role boundaries

- TERRAIN: `feature/terrain` — mesh, grass, cliffs, sand and transitions.
- WATER & RENDERING: `feature/ocean` — water shaders and rivers.
- INTEGRATOR: review, test, integration branch and PR; **no direct feature changes to main**.

## Next action

Publish the complete original baseline source to `integrator/bootstrap-source`, preserving original files and ignoring build/cache artifacts. Then open a T089-specific branch/PR once prerequisites are present.
