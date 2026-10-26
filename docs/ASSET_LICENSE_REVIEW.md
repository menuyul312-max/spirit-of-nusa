# Asset license review — blocking the T089 public-source import

Updated: 2026-10-26. Source: `licenses/manifest.csv` in the supplied T089 ZIP.

This is a **public repository**. Before uploading assets, confirm redistribution and commercial-use rights for flagged entries.

| Asset | Pending review |
| --- | --- |
| `game/assets/props/rumah_panggung.glb` | DINOv3 (Meta) licensing not verified |
| `game/assets/buildings/rumah_panggung.glb` | DINOv3 (Meta) licensing not verified |
| `game/assets/props/kendi.glb` | Gemini concept, TRELLIS.2 output and DINOv3 licensing not verified |
| `art-src/konsep/Gemini_Generated_Image_8evhod8evhod8evh.jpg` | Commercial-use/redistribution terms need owner confirmation |

Also review the provenance of generated UI art and every other manifest entry. The project's license manifest alone does not grant rights.

## Required before public import

1. Verify rights, or replace files with independently cleared original assets.
2. Update `licenses/manifest.csv` with accurate provenance and relevant licenses.
3. Import the full project only after review, using the import script and a non-force push to `integrator/bootstrap-source`.

## Technical and workflow status

Approximately 1,390 project files were prepared and pushed to a **temporary local test remote**, not GitHub. No source assets from that test are present in this GitHub branch.

**CI/CD is intentionally not used per project owner's 2026-10-26 instruction.** The prior GitHub Actions workflow was removed from the integration branch. Testing remains a local/manual pre-merge responsibility. Godot runtime and Android hardware tests have not been verified.
