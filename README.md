# k means ++ for Rhino3D

**TOOL:**

A kmeans++ solver for Rhino3D. All math coded from scratch. I wanted to learn the workings of the algorithm, and here they are!

**PURPOSE:**

General purpose clustering of 3d points and geomtetrical data.

**PSEUDOCODE kMeans++:**

- Initialize by random choice
- Run a sequential centroid collection by computing weights
- We select the successive centroids by the farthest SSD
- Iterate till the k
- Compute the SSD error
- Iterate the above loop and optimize by the SSD error metric   

---

**A demo on a simple point cloud** <br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo1_250526.gif" width="500"> 
<br>
**A demo on a point clouds of 500 points!** <br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo2_250526.gif" width="500">
<br>
