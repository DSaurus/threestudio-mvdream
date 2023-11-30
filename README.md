# threestudio-mvdream
The MVDream extension for ThreeStudio. The original implementation can be found at https://github.com/bytedance/MVDream-threestudio. We thank them for their contribution to the 3D generation community.

# Installation
```
cd custom
git clone https://github.com/DSaurus/threestudio-mvdream.git
cd threestudio-mvdream
pip install -r requirements.txt
```

# Quick Start
```
# MVDream without shading (memory efficient)
python launch.py --config custom/threestudio-mvdream/configs/mvdream-sd21.yaml --train --gpu 0 system.prompt_processor.prompt="an astronaut riding a horse"

# MVDream with shading (used in paper)
python launch.py --config custom/threestudio-mvdream/configs/mvdream-sd21-shading.yaml --train --gpu 0 system.prompt_processor.prompt="an astronaut riding a horse"
```

# Resume from checkpoints
```
# resume training from the last checkpoint, you may replace last.ckpt with any other checkpoints
python launch.py --config path/to/trial/dir/configs/parsed.yaml --train --gpu 0 resume=path/to/trial/dir/ckpts/last.ckpt
# if the training has completed, you can still continue training for a longer time by setting trainer.max_steps
python launch.py --config path/to/trial/dir/configs/parsed.yaml --train --gpu 0 resume=path/to/trial/dir/ckpts/last.ckpt trainer.max_steps=20000
# you can also perform testing using resumed checkpoints
python launch.py --config path/to/trial/dir/configs/parsed.yaml --test --gpu 0 resume=path/to/trial/dir/ckpts/last.ckpt
# note that the above commands use parsed configuration files from previous trials
# which will continue using the same trial directory
# if you want to save to a new trial directory, replace parsed.yaml with raw.yaml in the command

# only load weights from saved checkpoint but dont resume training (i.e. dont load optimizer state):
python launch.py --config path/to/trial/dir/configs/parsed.yaml --train --gpu 0 system.weights=path/to/trial/dir/ckpts/last.ckpt
```

# Citing

If you find MVDream helpful, please consider citing:

```
@article{shi2023MVDream,
  author = {Shi, Yichun and Wang, Peng and Ye, Jianglong and Mai, Long and Li, Kejie and Yang, Xiao},
  title = {MVDream: Multi-view Diffusion for 3D Generation},
  journal = {arXiv:2308.16512},
  year = {2023},
}
```
