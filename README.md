## Introduction

This is a general tutorial for 3D point cloud registration using SVD based closed form approaches with known correspondences. 

We also investigate what the minimum number of corresponding points needed is to register two point sets. This problem seems deceptively simple but I couldn't find a clear answer in standard computer vision/robotics texts. Therefore, this post offers a concise answer from multiple perspectives: theoretical, algorithmic and from geometric intuition by going through the original papers from the 1960s.

The main blog post providing theoretical/geometric justification can be found here: [A tutorial on finding minimum point correspondences between two point sets](https://saishubodh.notion.site/Minimum-point-correspondences-b-w-two-point-clouds-to-solve-for-transformation-between-them-f0d972001496410493a1613b9aada2d3?pvs=4).  

This repo supplements the blog post by providing the code in the form of ipython notebook.

Read this README file (you're reading currently) completely to know which place is best for you to get started (ipython notebook/Notion page).

## Problem 
You have a set of 3D points observed from 2 different coordinate frames separated by a transformation (rotation + translation). In other words, you have 2 sets of the same 3D points and you want to estimate what the transformation between them two is. 

The ipython notebook "point-set-registration-experiments.ipynb" has the most commonly used SVD based approaches, i.e. Orthogonal Procrustes and Wahba algorithm (actually a special case of Wahba's algorithm with weights as 1) and solves for rotation and translation between them.

### Further Objectives
In addition, the specific objective is to figure out what is the minimum number of corresponding points needed to register two point sets.

The notebook experiments with the two methods mentioned above to find the minimum number of corresponding points for registering 2 (3D) point clouds in a closed form. These 2 point clouds are separated by translation and rotation.

##  Solution for min. number of points
### Geometrically,
One can geometrically figure out that the minimum number of corresponding points for finding transformation between 2 point sets in 3D space is 3. 
One way you could go about it is: First assume the answer is 2; now you will realise the point cloud is free to rotate about the line joining the 2 points, hence you need 1 more point to constrain the rotation as well. One can reason about this in other ways as well.

The Notion page (link at top of this README file) goes into slightly more detail into the geometric method.

### Algorithmically,
However, the objective of our experiment was to figure out the same answer using standard closed form solutions and prove that that is actually the case algorithmically. 

The experimentation in the notebook concludes the following:   
- Orthogonal Procrustes' algorithm needs a minimum of 4 points.   
- Wahba's algorithm needs a minimum of 3 points. 

### Theoretically,
A detailed page has been created which explains theoretical justification in detail. [Link here](https://www.notion.so/saishubodh/Minimum-point-correspondences-b-w-two-point-clouds-to-solve-for-transformation-between-them-f0d972001496410493a1613b9aada2d3)

## Future Improvements
* Add code for solving scale as well. 
* Address the question if you need only 3 for solving scale as well, both algorithmically and theoretically.
* Kabsch algorithm and clear difference between the 3 algorithms?

# Citation
If you found this work helpful, you could cite it as:
```
@article{puligilla2024minpoint,
  title        = {A tutorial on finding minimum point correspondences between two point sets},
  author       = {Puliglla, Sai Shubodh},
  journal      = {shubodhs.ai},
  url          = {https://shubodhs.ai/blog/tutorial-correspondences/},
  year         = {2024}
}
```
