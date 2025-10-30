# G-NECNet
The source code of article 'G-NECNet: A Deep Learning Model for the Detection of Gastric Neuroendocrine Carcinoma'.

## System requirements
This code was developed and tested in the following settings. 
### OS
- Ubuntu 20.04
### GPU
- Nvidia GeForce RTX 2080 Ti
### Dependencies
- Python (3.9.6)
- Pytorch install = 1.9
- torchvision (0.6)
- CUDA (10.1)
- tensorboardX (2.4)
- Other dependencies: Openslide (3.4.1), matplotlib (3.1.1), numpy (1.18.1), opencv-python (4.1.1), pandas (1.0.3), pillow (7.0.0), scikit-learn (0.22.1), scipy (1.3.1)

## Installation guide

- Install [Miniconda](https://docs.conda.io/en/latest/miniconda.html#linux-installers) on your machine (download the distribution that comes with python3).  
  
- After setting up Miniconda, install OpenSlide:  
```
apt-get install openslide-python
```
- Create a conda environment with my_env.yaml:
```
conda env create -f my_env.yaml
```  
- Activate the environment:
```
conda activate env1
```

