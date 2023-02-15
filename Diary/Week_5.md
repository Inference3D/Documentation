# Research Diary: Week 6 February 2023 - 10 February 2023 #

## Entry: 10 February 2023 ##

So the main problem this week was about problem formulation. I want to use SymReg to solve problems related to 3D reconstruction, but I am unsure how to structure the problem solving approach. 

I do not think that it is possible to "learn" a solution in one go, I think that a more feasible solution is to start building a pipeline with some manually developed components and start filling in the "blanks" with SymReg solutions. 

Ultimately, the pipeline that I am developing should address the multi-view 3D reconstruction problems that I currently would like to solve:
* 3D reconstruction the line of trees captured at the apple farm.
* A 3D reconstruction system for the turntable.

While I think a "direct" feature free pipeline is probably the best solution and the one most likely to support real-time 3D reconstruction in the future. However, currently I am interested in getting a solution out fast - therefore I am looking to build a pipeline that is far more established, which is the feature point bundle adjustment algorithm. There are a couple of things that can be "learnt" in this space including:

* Feature detection (finding good feature points within the system)
* Feature matching (finding corresponding feature points across images)
* Machine learning based stereo matching
* Random search bundle adjustment
* Multiple image dense depth alignment.

A typical feature based 3D reconstruction pipeline (ModelMaker) should have the following form:
* Image extraction + Image filtering + feature extraction + feature matching (ModelImage)
* Pose estimation between frames + bundle adjustment (ModelPose)
* Stereo Matching between frames (assuming reasonable pose) (ModelDepth)
* Final model construction (ModelMerge)

**NOTE:** Next week I will focus on making some headway with **SymReg** because I need the ability to create and run machine generated functions (rather than just hypothesize about such a notion).
