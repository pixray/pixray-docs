---
description: A simple explanation for what happens under the scene.
---

# Introduction to Pixray

The main function of Pixray is the use of CLIP to guide image generation from text.&#x20;

Pixray uses CLIP (Contrastive Language-Image Pre-Training) by OpenAI as its perception engine. Check out CLIP's [official repository](https://github.com/openai/CLIP) and [paper (Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/abs/2103.00020)) to learn more about CLIP.

The vqgan drawer uses Vector Quantized Generative Adversarial Networks, or simply VQGAN, by Esser et al. from the paper [Taming Transformers for High-Resolution Image Synthesis](https://arxiv.org/abs/2012.09841). The original code for VQGAN is in[ this repository](https://github.com/CompVis/taming-transformers).&#x20;

The clipdraw drawer uses [ClipDraw](https://github.com/kvfrans/clipdraw/) by [Kevin Fran](https://github.com/kvfrans/)s, from the paper [CLIPDraw: Exploring Text-to-Drawing Synthesis through Language-Image Encoders](https://arxiv.org/abs/2106.14843).&#x20;

The diffusion drawer uses [Diffusion models](https://arxiv.org/abs/2006.11239), and models are trained by [Katherine Crowson](https://github.com/crowsonkb). The code we use for diffusion is in [this repository](https://github.com/crowsonkb/v-diffusion-pytorch).

The fft drawer is from the Aphantasia library by [vadim epstein](https://github.com/eps696/). The original code for fft drawer is in [this repository](https://github.com/eps696/aphantasia).&#x20;

The pixel drawer is created by [dribnet](https://github.com/dribnet/), the author of pixray.

The algorithm for generation is encoding prompts through CLIP, generating embeddings, which are compared against the output image for a loss that can backpropagate through the generation engine to learn a latent space that can minimize the loss. This minimal loss result is the output that most resembles the text which it was prompted.

The difference between the drawers lies between how the image itself is generated, and what the latent space of the model represents. It is possible to generate an image without an underlying model, but simply optimizing a tensor.
