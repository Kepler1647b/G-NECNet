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
- Typical installation time: 1 hour

### preprocess dataset for training
we use the python files to convert the WSI to patches with size 512*512 pixels and taking color normalization (optimal) as preprocessing.

The files are in ./preprocessing:
```
- generate_patch.py
- Vahadane/main.py
```

### train model for tumor detecting 
- To run the detector_train.py

```bash
python detector_train.py --TrainFolder './tumorfolder' --TrainFolder2 './normalfolder' --Comment 'resnet50,LR0.001,Decay0.0005' --FoldN 1 --Pretrain
```

### evaluate model
```bash
python detector_test.py --TrainFolder './datafolder' --FoldN 1

```

### classify the type of tumor
After separating the tumor region patch from the slide bag,we using the tumor patch to training a model
that could predicting the type of the tumor.

the datas' organizing way is showed in /EBV_classifier/data, you can run:

```bash
python classifier_train.py --TrainFolder './trainfolder'  --Comment 'resnet50,epoch100,10x,Vahadane' --Pretrain --FoldN 1
```

### evaluate model
```bash
python classifier_test.py --TrainFolder './testfolder' --FoldN 1