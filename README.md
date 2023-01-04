# Inference 3D #

Inspired by the ability of machine learning algorithms to find promising solutions in large datasets with high dimensionality, the goal of this research work is to attempt to use these techniques to find solutions through the large complex solution spaces associated with 3D multi-image 3D reconstruction problems.

## Research Strategy ##

The main research strategy that I want to pursue in this work is an iterative one - starting with a small problem and then progressively attempting to solve increasingly more difficult problems. I am interested in both approaches that are available through the learning of Neural Networks (often formulated as so-called NeRF solutions), and those of stochastic sampling (which is typically the way search spaces are traversed in approaches like Genetic algorithms). 

At this early stage of the research, the goal is to start with a two-image system and use an approach akin to _Patchmap stereo_ to try and converge onto a result. 

## Initial Solution ##

The goal of the initial solution is to attempt to "find" a depth map given:
* The project model for each camera in the system.
* A static scene with significant overlap between two images.
* An estimate of the pose between the two images (which is expected to be "reasonable" but not necessarily perfect).

**The initial depth map is expected to be a map of random depth estimates between the frames. There will be a depth map for each image in the system.**

### Map Refinement ###

Like in the context of _Patchmap stereo_, improvement of the model is expected to take the form of various types of random searches. These searchers are expected to be:
* **Neighborhood Refinement:** Randomly selects the depth value associated with a close neighbor (that has a similar color) and checks to see if that neighbor has a better score.
* **Random Refinement:** Iteratively selects sequentially smaller updates to see if there is an improvement in the depth estimate.
* **View Refinement:** Check to see if the corresponding depth map has a better estimate for the depth than this one.

### Scoring ###

The initial proposal for scoring is to use the traditional pattern of a data score and a smoothing score. My first attempt is to focus on a single pixel rather than block matching (because I think that it will be quicker and will lead to more crisp results). It is expected that the score will be classical weighted sum $score = \alpha data + (1 - \alpha) smooth$ where $\alpha$ is the blending term that falls between zero and 1 inclusive. 

The data term is simply to be the color absolute color difference between corresponding pixels across the two images. The smoothing term is expected to be the standard deviation of local neighborhoods of pixels that have a similar color. 

### Pose Refinement ###

One of the first novelties that I want to attempt to add is the notion of pose refinement. The basic concept is that once the depth map are starting to look reasonable, an improvement in pose should lead to an improvement in the map score. Thus the idea is to wait for the system to generate a reasonable depth map, and the see if small random changes in pose lead to improvement in the result.
