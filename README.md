# Stanford CS248 Assignment 2: MeshEdit

The repository is located at https://github.com/stanford-cs248/Cardinal3D. We have created a wiki (https://stanford-cs248.github.io/Cardinal3D/) that will be the primary source of information about this assignment. On that page you will find all the details about what you need to implement, etc. This document only contains administrative details about building the starter code, grading, and submission.

## Due Date

The assignment is due Feb. 11 at 11:59:59 PM.

## Code Environment

This codebase should compile on Linux, Mac OS X, and Windows on a typical environment. Check out the [git setup page](https://stanford-cs248.github.io/Cardinal3D/git/) and [the project page](https://stanford-cs248.github.io/Cardinal3D/build/) to set up the github repo, install dependencies and building the code. If you have difficulties running the code on your local machine, the rice cluster machines (rice.stanford.edu) have all the packages required to build the project.

When you have successfully built your code, you should get an executable named `Cardinal3D`. Upon starting the program, it should be in model mode. The [User Guide](https://stanford-cs248.github.io/Cardinal3D/guide/) details how to use the interface. For convenience, some keyboard shortcuts are reproduced below.

| Key                   | Command                                            |
| :-------------------: | :--------------------------------------------:     |
| `space`               | switch to navigate mode                            |
| `tab`                 | show/hide info panel                               |
| hold `control`        | temporarily switch to translation in edit mode     |
| hold `shift`          | temporarily switch to scaling in edit mode         |
| hold `alt/option`     | temporarily switch to rotation in edit mode        |
| `e`                   | cycle through **e**dit modes                       |
| `b`                   | toggle **b**evel mode                              |
| `n`                   | select **n**ext halfedge                           |
| `t`                   | select **t**win halfedge                           |
| `h`                   | select **h**alfedge of current element             |
| `T`                   | **T**riangulate mesh                               |
| `s`                   | **s**ubdivide Catmull-Clark                        |
| `S`                   | **S**ubdivide linear                               |
| `bksp/del`            | erase selected edge                                |
| `f`                   | **f**lip selected edge                             |
| `c`                   | **c**ollapse selected edge                         |
| `p`                   | s**p**lit selected edge triangle meshes only!      |
| `u`                   | **u**psample triangle meshes only!                 |
| `i`                   | **i**sotropic remesh triangle meshes only!         |
| `d`                   | **d**ownsample triangle meshes only!               |
| `w` then `0--9`       | **w**rite scene to numbered buffer                 |
| `l` then `0--9`       | **l**oad scene from numbered buffer                |

## Evaluation
For this assignment, you will implement methods in `meshEdit.cpp`.

The User Guide on the wiki describes a large number of features that are in principle available in MeshEdit mode. You do not have to implement all of these features to receive full credit on the assignment! However, you do have to successfully implement a subset of the features. Implementing additional features beyond the required subset will earn you extra credit points.

The particular requirements, and the percentage of the grade they correspond to, are:

* Four of the local operations (listed below), including EdgeCollapse, EdgeFlip, EdgeSplit and FaceBevel 
* Triangulation, LinearSubdivision, and CatmullClarkSubdivision 
* One of: LoopSubdivision, IsotropicRemeshing, or Simplification 
* Create one beautiful 3D model using Scotty3D (20 pts)
* Submit a suggested improvement to the A2 documentation on Piazza

In other words, everyone has to implement EdgeCollapse, EdgeFlip, EdgeSplit, FaceBevel, triangulation, linear subdivision, and Catmull-Clark. These features are the bare minimum needed to model interesting subdivision surfaces; triangulation is necessary in order to do the global remeshing task(s). Note that some of the global tasks require that you implement specific local operations! For instance, the implementation of Simplification depends on EdgeCollapse. The local operations are as follows (these operations are described in the User Guide):

* VertexBevel
* EdgeBevel
* FaceBevel - everyone must implement
* EraseVertex
* EraseEdge
* EdgeCollapse - everyone must implement
* FaceCollapse
* EdgeFlip - everyone must implement
* EdgeSplit - everyone must implement

The global operations, and their dependency on local operations, are as follows:

* Triangulation - everyone must implement
* LinearSubdivision - everyone must implement
* CatmullClarkSubdivision - everyone must implement
* LoopSubdivision - depends on EdgeSplit and EdgeFlip
* IsotropicRemeshing - depends on EdgeSplit, EdgeFlip, and EdgeCollapse
* Simplification - depends on EdgeCollapse

You are free to change the subset of features you choose to implement at any point during the assignment, but you should clearly indicate which features you chose (including those implemented for extra credit) by putting this information in your writeup (described below). You might find it worthwhile using the checkConsistency member function of the HalfedgeMesh class to help debug your operations.

Extra credit: each additional local operation beyond the requirements will be worth 2% of the assignment grade; each additional global operation will be worth 4% of the assignment grade. The maximum possible grade on the assignment is 110%.

## America's Next Top 3D Model
Every student is required to submit a 3D model created from cube.dae using their implementation of Scotty3D, which will be automatically entered into a class-wide 3D modeling competition. Models will be critiqued and evaluated based on both technical sophistication and aesthetic beauty. Note: Use of any other 3D package (e.g., free or commercial 3D modelers like Maya or Blender) is strictly prohibited! This model must be created by opening cube.dae, applying the operations implemented as part of the assignment, and saving the result.

NOTE: We are expecting some high-quality output here---or at least some creativity! Don't just brush this one off. :-)

Include this model in the root directory of your submission as model.dae.

## Documentation
Clear, well-written documentation is a critical part of software development. Since you (the students) are the ones who will most benefit from good documentation---or will suffer through bad documentation---we are "crowd sourcing" improvements to the course material. What did you find confusing---and then finally figure out?

As 5% of your assignment grade, you will need to submit suggested edits to the assignment documentation. These could be:

* Suggested changes or additions to the assignment writeup
* Suggested changes or additions to assignment Wiki (for A2, A3, and A4)
* Suggested changes or additions to comments in the skeleton code

Do not wait until the due date to submit these suggested edits. They will be most helpful to your classmates (and to us!) if they are submitted ahead of time, so that we can immediately incorporate any good suggestions into the actual course material. To submit your edits, you must therefore:

* Go on Piazza
* Find the thread with the appropriate label: a1wiki, a2wiki, a3wiki or a4wiki
* Make an anonymous (not private) post with your suggested edit

The TAs will monitor this label, and immediately update the docs with any/all useful suggestions. This Piazza post will also be recorded as part of your assignment grade. Note that we do not have to accept your edit in order for you to receive full credit on the assignment. However, we will grade your edits based on whether they appear to be a "good faith effort" to make a useful comment. In other words, did you really think about what is clear/unclear and provide a useful edit? Or did you just write something totally random at the very last minute? :-) Especially useful edits (e.g., those that provide nice insights, or point out serious bugs/errors) may receive extra credit.

## Writeup
Additionally, you will submit a short document explaining what you have implemented, and any particular details of your submission. If your submission includes any implementations which are not entirely functional, please detail what works and what doesn't, along with where you got stuck. This document does not need to be long; correctly implemented features may simply be listed, and incomplete features should be described in a few sentences at most.

The writeup must be a pdf, markdown, or plaintext file. Include it in the root directory of your submission as writeup.pdf, writeup.md, or writeup.txt.

Failure to submit this writeup will incur a 10 pt penalty on the assignment.

## Submission Instructions
We are using [Canvas](https://canvas.stanford.edu) as our submission tool. You should create and upload a zipped folder of your entire `/src` subdirectory along with the writeup (e.g. writeup.txt) and 3D modeling submission (`model.dae`). Do not include your build subdirectory. You may work in teams of up to two people. If working in a team, please have only one person make the submission. CS248 staff will run a simple script that checks for the extra files. If the output indicates that something is missing, fix it or risk losing points!

## Acknowledgement

CS248 course staff would like to thank Professor Keenan Crane and his course assistants for the initial development of assignment materials.