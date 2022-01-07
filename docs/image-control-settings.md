# Image control settings

## Init image related:

### `init_image`

> Default: `None`

Path or URL of the initial image that is used to jump start the model. having an `init_image` can be very beneficial to the output: it can concentrate the model to a central focus, which it typically has difficulty in.

![init\_image](<image-control-settings/init image.png>)

### `init_image_alpha` and `init_noise`

> Default: `200` and `pixels`

The two goes hand in hand. When using an init image, the noise is overlaid on the init image, making it noisier, and the color less intense, as shown in the last example, where the noise is `none`, the image becomes "brightened". Potentially, decreasing the `init_noise` may allow for the model to have a wider range of potential outcomes, and less prone to get in local minima, but this is just speculation. However, if repeatedly generating images and putting them back in, not setting `init_image_alpha` to 255 may cause the image to fade out.

`init_noise` can be one of `pixels` , `gradient` , `snow` , `none`. `none` cannot be used without an `init_image` and it would "brighten" the image if `init_image_alpha` isn't 255.

![init\_noise](image-control-settings/init\_noise.png)

## Image Prompts and Target Images

### `image_prompts`, `image_prompt_weight`, and `image_prompt_shuffle`

> Default: `[]`, `None`, and `False`

Image prompts work the same as text prompts: they are encoded as prompts and generate losses the same way a text prompt does.&#x20;

Image prompts unfortunately still cannot use the prompt:weight:stop logic, despite having prompt in its name. it also cannot use commas to separate different images, it uses an odd package called `braceexpand` to generate a list of filenames. and example may be `"a{1..3}b"` is expanded as `['a1b', 'a2b', 'a3b'`], while `"a{1,3}b"` is expanded as `['a1b', 'a3b']`. This should be changed.

Image prompt shuffle is just for resetting the transformed images every time cutouts is made, if `False` every image prompt will have the same cutout, if `True` different image prompts would have different cutouts.

> Usage

```python
image_prompts = "pimgs{1..10}.png"
image_prompt_weight = 1.0
image_prompt_shuffle = True
```

![image\_prompts](<image-control-settings/image prompt.png>)

### `target_images`

> Default: `None`

This is functionally similar to `image_prompts`. It differs in two places. `target_images` allows the prompt:weight:stop and `|` separation logic, and it is not made cutouts every time it is compared: it's embedding is generated during init, like text prompts, and not during ascent.

> Usage

```python
target_images = "fish.png:3:10 | anime.png:-1:-0.9"
```

## Spot Prompts

### `spot_prompts`, `spot_prompts_off`, and `spot_file`

> Default: `[]`, `[]`, and `None`

Spot prompts is a misleading name: a more accurate name may be masked prompts. With this option, a mask image can be used to specify which parts of the image will be seen by which prompts. The black parts of the `spot_file` will be shown to the prompts specified in `spot_prompts`, while the white parts will be shown to `spot_prompts_off`. Below is a basic visual demonstration of how this is utilized.

Spot prompts also has the same input logic as normal prompts.

![spot\_prompts](<image-control-settings/spot prompts showcase.png>)

## Overlay

### `overlay_image`

The image that is overlaid on top of the generated output, this is done every `overlay_every` iterations. When an init image is just not enough, and you need that power and control and specification… my impression is that this is best used for color location specification. Has big potential, but is kinda jank.

### `overlay_alpha`

This is important because if it's too high, then the image is just going to "reset" every time it hits overlay\_every. By default its behavior is same as setting it as 255, which is bad, so always remember to set this to something reasonable when using overlay. Somewhere around 50-100 is good for the default `overlay_every`=10.

### `overlay_every`

The name says it all: every `overlay_every` number of iterations, it does an overlay.

### `overlay_offset`

Seems not important. Not an image offset, but a iteration offset. For `overlay_every`=10, having offset at 5 makes it overlay at 5,15,25 etc. iterations.

![overlay\_image](<image-control-settings/overlay exp2.png>)
