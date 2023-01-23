# Research Diary: Week 09 January 2023 - 13 January 2023 #

## Entry: 13 January 2023 (Friday) ##

1. I am still working on the data preparation for testing out the multiview aspect of this system.
1. I have also started working on blog posts for PatchMatch Stereo and VanillaGP.
1. I also need to focus on the Strutfit problem:
    * Local neighborhood identification: What will this look like?
    * I think that the Strutfit problem will need its diary. 
1. I also need to start working on infrastructure (It would be nice to have a basic automated system by the end of the month).

## Entry: 12 January 2023 (Thursday) ##

So I got the PatchMatch binocular stereo algorithm working. What I learned
* A block match cost produces a much better score than an attempt with a single pixel.
* Even so, the result is still far from perfect.
* I know (from previous work) that left-right cross-referencing image data helps identify occlusions in the depth map.
* I also verified that replacing the standard "propagations" with my own _Random Selection_ and _Neighbour Selections_ reasonably drives the disparity values toward convergence.

### Next Steps ###
1. I am now concerned about the cost function - block matching is slow, so not that easy to incorporate into an unbiased multi-view matching system.
1. One idea is to have a system where I select a "keyframe" used as the main one for comparison (such as the approach used in the DTAM paper).
1. *Research Question:* If I use a multi-view approach, does this mean I can dispense with the block matching and use a single pixel (which seems to be the case in the DTAM algorithm)?

## Entry: 11 January 2023 (Wednesday) ##

The goal of the _Inference3D_ project is to put a system in place that can start processing large stacks of images and to try and determine 3D geometry - to a high degree of accuracy (essentially mining for structure).

```
The idea is that once the structure is in place - I can start refining the processes, which will then be the actual research part.
```

### So what are the parts of the system that I need? ###

* A **database** of image sequences (the data that I am going to be mining from).
* The **mining tool** takes input data, formulates a hypothesis, and improves those formulations.
* A **scheduler** that allows me to queue up problems and have regular runs (basically creates a routine experiment that is expected to be a "hook" that will let me quickly try out stuff).
* **Data preparation tools** are needed, at least initially, so that I can remove some of the challenges associated with data processing, including:
    * Calibration (it is expected that calibration parameters will be known beforehand).
    * Distortion has been removed.
    * Reasonable pose estimates are made for each frame within the system.

### So what am I working on right now? ###

```
Research Question: Can I use a standard "Single Node" Genetic Type algorithm to estimate depth (disparity)?
```

_NOTE: As _a simplifying assumption_, I_ will initially focus on the binocular stereo problem (images are available, processing bottlenecks are less, and I can link and evolve the patch match algorithm)._

To test this, the first step is to assemble a basic algorithm capable of performing the necessary search. The following notes are related:

* Assemble a database of binocular stereo pairs (start with rectified images - later use non-canonical search).
* The refinement process is expected to be as follows:
    * Select candidate random regions within the image.
    * Use tournament selection to determine what the more robust members in the region are.
    * Try to apply these to weaker members.
    * Perform a "binary" refinement to improve changed values.
* Report back in the blog how this experiment went.
* Once a mediocre system is going with promise, then the next step is to use machine learning to focus on improving things like:
    * Better cost function development (or image pixel encoding - marking pixels with features that exist in their local neighborhood).
    * The selection of "propagations" seem arbitrary - is there a search for different propagations that I could use?
    * How can I structure the search so that I get better results?