# Research Diary: Week 30 January 2023 - 3 Febuary 2023 #

## Entry: 3 February 2023 ##

So this week was a bad week in terms of progress. The key research idea that I wanted to look at was block matching via the GPU. The main problem was that I had incorrectly thought that the GPU processor in my laptop would still be supported by the latest offerings - an assumption that turned out to the false. 

### Retrospective ###

A major concern raised at the retrospective was that it seemed that I my task list was _diverging_ into an endless stream of unrelated activies. It was noted that the SymReg project was **created to avoid this**. The goal of SymReg was to solve real-world optimization problems and the goal of Inference3D was to determine how to formulate real-world 3D problems in such a what that they can be applied to SymReg.

For this reason, I have decided to update my focus a little. The initial problem that I was looking at was the multi-view stereo problem, which is an expansion of the binocular stereo problem (essentially the same problem, but with more views). What I noted in my thinking was that there are essentially two aspects to solving this type of problem:
* The solving of a single instance of the problem.
* A general solution that makes discovery of solutions quicker or have better quality.

I note that the single instance problem basically mirrored what I am doing in SymReg, namely trying to fit some sort of digital model to a set of sample measurements taken from the problem space, with the hope that the model is able to infer novel views with reasonable accuracy. Therefore I have decided to focus on the single instance solving problem first. Once this has been solved, I can think look at learning heuristics to make this search quicker in the general case.

#### SymReg Generalization ####

One of the ideas that I am hypothesising in SymReg is that I am able to generalize problem solving approaches to fit various families of problems. So one of the things that I am looking at is how much this problem space has with a typical problem space used for Symbolic Regression. The basic template for problem solving that I am using is the PatchMatch algorithm. The main difference is that Stereo Matching is a problem that can be divided into a local aspect (finding a depth value that leads to the best color matching across images) and a global aspect (the notion that there is normally a bunch of equally valid solutions locally that can be resolved to the "smoothest" solution globally). 

Local refinement can essentially be done individually for each pixel, while global refinement needs to take into account the "bigger" picture. My first hypothesis is that I can create a bunch of equally valid "local" solutions using a "single pixel" approach. And then use a "standard" global genetic algorithm to refine the solution. 

Thus this is the proposal that I will be looking at in the next week. It is much more aligned with the brief - I am formulating the stereo matching problem into a form that can potentially be solved by the SymReg Genetic Programming module VanillaGP - however I am thinking about adding some additional transforms to the approach that might be novel (and might have utility across other problem spaces as well).

