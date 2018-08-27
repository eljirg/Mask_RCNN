# Mask_RCNN
Implementation of mask rcnn for accomplishing instance segmentation tasks, based on https://github.com/matterport/Mask_RCNN work

### Preparation
1. prepare environment with tensorflow-gpu installed
2. copy this repository
3. install necessary requirements
4. install pycocotools (pip3 install git+https://github.com/waleedka/coco.git#subdirectory=PythonAPI)
5. go to the repo folder you copied run (python3 setup.py install)

### Customization notes:

There are two places where most of customization can be done:
1. damage.py which hold the configuration of model
2. mrcnn files, especially model.py which hold the default configuration of model (in order for change to take places in case you modify this file, you need to re do the step 5 of preparation.

### Dataset making
To make the dataset I used the labelme image annotation tool that can be obtained here, however i used the VIA format in order for the model to read the dataset, therefore it is bridged by a code i wrote.

The image annotation tool can be seen here: https://github.com/wkentaro/labelme

### Steps
Training model:
- To train the model you can use this setup:
  - `CUDA_VISIBLE_DEVICES=0 python3 Damage/damage.py train --dataset datasets/sample_4/ -- weights=coco --logs=logs`

- To train the model from previous model you can change the weights by using the last checkpoint
  - `CUDA_VISIBLE_DEVICES=0 python3 Damage/damage.py train --dataset datasets/sample_4/ --weights=logs/damage20180802T1704/mask_rcnn_damage_0600.h5 --logs=logs`

To Splash color on image:
- `CUDA_VISIBLE_DEVICES=0 python3 Damage/damage.py splash --image datasets/sample_4/val -- weights=logs/damage20180802T1704/mask_rcnn_damage_0900.h5 --output=datasets/sample_4/splash/model_x/val`

To Splash color on video:
- `CUDA_VISIBLE_DEVICES=0 python3 Damage/damage.py splash --video datasets/sample_4/val -- weights=logs/damage20180802T1704/mask_rcnn_damage_0900.h5 --output=datasets/sample_4/splash/video/ --Add_bbox=True`

To Show loss using tensorboard:
- `CUDA_VISIBLE_DEVICES='' tensorboard --logdir=logs`

### To add ###
1. folder:
   a. video
   b. log
   c. splash
   d. gt
2. 
