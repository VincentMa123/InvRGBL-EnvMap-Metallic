# InvRGB+L Extensions: Lighting, Materials, Shadows and Relighting (unofficial, team project)

> **This is an unofficial extension of [InvRGB+L](https://github.com/cxx226/InvRGBL)**
> (Chen et al., ICCV 2025). The method and the base codebase are the work of the original authors;
> we are not affiliated with them. This repository started from their code (commits up to `bf6b62e`).
>
> Team: [Vincent Ma](https://github.com/VincentMa123), [name](https://github.com/Susssyy123),
> [name](https://github.com/DhanaKresnawijaya237). [Course project for COURSE, SUSTech — if applicable]

Original project: [code](https://github.com/cxx226/InvRGBL) · [paper](https://arxiv.org/pdf/2507.17613) ·
All our changes: [diff since the original](https://github.com/VincentMa123/InvRGBL-EnvMap-Metallic/compare/bf6b62e...main)

## What we added
| Change | Description | Main files | Main contributor |
|---|---|---|---|
| Environment-map lighting | Learnable environment map, split into diffuse and specular maps | `models/modules_envmap.py`, `models/trainers/pbr.py` | Susssyy123 |
| Metallic material | Metallic parameter added to the physically based shading | `models/gaussians/relightgs.py`, `models/trainers/pbr.py` | Susssyy123 |
| Shadows | Shadow-map visibility in place of BVH ray tracing; OBB-based shadow handling | `models/trainers/base.py`, `tools/visualize_shadow_map.py` | VincentMa123 (shadow map), Susssyy123 (OBB) |
| Training speed | Fixed slow training caused by visibility updates | `models/trainers/base.py`, `models/video_utils.py` | VincentMa123 |
| Material fixes | Fixes to reflectivity, sun visibility, albedo and the environment map | `models/trainers/base.py`, `models/nodes/relight_rigid.py` | VincentMa123 |
| LiDAR intensity look-up table | Intensity look-up table for Waymo LiDAR, with verification and a report | `tools/custom/build_waymo_intensity_lut.py`, `tests/verify_waymo_intensity_lut.py`, `docs/LiDARIntensityReport.pdf` | Susssyy123 (preprocessing fixes: VincentMa123) |
| Image priors and SAM regions | Image priors (normals, RGB↔X) and SAM region maps for reflectivity | `tools/custom/extract_image_priors.py`, `tools/custom/run_rgbx_batch.py`, `tools/precompute_reflectivity_sam_regions.py` | Susssyy123 |
| Relighting and night scenes | Relighting script with streetlights and headlights; spotlight configs and ablations | `tools/relight.py`, `configs/spotlights_023_*.json`, `relight_023_*.sbatch` | Susssyy123, DhanaKresnawijaya237 (spotlights) |
| Visualisation | Ground-truth LiDAR intensity, shadow-map, SAM-region and prior visualisers | `tools/custom/visualize_gt_intensity.py`, `tools/visualize_shadow_map.py`, `tools/visualize_sam_regions.py`, `tools/custom/visualize_priors.py` | VincentMa123 (intensity, shadow map), Susssyy123 |
| Cluster scripts | Slurm scripts for training and relighting | `train_023*.sbatch`, `relight_023.sbatch` | VincentMa123, Susssyy123 |
