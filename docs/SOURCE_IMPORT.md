# Baseline import procedure — T089 archive

Status: **NOT YET IMPORTED TO GITHUB** (2026-10-26). This is a reproducible preparation guide, not proof that source code was uploaded.

## Verified source package

- Artifact: `Spirit_of_Nusa_T089_Terrain_Polish.zip`
- SHA-256: `c14f0468e7013d0cb65989429e5277570cffe9c9347290639b2042497b50bd08`
- Approximate compressed archive: 96.9 MiB.
- Repository inventory from archive with .gitignore rules: about 1,390 files requiring import to this branch (source, Godot assets and test fixtures).
- Largest tracked asset: `game/assets/pemain/pemain_chibi.glb`, 6.52 MiB.
- Local `python tools/validate.py` passed.
- 18/18 Python unit tests passed.
- Godot runtime, graphics, Android benchmark and third-party asset redistribution rights still require review.

## Safe staging and push

An audited helper `publish_spirit_of_nusa.py` has been generated in the integrator conversation along with a SHA-256 manifest for the source ZIP.

On a networked machine with **Python 3.10+, Git and authenticated GitHub access**, place the helper next to the original ZIP and run:

```sh
python publish_spirit_of_nusa.py Spirit_of_Nusa_T089_Terrain_Polish.zip
# Review dry-run report; if it passes, publish only to integrator/bootstrap-source:
python publish_spirit_of_nusa.py Spirit_of_Nusa_T089_Terrain_Polish.zip --push
```

The script:
1. checks the exact ZIP hash, safely extracts files, skips signing keys and cache, and respects the branch .gitignore;
2. clones the existing `integrator/bootstrap-source` branch;
3. refuses to overwrite existing files or proceed with an incomplete import;
4. creates a single commit and **non-force-pushes only the integration branch**;
5. prints the existing draft PR URL for code review.

Do **not** push the ZIP itself or replace `main`, `README.md`, `.gitignore` or `docs/PROJECT_STATUS.md` with files from the archive. A successful local Git test is not a successful GitHub push.

## Why was import not performed from the integration conversation?

The GitHub connector can create UTF-8 files and Git objects, but the mounted local ZIP is not readable by that connector; the container that can read the ZIP cannot reach GitHub (DNS/network unavailable). Local dry-run and a complete commit/push to a throwaway **local** Git repository were successful; no 1,390-file import was made to the real GitHub repo.

## Before merge

- Verify PR files on GitHub, build and run Godot, and inspect original licenses in `licenses/`.
- Check main-game and terrain showcase scenes, shader import errors and resource paths.
- Run hardware Android frame-time/memory tests.
- Keep PR as Draft until validation and explicit Integrator approval.
