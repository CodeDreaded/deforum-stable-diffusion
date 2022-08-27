# deforum-stable-diffusion

Refactor of the Deforum Stable Diffusion notebook (featuring video_init) https://colab.research.google.com/github/deforum/stable-diffusion/blob/main/Deforum_Stable_Diffusion.ipynb

- v0.1 announcement: https://twitter.com/deforum_art/status/1562999935414333441

## Layout

The notebook has been split into the following parts:

- `deforum_video.py` is the main module (everything else gets imported via that if used directly)
  - Reports on the GPU using `nvidia-smi`
- `general_config.py`:
  - sets `models_path` and `output_path` and creates them if they don't exist (they're no longer at
    `/content/models` and `/content/output` but under the caller's current working directory `./`)
  - also sets `DeforumArgs` and the namespace (`general_args`) which gets imported to the main
    `deforum_video` module as the name `args` (like in the original notebook).
- `env_config.py` 

## Installation

See `CONDA_SETUP.md` file indicating prerequisites to run and the reasoning behind installing them this way

```sh
conda create -n deforum
conda activate deforum
conda install -y pytorch torchvision torchaudio torchtext cudatoolkit=11.6 pytorch-lightning -c pytorch -c conda-forge
pip install accelerate einops ftfy jsonmerge kornia omegaconf resize-right torchdiffeq torchmetrics transformers
pip install -e git+https://github.com/CompVis/taming-transformers.git@master#egg=taming-transformers
pip install -e git+https://github.com/deforum/stable-diffusion@main#egg=latent-diffusion
pip install -e git+https://github.com/deforum/k-diffusion@master#egg=k-diffusion
```
