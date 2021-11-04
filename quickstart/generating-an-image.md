---
description: Text to image generation
---

# Generating an Image

For the pixray module, the simplest case for generation looks like this:

```python
import pixray
pixray.reset_settings()
pixray.add_settings(prompts="hellfire burning")
settings = pixray.apply_settings()
pixray.do_init(settings)
pixray.do_run(settings)
```

Now, what did the code do?

The first line imported pixray, which was added to the system path previously during installation.

Then, it reset its settings, clearing any previous settings, if any.

Then, through the `pixray.add_settings()` method, we can pass in arguments that pixray can use to guide and specify how to generate those images. More possible arguments and how to use them, as well as its purpose and effect can be found in [Docs](../docs/primary-settings.md)

We generate all settings, including defaults, in a namespace, which can be saved and used to initialize pixray again. (WARNING: this actually does not do this, and apply_settings actually modifies globals oof ouch)

Now with `settings`, we can initialize pixray's session (global) settings, and run pixray based on them.

By default, the WxH for an image is 384x208, and it runs for 250 iterations on VQGAN. Expected output may look like this:

<img src="generating-an-image/download%20-%202021-11-01T214340.344.png"/>

