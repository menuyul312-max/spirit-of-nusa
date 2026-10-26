# Asset license review — blocking the T089 public-source import

Updated: 2026-10-26. Source of findings: `licenses/manifest.csv` from the supplied T089 ZIP.

The repository is **public**. The archive contains a manifest listing some source assets for which redistribution or commercial-use conditions are not yet verified. Passing tests does not establish licensing clearance.

## Requires owner / licensing review before public push

| File in archive | License-manifest concern |
| --- | --- |
| `game/assets/props/rumah_panggung.glb` | DINOv3 (Meta) license unverified |
| `game/assets/buildings/rumah_panggung.glb` | DINOv3 (Meta) license unverified; used as player house asset |
| `game/assets/props/kendi.glb` | Gemini concept input / TRELLIS.2 output; accompanying DINOv3 license unverified |
| `art-src/konsep/Gemini_Generated_Image_8evhod8evhod8evh.jpg` | Manifest says Gemini commercial-use conditions require owner confirmation |

Also present: `game/assets/ui/logo_penunggu_nusa.png` and `game/assets/ui/nusa_icons_original.png` (manifest: OpenAI-generated). Review provenance and publication rights for all generated media before distributing the game publicly.

## Required decisions

1. Confirm provenance and distribution rights for every flagged asset with the owner and original applicable licenses.
2. If rights are not clear, replace the asset with independently cleared original work and update the manifest; do not silently omit a scene-critical mesh.
3. Review `licenses/manifest.csv` beyond the flagged entries. A self-reported manifest is not third-party authorization.
4. Only after clearance, publish the full ZIP-derived project via the validated import helper. Do not merge an incomplete Godot baseline.

## Technical status

The integrator prepared 1,390 source files locally and validated a simulated push against a throwaway local Git remote. **No asset from the ZIP has been uploaded to GitHub by that simulation.**

GitHub Actions for Python/source-presence checks was added to the draft integration branch. Its successful execution has not been verified. Godot and Android hardware tests remain outstanding.
