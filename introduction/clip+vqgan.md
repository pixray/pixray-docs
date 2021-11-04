# CLIP+VQGAN

Pixray uses the popular CLIP+VQGAN combo to guide image generation using text. The methodology is through encoding prompts through CLIP, generating embeddings, which are compared against each other to generate a loss that can backpropagate through the networks to learn a representation in VQGAN's latent space, which can generate the desired image through its generator network. 

> WIP, will write more later.

