# Drawer Settings

Currently there are four drawers

## pixel

### `pixel_size`

Pixel size determines how many pixels in rows and columns this pixel art image has. For example a specification of `pixel_size=[100,200]` generates a 100x200 pixel image, increasing `size` increases the size of the output, but not number of pixels.

### `pixel_scale`

This is a scaling multiplier on the _**size**_ of the pixels of the image. The final number of pixels equals `pixel_size/pixel_scale`.

### `pixel_type`

Pixel type can be one of `rect`, `rectshift`, `tri`, `diamond`, `hex`, and `knit`.

![pixel\_type](drawer-settings/pixeltype.png)

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

![vqgan\_model](<drawer-settings/vqgan models.png>)

## clipdraw

### `strokes`

number of strokes, default=1024.

### `min_stroke_width` and `max_stroke_width`

stroke thickness, percentage of image height. default=1 and 5

## line\_drawer

### `strokes`

default=24

### `stroke_length`

defualt=8

### `min_stroke_width` and `max_stroke_width`

default=0.5 and 2

### `allow_paper_color`

default=False, allows change in color of background
