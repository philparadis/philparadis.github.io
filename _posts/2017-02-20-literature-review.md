---
layout: post
title: Historical Background and Literature Review
published: true
permalink: /:year/:month/:day/:title/
author: Philippe Paradis
categories: IFT6266-project
---

# Historical Perspective and Relevant Work

Here is a relevant quote that sums up the state of affair as of 17 May 2016, from Reed et al's paper ''Generative Adversarial Text to Image Synthesis'':

> Generative adversarial networks (Goodfellow et al., 2014)
> have also benefited from convolutional decoder networks,
> for the generator network module. Denton et al. (2015)
> used a Laplacian pyramid of adversarial generator and discriminators
> to synthesize images at multiple resolutions.
> This work generated compelling high-resolution images
> and could also condition on class labels for controllable
> generation. Radford et al. (2016) used a standard convolutional
> decoder, but developed a highly effective and stable
> architecture incorporating batch normalization to achieve
> striking image synthesis results.
> 
> The main distinction of our work from the conditional
> GANs described above is that our model conditions on text
> descriptions instead of class labels. To our knowledge it
> is the first end-to-end differentiable architecture from the
> character level to pixel level. Furthermore, we introduce a
> manifold interpolation regularizer for the GAN generator
> that significantly improves the quality of generated samples,
> including on held out zero shot categories on CUB.
> 
> The bulk of previous work on multimodal learning from
> images and text uses retrieval as the target task, i.e. fetch
> relevant images given a text query or vice versa. However,
> in the past year, there has been a breakthrough in
> using recurrent neural network decoders to generate text
> descriptions conditioned on images (Vinyals et al., 2015;
> Mao et al., 2015; Karpathy & Li, 2015; Donahue et al.,
> 2015). These typically condition a Long Short-Term Memory
> (Hochreiter & Schmidhuber, 1997) on the top-layer
> features of a deep convolutional network to generate captions
> using the MS COCO (Lin et al., 2014) and other captioned
> image datasets. Xu et al. (2015) incorporated a recurrent
> visual attention mechanism for improved results.

# Background

1. Many authors have had good success over recent years at the task of generating descriptive text captions from images, often going as far as describing complex scenes with multiple objects, their characteristics and the relationships among the objects and their environment.

2. The reverse task of generating images based on a caption has proven more difficult, but fairly significant advances have been made in recent years (2014--2017).

3. Having generative models for both directions "image --> caption" and "caption --> image" is particularly useful, since combining them to produce "input caption --> generated image --> generated image caption" allows us to compare how semantically close the two captions "input caption" and "generated image caption" are to each other as a way to roughly gauge how close the generated image is to the target image. This can be used in an iterative process to train our model.

4.

Quick Summary of Relevant Literature
====================================

The following papers are not listed with respect to relevance, but in chronilogical order, to allow for a better perspective on the development of those techniques. However, the relevance (with respect to the IFT6266 project) is indicated in each entry.

TODO: Add date for each entry and re-order.

1. Generative Adversarial Text to Image Synthesis
Significance: First model to generate images ''from text captions'' only for any class.
Relevance: Very high
Summary: Use a stacked GAN model.
github:	 https://github.com/reedscot/icml2016
arXiv: 	 https://arxiv.org/abs/1605.05396

2. Learning Deep Representations of Fine-grained Visual Descriptions
Significance: 
Relevance: 
Summary: 
github: 
arXiv: 

3. StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks
Significance: 
Relevance: Very high
Summary: 
github: https://github.com/hanzhanggit/StackGAN
arXiv: https://arxiv.org/abs/1612.03242

4. Conditional generative adversarial nets
Significance: 
Relevance: High
Summary: 
github (not official): https://github.com/zhangqianhui/Conditional-Gans
arXiv: https://arxiv.org/abs/1411.1784

5. Generating images from captions with attention
  * Date:
  * Authors:
  * Significance: 
  * Relevance: 
  * Summary: 
  * github (official): https://github.com/emansim/text2image
  * arXiv: https://arxiv.org/abs/1511.02793

6. Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks
  * Date:
  * Authors:
  * Significance: Very high
  * Relevance: 
  * Summary: 
  * github (official): https://github.com/Newmu/dcgan_code
  * arXiv: https://arxiv.org/abs/1511.06434

Resources
=========
Literature papers on Adversial Networks:
https://github.com/zhangqianhui/AdversarialNetsPapers

In-depth Literature Review
==========================

