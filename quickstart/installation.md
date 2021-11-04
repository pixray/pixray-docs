---
description: How to install pixray
---

# Installation

{% tabs %}
{% tab title="IPython" %}
These snippets are applicable for Colab users that cannot access the command line.

```python
%%capture
!git clone https://github.com/dribnet/pixray
%cd pixray
!pip install -r requirements.txt
!git clone https://github.com/BachiLi/diffvg && cd diffvg && git submodule update --init --recursive && python setup.py install && cd ..
```

Due to the nature of colab, installing these requirements in a cell requires a runtime restart to properly load all libraries and ensure that pixray runs smoothly. After installation, the cell for installation need not be run again for the rest of the session, even after more runtime restarts. 

After restarting every time, this line should be run to ensure that the python interpreter knows where to find the pixray module.

```python
import sys
sys.path.append("pixray")
```

a simple working snippet for Colab may be: (note that pixray also needs a models directory, at the moment unfortunately)

```python
#@title Setup
#@markdown run once and restart runtime, then run again
import os, sys
if not os.path.isfile("/content/first_init_complete"):
    !git clone https://github.com/dribnet/pixray
    !pip install -r pixray/requirements.txt
    !git clone https://github.com/BachiLi/diffvg && cd diffvg && git submodule update --init --recursive && python setup.py install && cd ..
    os.mknod("/content/first_init_complete")
    if not os.path.isdir("models"):
        os.mkdir("models")
else:
    sys.path.append("pixray")
```
{% endtab %}

{% tab title="bash" %}
This is the basic setup for pixray

```
git clone https://github.com/dribnet/pixray
cd pixray
pip install -r requirements.txt

git clone https://github.com/BachiLi/diffvg 
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
