---
layout: post
title: Bottom-up Iterative Approach
published: true
permalink: /:year/:month/:day/:title/
author: Phil
categories: IFT6266-project
---

# Bottom-up Iterative Approach

After discussions with Alex Lamb, I decided to ignore GANs for the moment and start with the simplest possible approach.

Then, I will proceed in an incremental manner after each step is working and add a little bit of sophistication to my working model from the previous step, using material from the course.

## Rough outline of the new strategy.

1. Build a simple MLP model with:
  - Input dataset $(X_{\text{outer}}, X_{\text{inner}})$
  - Model: Simple fully-connected MLP with 1 to 3 hidden layers which takes $X_{\text{outer}}$ as my input and tries to output $\hat{X}_{\text{inner}}$.
  - Loss function is simply: $|| \hat{X}_{\text{inner}} - X_{\text{inner}} ||_2^2$
2. Replace the first layer or two with convolutional layers and some pooling layers before flattening the images. The rest stays the same. See if that helps.
3. Replace all the remaining fully-connected layers with convolutional layers, except this time, in order to make the output dimension large enough, we will use strided convolutions to increase the dimensionality at each step.
4. Use the model from step 3, but change the loss function to something more appropriate. We want to get away from the pixel space and instead get the loss function by comparing generated output and target output at some hidden layer of the convolutional net.

