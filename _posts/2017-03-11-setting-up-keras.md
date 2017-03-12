---
layout: post
title: Using Keras to implement convolutional nets
published: true
permalink: /:year/:month/:day/:title/
author: Philippe Paradis
categories: IFT6266-project
---

## Step 1: Install Anaconda
~~~~
> cd ~/Downloads
> bash ./Anaconda2-4.3.1-Linux-x86_64.sh
> cd
~~~~
Now, it's time to create a fresh conda virtual environment in which we will install keras and a backend (tensorflow or theano).

Note that `-n keras` simply defines the name of the virtual environment as `keras`, `python=2.7` specifies the python version to use and `anaconda` is used here to install all the default packages that come with a fresh install of anaconda.
~~~~
> conda create -n keras python=2.7 anaconda
~~~~

## Step 2: Install Keras and TensorFlow
It will be possible to use the command `conda install keras` to install Keras and all dependencies, including TensorFlow and Theano. However, we will not do this, because conda will install the CPU versions of the backends only. Instead, we will activate our conda environment and from within use pip to install everything. See below:
~~~~
> source activate keras
> export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0-cp27-none-linux_x86_64.whl
> pip install --upgrade $TF_BINARY_URL
> pip install keras
~~~~

We did not install Theano yet, but it is easy to do and we shall do so if and when necessary.
