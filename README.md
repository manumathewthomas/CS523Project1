# Neural Style Transfer
<b>!!!CAUTION - At the time we modified this project it was tensorflow v0.12 and now it's tensorflow v1.1. We could not run this project on the latest tensorflow version since a lot has changed. Try at your own risk!!!</b>

## Introduction
Style transfer is the task of producing a pastiche image 'p' that shares the
content of a content image 'c' and the style of a style image 's'. This code
implements the paper "A Learned Representation for Artistic Style":

[A Learned Representation for Artistic Style](https://arxiv.org/abs/1610.07629). *Vincent Dumoulin, Jon Shlens,
Manjunath Kudlur*.

#### Table of Contents

* [Installation](#installation)
* [Running](#running)
* [Dataset](#dataset)
* [Results](#results)
* [Improvements](#improvements)
* [Credits](#credits)

## Installation

To run the project you will need:
 * python 2.7
 * jupyter notebook
 * tensorflow (v0.12)
 * [CKPT FILE monet](http://download.magenta.tensorflow.org/models/multistyle-pastiche-generator-monet.ckpt)
 * [CKPT FILE varied](http://download.magenta.tensorflow.org/models/multistyle-pastiche-generator-varied.ckpt)
 * [CKPT FILE From our training](https://uofi.box.com/shared/static/21a5jwdiqpnx24c50cyolwzwycnr3fwe.gz)


## Running

To run this project, you need to setup google's magenta enviornment. Please see https://github.com/tensorflow/magenta for more info about installing magenta. There are different options to setup the enviornment
  * manually install with pip and anaconda
  * autoinstall with anaconda
  * docker setup - This worked for us.
  
## Dataset
For the training we did, we used Japanese art sytle image randomly picked from the internet.
<img src="https://github.com/manumathewthomas/CS523Project1/blob/master/dataset.PNG" alt="alt text" width="850" height="500">


## Results
Since we this was intended to run on a CPU we only trained it for 100 iterations.
* Input
<img src="https://github.com/manumathewthomas/CS523Project1/blob/master/input.PNG" alt="alt text" width="850" height="500">

* Output
<img src="https://github.com/manumathewthomas/CS523Project1/blob/master/output.PNG" alt="alt text" width="850" height="500">

## Improvements
* Train for a longer period of time
* Ability to select multiple styles for one Image

## Credits
[Google Magenta](https://magenta.tensorflow.org/welcome-to-magenta)

