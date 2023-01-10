# Research Diary: 09 - 13 January 2023 #

## Entry: 11 January 2023 (Wednesday) ##

The goal of the _Inference3D_ project is to put a system in place that can start processing large stacks of images and to try and determine 3D geometry - to a high degree of accuracy (essentially mining for structure).

```
The idea is that once the structure is in place - I can start refining the processes, which will then be the actual research part.
```

### So what are the parts of the system that I need? ###

* A **database** of image sequences (the data that I am going to be mining from).
* The **mining tool** takes input data, formulates a hypothesis, and improves those formulations.
* A **scheduler** that allows me to queue up problems, and have regular runs (basically creates a regular experiment that is expected to be a "hook" that will allow me to easily take stuff onto).
* **Data preparation tools** are needed, at least initially, so that I can remove some of the challenges associated with data processing including:
    * Calibration (it is expected that calibration parameters will be known beforehand).
    * Distortion has been removed.
    * Reasonable pose estimates are made for each frame within the system.

### So what am I working on right now? ###

```
Research Question: Can I use a standard "Single Node" Genetic Type algorithm to estimate depth (disparity)?
```

_NOTE: As a simplifying assumption I_ will initially focus on the binocular stereo problem (images are available, processing bottlenecks are less, and I can link and evolve the patch match algorithm)._

To test this, the first step is to assemble a basic algorithm that is capable of performing the necessary search. The following notes are related:

* Assemble a database of binocular stereo pairs (start with rectified images - later use non-canonical search).
* The refinement process is expected to be as follows:
    * Select candidate random regions within the image.
    * Use tournament selection to determine what the stronger members in the region are.
    * Try to apply these to weaker members.
    * Perform a "binary" refinement to improve changed values.
* Report back in the blog how this experiment went.
* Once a mediocre system is going with promise, then the next step is to use machine learning to focus on improving things like:
    * Better cost function development (or image pixel encoding - marking pixels with features that exist in their local neighborhood).
    * The selection of "propagations" seem kind of arbitrary - is there a search for different propagations that I could use?
    * How can I structure the search so that I get better results?

