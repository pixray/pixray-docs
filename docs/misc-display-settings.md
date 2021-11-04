# Misc/Display settings

### `output_name`

> Default: `output.png`

Specifies name of output, note that for command line its actually just `--output`



### `display_every`

> Default: `20`

Display frequency. Sometimes displays at half the frequency. IDK why.



### `display_clear`

> Default: `False`

If on the colab it clears the output whenever there is a new image. I'd recommend keep this `False` and check the init variables and intermediate steps for good measure.



### `make_video`

> Default: `False`

Make a 15 second video with intermediate frames. Currently its hard coded for now. Here's a code snippet you can use to specify fps.

```python
#@title frames->video (make_video custom fps)

import cv2
import numpy as np
import glob
import os
from tqdm.notebook import tqdm
from PIL import Image

fps =    24#@param 
folder_name = "steps/" #@param
video_name = "output.mp4" #@param 
frames = glob.glob(folder_name+"*.png")
frames.sort()
frames = [cv2.imread(fn) for fn in frames]

height, width, layers = frames[0].shape
size = (width,height)
out = cv2.VideoWriter(video_name,cv2.VideoWriter_fourcc(*'MP4V'),fps,size)
 
for i in tqdm(frames):
    out.write(i)
out.release()

import warnings
from moviepy.editor import *
warnings.filterwarnings('ignore')
clip=VideoFileClip(video_name)
ipython_display(clip)
```





