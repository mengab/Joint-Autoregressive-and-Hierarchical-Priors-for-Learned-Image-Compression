# Joint-Autoregressive-and-Hierarchical-Priors-for-Learned-Image-Compression
This is a personal reimplementation of NIPS2018 paper: D. Minnen et al. "Joint Autoregressive and Hierarchical Priors for Learned Image Compression".  We achieved almost the same results as in the paper.

Paper  [[ArXiv]](https://arxiv.org/abs/1809.02736) | [[NIPS2018]](https://papers.nips.cc/paper/8275-joint-autoregressive-and-hierarchical-priors-for-learned-image-compression.pdf)

## Installation

- Anaconda

This creates an Anaconda environment with Python 3.6 and CUDA libraries, and then installs TensorFlow and tensorflow-compression with GPU support:
```bash
conda create --name py36 python=3.6 cudatoolkit=10.0 cudnn
conda activate py36
pip install tensorflow-gpu==1.15 tensorflow-compression
```

## Usage
Importing the library from your Python code as follows:

```python
import tensorflow as tf
import tensorflow_compression as tfc
```

### Using a pre-trained model to compress an image 

Download the file and run:
```bash
python tfci.py -h
```

This will give you a list of options. Briefly, the command
```bash
python tfci.py compress <model> <PNG file>
```
will compress an image using a pre-trained model and write a file ending in
`.tfci`. Execute `python tfci.py models` to give you a list of supported
pre-trained models. The command
```bash
python tfci.py decompress <TFCI file>
```
will decompress a TFCI file and write a PNG file. By default, an output file
will be named like the input file, only with the appropriate file extension
appended (any existing extensions will not be removed).

### Training your own model
To train the model, you need to supply it with a dataset of RGB training images.
They should be provided in PNG format. Training can be as simple as the
following command:
```bash
python joint_NIPS2018.py --verbose train --train_glob="images/*.png"
```
