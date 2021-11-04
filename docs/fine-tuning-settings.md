# Fine-tuning settings

Fine tuning settings may not have a huge effect on the output, and are mostly used for specific uses.

For most where default is `None` it is often fine to not modify it and keep it `None`




### `optimiser`

> Default: `Adam`

Gradient descend optimizer, effects minimal. For now only effects vqgan. All others defaults to Adam. Seems unimportant to output.

![optms](fine-tuning-settings/optms.png)


### `batches`

> Default: `1`

The number of batches specifies how many iterations of accumulation of gradients would be needed before the image is altered one step. Think of it the same as in SGD. It can also be increased in conjunction with reducing `num_cuts` to reduce VRAM needed for image generation.




### `num_cuts`

> Default: `None`

`num_cuts` specifies the number of "cutouts" that the algorithm feeds into CLIP. A "cutout" is like image augmentation, and allows CLIP to see the image in differing zoom levels, perspectives, and so on. This is much like image augmentation for NN training - the more images, the better the grasp of the model. @robinsloan has a good write up [here](https://www.robinsloan.com/notes/cutouts/)




### `size`

> Default: `None`

Size specifies the width * height of the image. 

Usage:

> Python

```python
size = [100,200]
```

> Command line

```bash
--size 100 200
```






### `clip_models`

> Default: `None`

`clip_models` specify what CLIP pretrained models are used to optimize image generation. These models can be one of ['RN50', 'RN101', 'RN50x4', 'RN50x16', 'ViT-B/32', 'ViT-B/16'], where RN means the resNet architecture with 50 layers, and ViT means visual transformers. If using only one (typically with `quality=better` or `quality=best` there will be 3-4), it can save on VRAM usage, but with potential sacrifice to final output quality. 

Usage:

> Python

```python
clip_models='RN50,ViT-B/16'
```

> Command line

```bash
--clip_models 'RN50,ViT-B/16'
```

![clip models](fine-tuning-settings/clip%20models.png)




### `noise_prompt_seeds` and `noise_prompt_weights`

> Default: `None` and `None`

When both is not none, for every batch in an iteration, there will be a small random noise placed in the loss (and gradient). This is done by creating a prompt that only generates noise for every output. This may be used to allow the model to make some risk or change, or to be able to escape local minima. This is all just speculation, however.

Note that if one of them is shorter, it will silently reduce the total length of the shorter one; If one is `None`, noise prompts would not be active at all. 

The effects are unclear at the moment.

Usage:

> Python

```python
noise_prompt_seeds=[1,2]
noise_prompt_weights=[0.5,0.5]
```

> Command line

```bash
--noise_prompt_seeds 1 2 3 --noise_prompt_weights 1 1 1
```

![Canvas 1](fine-tuning-settings/Canvas%201.png)




### `init_noise`

> Default: `pixels`

`init_noise` can be one of  `pixels` , `gradient` , `snow` , `none`. Note that `none` cannot be used without a `init_image`, see more in [Image control settings](image-control-settings.md) 

![init_noise](fine-tuning-settings/init_noise.png)




### `learning_rate`, `learning_rate_drops`, and `auto_stop`

> Default: `0.2`, `[75]`, and `False`

The learning rate determines how big a step the model should take, but may cause unstable/more jittery images. `learning_rate_drops` is a list of percentage amounts that learning rate should drop, a drop means a division by 10. For example, the default is `[75]`, meaning that at 75% iterations, the lr would divide by 10.

