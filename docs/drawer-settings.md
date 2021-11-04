# Drawer settings

Currently there are four drawers

## pixel

### `pixel_size`

Pixel size determines how many pixels in rows and columns this pixel art image has. For example a specification of `pixel_size=[100,200]` generates a 100x200 pixel image, increasing `size` increases the size of the output, but not number of pixels.

### `pixel_scale`

This is a scaling multiplier on the ***size*** of the pixels of the image. The final number of pixels equals `pixel_size/pixel_scale`. 

### `pixel_type`

Pixel  type can be one of `rect`, `rectshift`, `tri`, `diamond`, `hex`, and `knit`. 

![pixel_type](drawer-settings/pixeltype.png)

## vqgan

### `vqgan_model`

One of these:

```
"imagenet_f16_1024" 
"imagenet_f16_16384"
"imagenet_f16_16384m"
"openimages_f16_8192"
"coco"
"faceshq"
"wikiart_1024"
"wikiart_16384"
"wikiart_16384m"
"sflckr"
```

Seems like these three have limited differences (all three seems to be labeled general images), faceshq and sflckr should be tested sometime soon.

![vqgan_model](drawer-settings/vqgan%20models.png)



## clipdraw

Didn't test. 🙇🏻‍♂️

### `strokes`

### `min_stroke_width`

### `max_stroke_width`



## line_drawer

Didn't test. 🙇🏻‍♂️

### `strokes`

### `stroke_length`

### `min_stroke_width`

### `max_stroke_width`

### `allow_paper_color`