# Style Transfer


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
 * python 3.5
 * tensorflow (v0.12)
 * django (1.10)
 * channels
 * Redis
 * asgi_redis (at least 1.0)
 * [CKPT FILE](https://uofi.box.com/shared/static/vm0sm79oh037eh2kood6tvnaq010f75h.zip)
 * [Dataset](https://uofi.box.com/shared/static/vz93xppov71cu5ubf14cb65i3pvwgmmw.txt)

## Running

Once you have all the depenedencies ready, do the folowing:

Download the dataset friends.txt and move it to data/lightweight/. 

Extract the ckpt zip file, you will get a folder 'model-server' with the ckpt file and its associated files. Move this folder to /save. The server will look at the model present on save/model-server/model.ckpt

To configure the web app

```bash
export CHATBOT_SECRET_KEY="my-secret-key"
cd chatbot_website/
python manage.py makemigrations
python manage.py migrate
```

Then, to launch the server locally, use the following commands:

```bash
cd chatbot_website/
redis-server &  # Launch Redis in background
python manage.py runserver 0.0.0.0:8888
```
Go to the browser, if you are running it on a server then [ip-address]:8888, if you are on your local machine then localhost:8888


# Stylizing an Image
First, download one of our pre-trained models:

* [Monet](http://download.magenta.tensorflow.org/models/multistyle-pastiche-generator-monet.ckpt)
* [Varied](http://download.magenta.tensorflow.org/models/multistyle-pastiche-generator-varied.ckpt)


