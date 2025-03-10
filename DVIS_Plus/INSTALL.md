## Installation

### Requirements
- Python ≥ 3.6
- PyTorch ≥ 1.9 and [torchvision](https://github.com/pytorch/vision/) that matches the PyTorch installation.
  Install them together at [pytorch.org](https://pytorch.org) to make sure of this. Note, please check
  PyTorch version matches that is required by Detectron2.
- Detectron2: follow [Detectron2 installation instructions](https://detectron2.readthedocs.io/tutorials/install.html).
- OpenCV is optional but needed by demo and visualization
- Panopticapi: `pip install git+https://github.com/cocodataset/panopticapi.git`
- `pip install -r requirements.txt`

### CUDA kernel for MSDeformAttn (Skip this step)
After preparing the required environment, run the following command to compile CUDA kernel for MSDeformAttn:

`CUDA_HOME` must be defined and points to the directory of the installed CUDA toolkit.

```bash
cd mask2former/modeling/pixel_decoder/ops
sh make.sh
```

### Example conda environment setup (Skip this step)
```bash
conda create --name dvis python=3.8 -y
conda activate dvis
pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 torchaudio==0.9.0 -f https://download.pytorch.org/whl/torch_stable.html
pip install -U opencv-python

# install detectron2
python -m pip install detectron2 -f \
  https://dl.fbaipublicfiles.com/detectron2/wheels/cu111/torch1.9/index.html

# install panoptic api
pip install git+https://github.com/cocodataset/panopticapi.git

git clone https://github.com/zhang-tao-whu/DVIS_Plus.git
cd DVIS_Plus
cd DVIS_Plus
pip install -r requirements.txt
cd mask2former/modeling/pixel_decoder/ops
sh make.sh
```

### Example pip .env environment setup (COMPLETE THIS STEP)
```bash
python3 -m venv .env

source .env/bin/activate

# Get most recent version of pytorch (may not work forever, we'll see) compatible w/ CUDA 12.x
# There are 2 versions of CUDA, 11.5 (native) and 12.1 (/usr/local/cuda-12.1)
# To use the pytorch version compatible w/ CUDA 11.x, we NEED gcc/g++ 10. Otherwise, Detectron2 fails to
# compile from source using the command give later.
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# Read the paragraph above to understand why we need this line. This helps Detectron2 build using the proper CUDA.
export CUDA_HOME=/usr/local/cuda-12.1

# Build Detectron2 from source
python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'

# install panoptic api
pip install git+https://github.com/cocodataset/panopticapi.git

# install relevant dependencies
cd DVIS_Plus
pip install -r requirements.txt

cd mask2former/modeling/pixel_decoder/ops
sh make.sh
```
