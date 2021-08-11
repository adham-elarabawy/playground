# Anaconda

### Installation

{% embed url="https://www.anaconda.com/distribution/\#macos" %}

### Creating Environment

```bash
conda create -n {env} python={python version}
```

### Entering Environment

```bash
conda activate {env}
```

### Leaving Environment

```bash
conda deactivate
```

### Installing Packages

```bash
conda install {package name}
```

### Installing Virtual Env. as Jupyter Kernel

```bash
pip install --user ipykernel
python -m ipykernel install --user --name=nmep
```

In the menu bar of the jupyter notebook, go to **Kernel &gt; Change Kernel**



