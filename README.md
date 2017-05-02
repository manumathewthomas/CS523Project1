# Neural Style Transfer
<b>!!!CAUTION - At the time we modified this project it was tensorflow v0.12 and now it's tensorflow v1.1. We could not run this project on the latest tensorflow version since a lot has changed. Try at your own risk!!!</b>

## Introduction
Style transfer is the task of producing a pastiche image 'p' that shares the
content of a content image 'c' and the style of a style image 's'. This code
implements the paper "A Learned Representation for Artistic Style":

[A Learned Representation for Artistic Style](https://arxiv.org/abs/1610.07629). *Vincent Dumoulin, Jon Shlens,
Manjunath Kudlur*.

In this project we ran a model of style transfer from the Magenta project by Google brain team. Magenta is developed by Google to generate art and music using machine learning. The model image_stylization is an implementation of the paper “A Learned Representation for Artistic Style” by Vincent Dumoulin, Jon Shlens and Manjunath Kudlur. Below we briefly describe the running and usage of the model to stylize images. 


#### Table of Contents
 
* [Installation](#installation)
* [Running](#running)
* [Dataset](#dataset)
* [Model](#Model explanations)
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
  
After installing the enviornment run the nst notebook file.
  
## Dataset
For the training we did, we used Japanese art sytle image randomly picked from the internet.
<img src="https://github.com/manumathewthomas/CS523Project1/blob/master/dataset.PNG" alt="alt text" width="850" height="500">

## Model 
The model trains the network to create an image that is similar in content to content-image and similar in style to style-image. The Euclidian distance between the high-level features measures the content similarity between content-image and generated image. While the style similarity is estimated by reducing the differences between features’ Gram matrices of the style-image and generated image.  

## Main modules and functions
* Create dataset (module) 
It’s a module to create a dataset out of a list of style images. It reads structured directory of images and convert it into tensorflow record that can be read by the model. For each style in the dataset, it stores the style image as a JPEG string, a unique style label and the pre-computed Gram matrices. 

* Image stylization train (module)
Trains the N styles style transfer model. It takes set of style images along with imagenet inputs and construct the model. That is by creating a transformer network from imagenet and style labels. Next it computes total loss as defined below to create a training operation from the total loss and learning rate. Finally, run the training operation to learn style-transferring weights. 

* Learning (module) 
It has the main function related to training the model:

* def total_loss: computes the total loss which is a content loss plus style loss. 
* def content_loss: computes the content loss which is the Euclidean distance between tensor value for the original input and stylized input. 
* def style_loss: it takes gram matrix for each style image, tensor value for the stylized input and style loss weight to computes the total style loss. 
* def _gram_matrix: computes the Gram matrix for a set of feature maps.

* Model (module)
It has the style transfer network that map an input image into stylized image. 
* def transform: take a batch of images or an image and build a transformer network. 
* _conv2d takes Input + 'conv1' to create a tensor output of 32 channels + 'conv2' to create a tensor output of 64 channels + 'conv3' to create a tensor output of 128 channels
* upsampling to expand the tensor by computing nearest-neighbor upsampling of the input by a factor of `stride`. It expands the tensor to a 3-channel tensor for the final tensor output.  

* Image stylization transform (module)
For reading and input image and stylization mode (i.e. one image of mixed styles, multiple images of different styles). It sends the input image to Model module to create the transformer network. Then it maps the input image into stylized image according to the transformer network. Finally, it saves the output image to output directory. 

## Extra functionality 
* User Interface
We created a user interface using jupyter notebook. The user is able to browse for input images and stylize them using the trained styles. Each time a new style is trained, a checkpoint file is created and saved to the project directory. The user select an input image to be stylized and select one of the previously trained styles as checkpoint file. In addition, the user is able to visualize each layers activations outputs. That is, to see how the image activates the neurons of the network.

* Layers activations visualization
After running the code we added an extra function to visualize all layer activations outputs. That helps to understand what the network is doing given specific input. We used functions adopted from medium.com in which the first function applies the activations to a given input image at a given layer. The second function plots the results of those activations. In a given layer, each filter has learned to activate optimally for different features of the image. We’re showing here the activations of the first six filters of ‘conv1’ layer that has 32 filters:


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

