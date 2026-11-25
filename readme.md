# InvRGB+L with Environment-Map Lighting and Metallic Materials (unofficial extension)

> **This is a personal, unofficial extension of [InvRGB+L](https://github.com/cxx226/InvRGBL)**
> (Chen et al., *InvRGB+L: Inverse Rendering of Complex Scenes with Unified Color and LiDAR
> Reflectance Modeling*, ICCV 2025). The method and most of this codebase are the work of the
> original authors. I am not affiliated with them. My own changes are listed below.

Original project: [code](https://github.com/cxx226/InvRGBL) · [paper](https://arxiv.org/pdf/2507.17613)

## What I added
| Change | Description | Where |
|---|---|---|
| Environment-map lighting | [one line on how lighting is modelled] | `[path/to/file.py]` |
| Learnable metallic parameter | Per-Gaussian metallic material parameter, optimised jointly with the existing materials | `[path]` |
| LiDAR data preprocessing | LiDAR scan loading and intensity look-up tables (NumPy) | `[path]` |
| Visualisation | Camera geometry and multi-sensor (RGB + LiDAR) visualisation for driving scenes | `[path]` |
| LiDAR-aware supervision | [one line on what it changes] | `[path]` |

**Status:** [experimental research code; not benchmarked against the original] *or*
[short results table if you have numbers].

## Installation
```shell
git clone https://github.com/VincentMa123/InvRGBL-EnvMap-Metallic
cd InvRGBL-EnvMap-Metallic

conda create -n InvRGBL python=3.9 -y
conda activate InvRGBL
pip install -r requirements.txt
pip install git+https://github.com/nerfstudio-project/gsplat.git@v1.3.0
pip install git+https://github.com/facebookresearch/pytorch3d.git
pip install git+https://github.com/NVlabs/nvdiffrast
pip install ./bvh
```

## Data
Same as the original: Waymo, prepared following [docs/Waymo.md](docs/Waymo.md).

## Running
Training follows the original commands (`configs/invrgbl.yaml` for dynamic scenes,
`configs/invrgbl_static.yaml` for static scenes):

```shell
export PYTHONPATH=$(pwd)
python tools/train.py \
    --config_file configs/invrgbl.yaml \
    --output_root $output_root \
    --project $project \
    --run_name $expname \
    dataset=waymo/1cams \
    data.scene_idx=$scene_idx \
    data.start_timestep=0 \
    data.end_timestep=50
```

To enable my additions: [config flags or config file, e.g. `model.envmap.enabled=True`].

## Acknowledgments
All credit for the InvRGB+L method and its base implementation goes to its authors:
Xiaoxue Chen, Bhargav Chandaka, Chih-Hao Lin, Ya-Qin Zhang, David Forsyth, Hao Zhao and
Shenlong Wang. The original code builds on [DriveStudio](https://github.com/ziyc/drivestudio).

## Citation
If you use this code, please cite the original paper:
```bibtex
@article{chen2025invrgb+,
  title={InvRGB+L: Inverse Rendering of Complex Scenes with Unified Color and LiDAR Reflectance Modeling},
  author={Chen, Xiaoxue and Chandaka, Bhargav and Lin, Chih-Hao and Zhang, Ya-Qin and Forsyth, David and Zhao, Hao and Wang, Shenlong},
  journal={arXiv preprint arXiv:2507.17613},
  year={2025}
}
```

## License
Follows the license of the original repository; see `LICENSE`.
