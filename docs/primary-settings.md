# Primary settings

Primary settings are settings that provide a large impact, and are the major settings that typically needed to consider when generating an image

### `prompts`

> Default: `[]`

prompts are the most direct and most meaningful of settings - it is the text that is used to guide how the drawer generates images.

Multiple simultaneous prompts can be input, with the pipe/vertical bar character "`|`" as separation between prompts. For each prompt, it is possible to specify weight and when to stop optimizing for a prompt, with syntax like `prompt:weight:stop`. The `weight` is a constant multiple that enhances the importance and impact of a prompt to the generation, and between multiple prompts. The `stop` is for telling the drawer/optimizer when to stop optimizing for this particular prompt, often used in conjunction with a negative weight: this is because the possibility for making an image look like "not something" is quite easy, it just has to look like absolutely nothing. `stop` to some extent prevents that.

Usage:

> Python

```python
prompts="suicide at the brooklyn bridge | film noir"
prompts="Squid game| art by Hwang Dong-hyuk"
```

> Command line

```bash
--prompts "seaside sunset| blue seas:3"
```

Examples: more in [this imgur post](https://imgur.com/a/SnSIQRu) - extremely helpful

![prompt examples](primary-settings/image-20211101233930703.png)

### `aspect`

> Default: `widescreen`

`aspect` can be one of three: `square`, `portrait`, or `widescreen`. By specifying aspect, it automatically defines `size` for the user, where the one-to-one relationship is defined as follows:

> 'square' -> size=\[144, 144] 'portrait'-> size=\[128, 160] 'widescreen'-> size=\[192, 108]

~~Recommended to use along with `scale` to increase size, note that quality automatically defines `scale`~~

![aspect](primary-settings/aspect.png)

### `drawer`

> Default: `vqgan`

The type of drawer defines what technology generates the images: `vqgan` uses VQGAN from [taming-transformers](https://github.com/CompVis/taming-transformers), `clipdraw` and `line_sketch` all use [diffvg](https://github.com/BachiLi/diffvg), and `pixel` uses dribnet's original pixel drawer. the new `diffusion` drawer makes higher quality images (subjective), but needs more iterations that vqgan.

difference in style: `pixel` generates pixel art, `vqgan` generates GAN-images, which are often trippy or realistic, and `clipdraw`/`line_sketch` generates stroke-based images as if it was a drawing and strokes were drawn down.&#x20;

![drawer](primary-settings/drawers.png)

### `quality`

> Default: `normal`

The `quality` parameter is able to give defaults to many different other arguments. In general, the better the quality, the larger the image, more CLIP models would be incorporated, more iterations it would run, and more batches would be run. This gives us an easier time to specify image quality.

Often, when testing a prompt or init\_image or technique, start with "draft", and then go larger as testing progresses.

![quality](primary-settings/quality.png)

### `iterations`

> Default: `None`

The name says it all, specify the number of iterations that a prompt would run with.

Typically for a prompt, 30 iterations would show the basic layout and focus, while from 100 on, the iterations may not change as much. Over 300 would have minimal effects.

Note: `quality` specifies iterations.

### `scale`

> Default: `None`

Use scale to increase size of output. The pixel size of the output is just aspect defaults multiplied by `scale`, `size` overrides `scale`. Scale need not be integer. Scale nor size does not effect pixel number of pixel drawer, or strokes of clipdraw drawer.
