# FAQ

1. [Why do I keep getting "CUDA out of memory" errors?](#memory)
2. [How can I get this working on an AMD GPU?](#amd)
3. [What kind of royalties can I expect to pay?](#royalties)
4. [Why is my custom palette being ignored?](#palette)
5. [I'm having issues on Colab. What should I do?](#colab)


## Why do I keep getting "CUDA out of memory" errors?<a name="memory"></a>

Pixray generally requires a minimum of 8GB VRAM (with at least 16GB recommended for the best experience). If you do have enough VRAM, you can try any or all of the following: reducing the `quality` setting; reducing the `size`/`scale` of the image; reducing `num_cuts` and increase `batches` to compensate.

## How can I get this working on an AMD GPU?<a name="amd"></a>

Unfortunately, Pixray relies on CUDA and therefore currently only works on Nvidia GPUs. You can try running in CPU mode or using a provider like Colab.

## What kind of royalties can I expect to pay?<a name="royalties"></a>

Feel free to reach out in the #royalties channel on Discord or to dribnet if you have any specific questions about your use case. Generally speaking, the following guidelines apply:

### NFTs
"...For NFT projects pixray requests 5% of initial sales and 0.5% of resales to find further development and support server costs in making the online tools available for free. There are wallet addresses for various blockchains in the USE file in the repo; it is preferred that payments be done contractually and on-chain but if your platform does not support that then retroactive payments can be done by transfers..." - dribnet

### Other Art Projects

"Currently for commercial projects that don't end up in the NFT market we are happy with attribution only..." - dribnet

## Why is my custom palette being ignored?<a name="palette"></a>

In order to use a custom palette, you also need to set `filters` to `lookup`.

## I'm having isuses on Colab. What should I do?<a name="colab"></a>

Colab can be a little finicky at times. Trying to `Restart Runtime` or `Factory Reset Runtime` can often solve transient issues. Using Colab Pro can also help with some issues you might encounter. If all else fails, feel free to reach out to the #debugging channel on Discord.
