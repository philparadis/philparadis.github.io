---
layout: post
title: Early-phases ideas and experiments
published: true
permalink: /:year/:month/:day/:title/
author: Philippe Paradis
categories: IFT6266-project
---

# Initial Ideas: Part I

## The two basic tools:

To solve this task, it is likely that we will have to make heavy use of two basic tool and  techniques,
which are fairly recent but for wich many variations and different implementations already exist:

### Tool A: "image -> caption" generative model

### Tool B: "caption -> image" generative model

# First idea (to resolve part of the conditioning problem)

We plan to decompose the problem into many subproblems, that is, use a divide-and-conquer approach.
Each technique will be simple and resolve only a part of the task or a subpart of a part.
The idea we are about to introduce resolves a subpart of a part, the part being: how to condition the
generated target image to blend smoothly with the outside frame. The subpart is an idea to make the blending easier to accompli11sh.

## Description of first idea to help 

1. Data augmentation (for captions)
  - Use an "image -> caption" generator on the outer frame to produce a short caption that can be concatenated with existing captions
  - If done properly, this would create captions that contain the "full picture" (as typical human-generated captions tend to focus on
    the main subject -- often central in the image -- and ignore the surrounding background. Such new captions would fill in this gap.
  - To minimize work, the outer frame can be split into four rectangles with coordinates (assuming (0, 0) is the bottom-left corner:
    - [(0, 0), (0, 64), (16, 64), (16, 0)]
    - [(0, 64), (64, 64), (64, 48), (0, 48)]
    - [(48, 84), (64, 64), (64, 0), (48, 0)]
    - [(0, 0), (0, 16), (64, 16), (64, 0)]
  - In case where we cannot easily get an "image -> caption" generator that takes non-square image inputs, then we would have to split
    the outer frame into twelve 16x16 pixels images
2. Style transfer for generating an early-stage "outer frame" and target image edge area
  - See (Leon A. Gatys, Alexander S. Ecker, Matthias Bethge, "A Neural Algorithm of Artistic Style", 2015, https://arxiv.org/abs/1508.06576v2) for the original paper explaining this technique (with github code: https://github.com/jcjohnson/neural-style)
  - See https://github.com/jcjohnson/fast-neural-style for a much faster (100x speedup) implementation (based on the paper http://cs.stanford.edu/people/jcjohns/papers/eccv16/JohnsonECCV16.pdf)
  - Now the idea would similar to idea 1 above, using rectangles or square decompositions of the outer frames. Those images
  would be use as the "style" images in order to generate a 32x32 pixels target image. Of course, a content image of some sort would have exist first: Many candidates exist:
    * Simple white noise: in this case, all we get are the textures and colors from the outer frame, which we can then try to use as a background when generating an actual target image
    * We could use a "caption->image" generative model to generate a target image based on input captions. Then, use this as the "content" image. This has the obvious problem that the target image produced would only have textures and colors that come from the outer frame, which is unlikely to frequently correspond to the desired colours. There are multiple solutions to this:
      * There exists a variation on the "style transfer" technique which preserve the colours of the content image, rather than the colours of the style image (see https://arxiv.org/abs/1606.05897)
      * We could try to restore the colors in a subsequent phase of the algorithm
  year={2016}
}
