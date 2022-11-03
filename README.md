# CPCStoryVisualization-Pytorch (ECCV 2020)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/character-preserving-coherent-story/story-visualization-on-pororo)](https://paperswithcode.com/sota/story-visualization-on-pororo?p=character-preserving-coherent-story)

![](https://raw.githubusercontent.com/basiclab/CPCStoryVisualization-Pytorch/master/images/introduction4.jpg)

Author: [@yunzhusong](http://github.com/yunzhusong), [@theblackcat102](http://github.com/theblackcat102), [@redman0226](http://github.com/redman0226), Huiao-Han Lu, Hong-Han Shuai

[Paper Link (ECCV 2020)](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123620018.pdf)

[Organization](https://github.com/basiclab/CPCStoryVisualization-Pytorch)

Code implementation for Character-Preserving Coherent Story Visualization


```
Objects in pictures should so be arranged as by their very position to tell their own story.
           - Johann Wolfgang von Goethe (1749-1832)
```

In this paper we propose a new framework named Character-Preserving Coherent Story Visualization (CP-CSV) to tackle the challenges in story visualization: generating a sequence of images that emphasizes preserving the global consistency of characters and scenes across different story pictures.


CP-CSV effectively learns to visualize the story by three critical modules: story and context encoder (story and sentence representation learning), figure-ground segmentation (auxiliary task to provide information for preserving character and story consistency), and figure-ground aware generation (image sequence generation by incorporating figure-ground information). Moreover, we propose a metric named Frechet Story Distance (FSD) to evaluate the performance of story visualization. Extensive experiments demonstrate that CP-CSV maintains the details of character information and achieves high consistency among different frames, while FSD better measures the performance of story visualization. The FVD evaluation metric is from [here](https://github.com/google-research/google-research/tree/master/frechet_video_distance).

## Datasets
1. PORORO images and segmentation images can be downloaded [here](https://drive.google.com/file/d/1p_8xTivhjs0OaQ2vlQjd15qA7OKYsG4y/view?usp=sharing). Pororo, original pororo datasets with self labeled segmentation mask of the character.

2. CLEVR with segmentation mask, 13755 sequence of images, generate using [Clevr-for-StoryGAN](https://github.com/theblackcat102/Clevr-for-StoryGAN)

```
images/
    CLEVR_new_013754_1.png
    CLEVR_new_013754_1_mask.png
    CLEVR_new_013754_2.png
    CLEVR_new_013754_2_mask.png
    CLEVR_new_013754_3.png
    CLEVR_new_013754_3_mask.png
    CLEVR_new_013754_4.png
    CLEVR_new_013754_4_mask.png
```

Download [link](https://drive.google.com/file/d/1w6z6VAcJiLwXK0tm6J84RqzERGxmBY24/view?usp=sharing)

## Setup environment

```
    virtualenv -p python3 env
    source env/bin/activate
    pip install -r requirements.txt
```


## Train CPCSV

### Steps

1. Download the Pororo dataset and put at **DATA_DIR**, [downloaded](https://drive.google.com/file/d/1p_8xTivhjs0OaQ2vlQjd15qA7OKYsG4y/view?usp=sharing). The dataset should contain SceneDialogues/  ( where gif files reside ) and *.npy files.

2. Modify the **DATA_DIR** in _./cfg/final.yml_

3. The dafault hyper-parameters in _./cfg/final.yml_ are set to reproduce the paper results. To train from scratch:

```
./script.sh
```

4. To run the evaluation, specify the _--cfg to ./output/yourmodelname/setting.yml_, e.g.,:

```
./script_inference.sh
```

## Evaluate CPCSV

Pretrained model can be download [here](https://drive.google.com/drive/folders/1yqiUci54LvB0yG43oN2JoVjOdlRMeKGt?usp=sharing). 

### Steps

1. Download the Pororo dataset and put at **DATA_DIR**, [downloaded](https://drive.google.com/file/d/1p_8xTivhjs0OaQ2vlQjd15qA7OKYsG4y/view?usp=sharing). The dataset should contain SceneDialogues/  ( where gif files reside ) and *.npy files.

2. Modify the **DATA_DIR** in _./cfg/final.yml_

3. To evaluate FID, FSD of the pretrained model:

```
./script_inference.sh
```

## Tensorboard

Use the tensorboard to check the results.

```
    tensorboard --logdir output/ --host 0.0.0.0 --port 6009
```

## The slide and the presentation video:
The slide and the presentation video can be found in [slides](https://drive.google.com/drive/folders/1r0vZMNd2jRK0JN4VAgWfvhVjajq-w_E8?usp=share_link).


## Cite

```
@inproceedings{song2020CPCSV, 
    title={Character-Preserving Coherent Story Visualization},  
    author={Song, Yun-Zhu and Tam, Zhi-Rui and Chen, Hung-Jen and Lu, Huiao-Han and Shuai, Hong-Han},  
    booktitle={Proceedings of the European Conference on Computer Vision (ECCV)},  
    year={2020} 
}
```
