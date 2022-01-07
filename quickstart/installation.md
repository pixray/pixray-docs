---
description: How to install pixray
---

# Installation

{% tabs %}
{% tab title="IPython" %}
These snippets are applicable for Colab users that cannot access the command line.

```python
!git clone https://github.com/pixray/pixray
%cd pixray
!pip install -r requirements.txt
!git clone https://github.com/pixray/v-diffusion-pytorch
!cp -r v-diffusion-pytorch/diffusion pixray/.
!git clone https://github.com/pixray/diffvg && cd diffvg && git submodule update --init --recursive && python setup.py install && cd ..
```

Due to the nature of colab, installing these requirements in a cell requires a runtime restart to properly load all libraries and ensure that pixray runs smoothly. After installation, the cell for installation need not be run again for the rest of the session, even after more runtime restarts.

After restarting every time, this line should be run to ensure that the python interpreter knows where to find the pixray module.

```python
import sys
sys.path.append("pixray")
```

a simple working snippet for Colab may be: (note that pixray also needs a models directory, at the moment unfortunately)

```python
from IPython.utils import io
with io.capture_output() as captured:
  !rm -Rf pixray
  !git clone https://github.com/pixray/pixray
  !pip install -r pixray/requirements.txt
  !rm -Rf v-diffusion-pytorch
  !git clone https://github.com/pixray/v-diffusion-pytorch
  # not sure why this setup hack is necessary
  !cp -r v-diffusion-pytorch/diffusion pixray/.
  !pip uninstall -y tensorflow 
  !git clone https://github.com/pixray/diffvg
  %cd diffvg
  !git submodule update --init --recursive
  !python setup.py install
  %cd ..
  !pip freeze | grep torch
import os
if not os.path.isfile("first_init_complete"):
  !mkdir -p models
  os.mknod("first_init_complete")

```
{% endtab %}

{% tab title="bash" %}
This is the basic setup for pixray

```
git clone https://github.com/pixray/pixray
cd pixray
pip install -r requirements.txt
git clone https://github.com/pixray/v-diffusion-pytorch
cp -r v-diffusion-pytorch/diffusion pixray/.
git clone https://github.com/pixray/diffvg 
cd diffvg 
git submodule update --init --recursive 
python setup.py install 
cd ...
mkdir models
```
{% endtab %}
{% endtabs %}

Note: if diffvg is not installed, pixray can still be used for vqgan generation

Note: pixray works well with 16GB RAM, working with less RAM is fine, but see [Working with weaker machines](../tutorial/working-with-weaker-machines.md) for detailed solutions.
