# Style Transfer
<b>!!!CAUTION - At the time we modified this project it was tensorflow v0.12 and now it's tensorflow v1.1. We could not run this project on the latest tensorflow version since a lot has changed.</b>

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
* [Hyperparameters](#hyperparameter)
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

To run this project, you need to setup google's magenta enviornment


