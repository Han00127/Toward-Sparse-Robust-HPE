# Toward-Sparse-HPE
This project aims to make head pose estimation without face detection in sparse dataset and robust to occlusion.
This project is the term project for AI convergence project at Inha University with Suprema. 

## Description
Our Head Pose Esitmation (HPE) achieves proper performance and robustness in sparse and masked dataset without using face detection. The details of our project are summarized as follows: 
1. Sparse model architecture based on Retina-Face.
2. Newly generated masked data only for HPE.
3. Trained model with diverse dataset
4. Newly generated rotated dataset in range -45 degree to 45 degree. 

## Trained Results
<p align="center">
  <img align="center" src="./figures/training_result2.gif" width="400">
</p>
<p align="center">
  Fig. 1 - Result of our trained model. 
  
  |Model|Dataset|Yaw|Pitch|Roll|MAE|
  |---|---|---|---|---|---|
  |Our|BIWI|5.43|4.17|3.74|4.45|
  |Our|BIWI_masked|4.45|2.97|2.90|3.44|
</p>

## Masked Images 
<p align="center">
  <img align="center" src="./figures/Screenshot from 2022-04-25 14-24-31.png" width="400">
</p>
<p align="center">
  Fig. 2 - Masked image generation. 
</p>

## Rotated Images 
<p align="center">
  <img align="left" src="./figures/45_dgree_change.gif" width="200">
  <img align="center" src="./figures/original.gif" width="200">
  <img align="right" src="./figures/-45_degree_change.gif" width="200">
</p>
<p align="center">
  Fig. 3 - Rotated image examples -45, 0, 45 degree.
</p>

### Distribution
<p align="center"> 
  <img align="center" src="./figures/orig_dist.png" width="300"> &nbsp; &nbsp; &nbsp;
  <img align="center" src="./figures/changed_dist.png" width="300">
</p>
&NewLine;
<p align="center">
  Fig. 4 - left : original distribution of BIWI data, right: rotated distribution of BIWI in range [45,-45] degrees
</p>
&NewLine;

## Quick start
* Please go to [here](https://bridge-aix.inha.ac.kr/studio/preview?projectId=48&token=eyJhbGciOiJIUzI1NiJ9.OA.LkEQgaZ3g67mvxL2PYlV6pGn5N6WRBCjwqbTR7Jml6E&nodeName=master).

## Get Started 
Please set requirments.txt to virtual environment or conda. 
### Requirements

*   torch==1.5.1 cu102
*   torchvision==0.6.1
*   numpy>=1.15.0
*   pillow>=8.1.0
*   scipy=1.7.3

### Preparing datasets
Download datasets:
* **300W-LP**, **AFLW2000** from [here](http://www.cbsr.ia.ac.cn/users/xiangyuzhu/projects/3DDFA/main.htm).
* 
* **BIWI** (Biwi Kinect Head Pose Database) from [here](https://icu.ee.ethz.ch/research/datsets.html) 
Store them in the *datasets* directory.
For 300W-LP and AFLW2000 we need to create a *filenamelist*. 
```
python 300_create_filenae_list.py --root_dir datasets/300W_LP
```
### Training
Every dataset should contains HPE, Landmark, Bounding box labels. Please check this out.
```
python 300_create_filenae_list.py --root_dir datasets/300W_LP
```
For training 
```
python3 train.py --dataset BIWI --batch_size 32 --epoch 50 --num_workers 1
```
### Test 
For testing
```
python3 test.py -m ./weights/BIWI/BIWI__Resnet50_Final.pth --dataset BIWI --num_workers 1
```
## Notification
We are not able to upload all dataset and final presentation file due to uploading constraint in Github. We upload the pdf version presentation files, it can be found in /presentation/final_ppt.pdf.
If you have any concerns about dataset and presentation files, please email me. 

## Authors
Kyeontak Han, Sujung Kim


