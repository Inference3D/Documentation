# Research Diary: Week 23 January 2023 - 27 January 2023 #

## Entry: 24 January 2023 - Tuesday ##

I have now managed to execute the PMVS system against data. Here are my findings: 
* A single-pixel approach is speedy and allows me to quickly process many images and retrieve some "fine" thin image elements.
* Multiple images make this smoother - but I still have noisy depth maps in homogenous regions.
* I still have occlusion noise, and distant scene elements are not outstanding.
* I designed the system to learn depth along with a color model. I found that this did not work very well - because the system tended to find some compromise between color and depth that was unrealistic. Adding color gives the system too many "degrees of freedom."
* Without color, I matched a single frame within the system. This is not really what I intended initially.

I am currently in the process of designing PMVS2 - Which I am calling DMap (COLMAP for depth maps)

## Entry: 23 January 2023 - Monday ##

On Friday, I threw together a quick concept implementation of PMVS. In hindsight, I should have built up the system in pieces and tested each component with unit tests - rather than having a complex system as a whole to evaluate. 

Note that I need to do things in this way in the future. I need to practice a more careful, slow approach to science.  I also need to avoid "peer pressure" because my goal is to do something different from my peers, so following them makes no sense.

My logic for building a PMVS implementation before the infrastructure was to prove that I had a competing idea for the NeRF idea. 

Ultimately my thinking is as follows:
* I have been looking at Symbolic regression as a tool to make data "explainable."
* I see the 3D model representation as a symbolic representation of 3D data.
* A common approach to fitting Symbolic Representations to data is Genetic Programming. 
* 3D models tend to be quite large - so holding an entire population of these in memory seems untenable - however, there is a "single node" variant of genetic programming that is much more space efficient.
* The transforms of "single node" genetic programming differ from regular Genetic Programming. I hypothesize that a variant of Patchmatch transforms a better fit to the solution space than something more generic.
* Ultimately I am skeptical that Genetic Programming is the best approach for symbolic regression. I am interested in other algorithms for optimization (of the first of a model to data) and currently reading about convex optimization as a tool. 

However, the first step is to try and see how well my PMVS idea performs.

