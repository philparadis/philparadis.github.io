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

1. Data augmentation *(
  - More specifically, we will augment the captions associated to each image by using a "image -> caption" on the outer frame
  - The outer frame can be split into four rectangles with coordinates (assuming (0, 0) is the bottom-left corner:
    - [(0, 0), (0, 64), (16, 64), (16, 0)]
    - [(0, 64), (64, 64), (64, 48), (0, 48)]
    - [(48, 84), (64, 64), (64, 0), (48, 0)]
    - [(0, 0), (0, 16), (64, 16), (64, 0)]
