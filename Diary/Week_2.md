# Research Diary: Week 15 January 2023 - 21 January 2023 #

## Entry: 20 January 2023 (Friday) ##

My hypothesis was a success! I used my mobile phone to capture a sequence of the graph vine focused on the crown and got a pretty good model! 

Now that I have demonstrated that the system can work, I can move on to the next steps of my research plan:
 
* Establish a test environment that will allow me to process image sets automatically using NeRF (I have already established that the system can run headless).
* Start work on my variant - PMVS - which will allow me to inject novelty to start publishing on this.

## Entry: 19 January 2023 (Thursday) ##

There was no real improvement overnight in building my NeRF model. The problem is that NeRF needs a central focal point in the scene, which I did not do with the current data. I will capture a new sequence of data to try and verify this.

## Entry: 16 January 2023 (Tuesday) ##

I am focused on evaluating the SOTA - which is the NeRF technology

* I need to fix the script for calculating poses.
* I want to load in the Maaratech data and see how this looks.
* I also want to try and make my sequences and see how those look.
* It might be interesting to make a blog post of my findings.

I am also thinking about what I can compare the technology to:
* I believe that a Multi-View Patchmatch algorithm might be an interesting comparison system.
* I hypothesize that using multiple images means no block matching (which is slow). This idea essentially comes from DTAM.
* I hypothesize that the application will be too slow - therefore, I have invested in using CUDA to try and solve things.
* I also want to investigate the notion of "dense alignment" once I have a semi-plausible model.
* Alignment is currently dependent on bundle adjustment logic. This means COLMAP! But the plan is to use a DTAM approach and start moving away from COLMAP. The role that COLMAP will play in this is to verify the accuracy of the system.

Note that this will be a year long project. While I am busy planning for an automated infrastructure for searching for functional solutions - I need to develop a similar infrastructure for scanning, and appending to large 3D models - which is the goal of this particular project.