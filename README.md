![repo-size](https://img.shields.io/github/repo-size/murtazahatim/number-plate-recognition-system)
[![LinkedIn](https://img.shields.io/badge/linkedin-connect-blue)](https://www.linkedin.com/in/murtaza-rangwala-889064160/)
# Number-Plate-Recognition-System

This repo contains MATLAB source code to recognize car number plates using image recognition

## Introduction

Image processing can be seen everywhere in our day-to-day lives. From traffic cameras to mobile phone cameras, all images are processed in some form or the other. One of the most
prominent uses of image processing is to enforce traffic rules. This repository contains codebase that effectively recognizes number plates and converts them into digital text.

This project contains two directories:
* `number_localization_and_segmentation`
* `number_recognition`

The first directory contains a script that is called automatically in the second directory and does not manually need to be run my the user. The second directory uses two different
approaches to number recognition; template matching and machine learning. Scripts for both can be found. Sample images are also provided.

If you wish to use your own images, add them to the `number_localization_and_segmentation/number_plate_images` and follow the naming convention.

More implementation details are given below for the knowledge of the user.

## Localization and Segmentation

This section can be split into three parts; localization of the number plate, skeletonization of the content and segmentation of
the characters. The program flow for this script is as follows:

[![QF8KFY.md.png](https://i.im.ge/2021/08/28/QF8KFY.md.png)](https://im.ge/i/QF8KFY)

Please open the image in a new tab if it's not clear.


## Text Recognition

### I: Template Matching

Template matching is an optical character recognition technique that finds the location of a
template inside a given input image. It involves determining the similarities between a given
dataset of templates and an image of the same size.

The most basic form of template matching involves the following steps:
* Preprocess Input Image
  * Resize Image to the size of the template
  * Add or remove image padding to scale the template in the input image to roughly the same size as the dataset.
* Read all the images in the template dataset and check the correlation between the templates and the input image.
* Store all the correlation values for each template image.
* Select the highest correlation value as the best match and hence, use that template label as the return label.

Matlab contains an inbuilt function called corr2 that takes the input image and template
image as input parameters and returns a similarity score between 0 and 1, where 0 is no
similarities and 1 is complete similarity.

The overall flow of this implementation is given in the flowchart below:

[![QF8VjD.md.png](https://i.im.ge/2021/08/28/QF8VjD.md.png)](https://im.ge/i/QF8VjD)

### II. Machine Learning

Machine Learning for Character Recognition is a Multiclass classification challenge.
Supervised classification involves preprocessing training and testing image datasets,
extracting important features from these images, training the classification model with the
training dataset, and testing the model with the testing dataset.

In this repo, the image dataset used to train the model is the same as the dataset used
for template matching in the previous section. Histogram of Oriented Gradients (HoG) is
used to extract important features from the training and testing image dataset and a Single
Vector Machine (SVM) classifier is trained on the extracted features. This model is then used
to make predictions on input images from the segmented number plates.

The overall flow of this implementation is given in the flowchart below:

[![QF8fR4.md.png](https://i.im.ge/2021/08/28/QF8fR4.md.png)](https://im.ge/i/QF8fR4)

## Installation Instructions

* Open Windows Command Prompt or Bash and clone repo:

`git clone https://github.com/murtazahatim/number-plate-recognition-system.git`
* Open directory in MATLAB
* Run the following livescripts for either approaches: 

`number_recognition/template_matching_approach.mlx` | `number_recognition/machine_learning_approach.mlx`


## Contribute
- Show your support by ⭐ the project.
- Submit pull requests and improve the repo overall quality
