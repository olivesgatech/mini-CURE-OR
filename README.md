# mini-CURE-OR

 [OLIVES Lab, Georgia Institute of Technology](https://ghassanalregib.info/)


<p align="center"><img src="./figs/cure_or_lr.gif", width="500"></p>


This repository contains the description and the link to a subsampled version of the original CURE-OR dataset. The goal of this project is to analyze the robustness of off-the-shelf recognition applications under multifarious challenging conditions, investigate the relationship between the recognition performance and image quality, and estimate the performance based on hand-crafted features as well as data-driven features. To achieve this goal, we introduced a large-scale, controlled, and multi-platform object recognition dataset CURE-OR, which stands for Challenging Unreal and Real Environments for Object Recognition. For more information about CURE-OR, please refer to our papers.

### Papers
If you use CURE-OR dataset and/or these codes, please cite:

 [CURE-OR: Challenging Unreal and Real Environments for Object Recognition](https://arxiv.org/pdf/1810.08293.pdf)
  
```
  @inproceedings{Temel2018_ICMLA,
author      = {D. Temel and J. Lee and G. AlRegib},
booktitle   = {2018 17th IEEE International Conference on Machine Learning and Applications (ICMLA)},
title       = {CURE-OR: Challenging unreal and real environments for object recognition},
year        = {2018},}
```
   
 [Object Recognition Under Multifarious Conditions: A Reliability Analysis and A Feature Similarity-Based Performance Estimation](https://arxiv.org/pdf/1902.06585.pdf)

```
@INPROCEEDINGS{Temel2019_ICIP,
author      = {D. Temel and J. Lee and G. AIRegib},
booktitle   = {IEEE International Conference on Image Processing (ICIP)},
title       = {Object Recognition Under Multifarious Conditions: A Reliability Analysis and A Feature Similarity-Based Performance Estimation},
year        = {2019},}
```
 
### Download Dataset
In the original CURE-OR dataset, there are 1,000,000 images of 100 objects with varying size, color, and texture, captured with multiple devices in different setups. In the sampled version, there are a total of 16,500 images in train and test sets distributed over ten classes. For each class, there exists training image samples for three backgrounds, five camera angles, 18 different challenge types, and 5 levels of challenge. To download the dataset, please head over to the following [link](https://zenodo.org/record/4268901#.X61drmhKhPY).
 
### File Descriptions
* train.zip - the training set
* test.zip - the test set
* train.csv - the ground truth for the training images with the following information: imageID, class, background, perspective, challengeType, challengeLevel
* test.csv -  the ground truth for the training images with the following information: imageID, class, background, perspective, challengeType, challengeLevel



<b>background</b><b>ID</b><b>:</b>

1. White
2. Texture 1 - living room
3. Texture 2 - kitchen


<b>objectOrientation</b><b>ID</b><b>:</b>

1. Front (0 º)
2. Left side (90 º)
3. Back (180 º)
4. Right side (270 º)
5. Top

<b>objectID</b><b>:</b>
1. Canon camera
2. Training marker cone
3. Baseball
4. Pan
5. Toy
6. LG Cell phone
7. Hair brush
8. DYMO Label maker
9. Calcium bottle
10. Shoes


<b>challengeType</b><b>:</b>

01. No challenge
02. Resize
03. Underexposure
04. Overexposure
05. Gaussian blur
06. Contrast
07. Dirty lens 1
08. Dirty lens 2
09. Salt & pepper noise
10. Grayscale
11. Grayscale resize
12. Grayscale underexposure
13. Grayscale overexposure
14. Grayscale gaussian blur
15. Grayscale contrast
16. Grayscale dirty lens 1
17. Grayscale dirty lens 2
18. Grayscale salt & pepper noise

<b>Challenge Level</b><b>:</b>

A number between 0 and 5, where 0 indicates no challenge, 1 the least severe and 5 the most severe challenge. Challenge type 1 (no challenge) and 10 (grayscale) has a level of 0 only. Challenge types 2 (resize) and 11 (grayscale resize) has 4 levels (1 through 4). All other challenges have levels 1 to 5.
<h3></h3>

### Challenging Conditions Generation
Python Imaging Library (PIL) version 4.2.1 and scikit-image version 0.13.0 are utilized to generate challenging conditions. Salt and pepper noise is synthesized with scikit-image and all other challenging conditions are simulated with PIL. The minimum and maximum parameter values for each challenge type except dirty lens 2 and grayscale are provided below, and parameter values are linearly spaced between the two for different challenge levels.
<ul>
	<li>Resize: downsample with bicubic interpolation; the size of a new image is determined by multiplying pixel dimensions of an original image by factors linearly spaced between 1 (exclusive) and 0.5 (inclusive)</li>
	<li>Underexposure: brightness control with factors between 0.4 and 0.08</li>
	<li>Overexposure: brightness control with factors between 1.4 and 6</li>
	<li>Gaussian blur: radius of blur between 8 and 60</li>
	<li>Contrast: increase separation between dark and bright colors on spectrum by factors between 2 and 5</li>
	<li>Dirty lens 1: blends a single dirty lens pattern into an image with weights values between 0.2 and 0.65</li>
	<li>Dirty lens 2: overlays a distinct dirt pattern onto an image for each challenge level</li>
	<li>Salt & pepper noise: replaces random pixels of an image with either one or zero, with amount between 0.2 and 0.9</li>
	<li>Grayscale: convert an image into monochrome</li>
</ul>

To access the complete dataset and associated files, please refer to [link](https://github.com/olivesgatech/CURE-OR).
