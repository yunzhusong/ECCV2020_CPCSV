# ECCV2020_CPCSV

### The pretrained model:
The pretrained model can be downlond from https://drive.google.com/drive/folders/1Oy-Npt19hYvrGAB_u5c_XYnuBsoBu34b?usp=sharing.

### The Dataset:
The Pororo dataset and the segmentation images can be download from https://drive.google.com/drive/folders/1Oy-Npt19hYvrGAB_u5c_XYnuBsoBu34b?usp=sharing.


## Setup

```
    virtualenv -p python3 env
    source env/bin/activate
    pip install -r requirements.txt
```


Create a environment file .env with the following line:

```
DATAPATH = "PATH TO pororoSV/"
```

## File placement 

pororoSV should contain SceneDialogues/  ( where gif files reside ) and *.npy files

1. setup image for video dataloader

```
    python preprocess_pororo.py
```

2. Segment results should placed under DATAPATH and rename as img_segment 



3. Change related directory PORORO_PATH, etc





## Try to run main_pororo.py and good luck

## Tensorboard

```
    tensorboard --logdir output/ --host 0.0.0.0 --port 6009
