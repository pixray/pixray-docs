---
description: Text to image generation
---

# Generating an Image

For the pixray module, the base case for generation looks like this:

```
import pixray
pixray.reset_settings()
pixray.add_settings(prompts="hellfire burning")
settings = pixray.apply_settings()
pixray.do_init(settings)
pixray.do_run(settings)
```

