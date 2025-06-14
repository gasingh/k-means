# kmeans++ for Rhino3D
kMeans++ is an unsupervised machine learning algorithm.

`machine learning` `unsupervised learning` `AI` `3d` `Rhino3D`

## **INTRODUCTION**
K-means (KM) algorithm groups N data points into k clusters by minimizing the sum of squared distances between every point and its nearest cluster mean (centroid). This objective function is called sum-of-squared errors (SSE). K-means was originally designed for minimizing SSE of numerical data. [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0031320319301608)

<p align="center" width="100%">
  CLUSTERING MESHES <br>
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175717.jpg" width="250"> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175724.jpg" width="250">  
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175857.jpg" width="250"><br> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_003334.jpg" width="250">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_003320_.jpg" width="250"> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_003353_.jpg" width="250"> <br>
  kMeans++ clustering a Stanford Bunny mesh in Rhino3D <br>

  <br>
  CLUSTERING POINT CLOUDS <br>
<img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_225341_black.jpg" width="300"> <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_225315_.jpg" width="300"> <br> <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_225327_.jpg" width="300"> <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_224405__.jpg" width="300">

<br>
kMeans++ clustering a randomized point cloud in Rhino3D<br>
A series of output images above: Top to Bottom, Left to Right. <br>
  TOP ROW: [1] k = 0 (initial), [2] k = 20 <br>
  BTM ROW: [3] k = 50         , [4] k = 50 as voxels
<br> 
</p>

### REFERENCES

#### PRIMARY
- [k means - Google Search](https://www.google.com/search?q=k+means&oq=k+means+&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQRRg7MgYIAhBFGDwyBggDEEUYPTIGCAQQRRg8MgYIBRBFGEEyBggGEEUYQdIBCDI4MTFqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8)
- [K-Means Clustering Explained](https://neptune.ai/blog/k-means-clustering)
- [Kmeans ++ From Scratch. An intuitive explanation of kmeans++… | by Lance Galletti | Medium](https://medium.com/@gallettilance/kmeans-from-scratch-24be6bee8021)

#### SECONDARY
- [1. How much can k-means be improved by using better initialization and repeats? - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0031320319301608)
- [2. k-means clustering - Wikipedia](https://en.wikipedia.org/wiki/K-means_clustering)
- [3. Stanford: kMeansPP.pdf](https://theory.stanford.edu/~sergei/papers/kMeansPP-soda.pdf)
- [4. k-means++ - Wikipedia](https://en.wikipedia.org/wiki/K-means%2B%2B)
- [5. KMeans — scikit-learn 1.6.1 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)

#### TERTIARY
- [kmeans++ heuristic - Google Search](https://www.google.com/search?q=kmeans%2B%2B+heuristic&sca_esv=fd75f58ac1ff980e&sxsrf=AE3TifMjmMSKIw1X2rmVBPleUle1XsR_1w%3A1748292902734&ei=JtU0aLTOLIWlhbIP-PC6mA4&ved=0ahUKEwi0-bjLgsKNAxWFUkEAHXi4DuMQ4dUDCBA&uact=5&oq=kmeans%2B%2B+heuristic&gs_lp=Egxnd3Mtd2l6LXNlcnAiEmttZWFucysrIGhldXJpc3RpYzIHECMYsAIYJzIIEAAYgAQYogQyCBAAGIAEGKIEMgUQABjvBUjLAlB4WHhwAXgBkAEAmAGNAaABjQGqAQMwLjG4AQPIAQD4AQGYAgKgApQBwgIKEAAYsAMY1gQYR5gDAOIDBRIBMSBAiAYBkAYIkgcDMS4xoAfVBLIHAzAuMbgHkgE&sclient=gws-wiz-serp)
- [Mastering data clustering: Your guide to K-means & K-means++](https://www.aiacceleratorinstitute.com/mastering-data-clustering-your-comprehensive-guide-to-k-means-and-k-means/#:~:text=Like%20K%2Dmeans%2C%20it%20is,can%20lead%20to%20suboptimal%20results.)
- [K-Means Clustering - an overview | ScienceDirect Topics](https://www.sciencedirect.com/topics/computer-science/k-means-clustering)

## **TOOL**

A kmeans++ solver for Rhino3D. All math coded from scratch. I wanted to learn the workings of the algorithm, and here they are!

## **PURPOSE**

General purpose clustering of 3d points and geomtetrical data.

## **PSEUDOCODE & CRITIQUE**

**PSEUDOCODE**
- Initialize by random choice
- Run a sequential centroid collection by computing weights
- We select the successive centroids by the farthest SSD
- Iterate till the k
- Compute the SSD error
- Iterate the above loop and optimize by the SSD error metric

**CRITIQUE**
- **K-MEANS**: I initially coded the traditional k-means. Where the initialization is by random choices (initial randomised cluster), and then clustering data by forming SD based associative collections. This is the vanilla version.
- **K-MEANS++**: This is the version with a heuristic applied for optimization. The k-means++ seems to be a more simpler and straightforward solution to code where we employ a simple weights heuristic to compute the centroid clusters.
- **INITIAL SEEDS**: Seeds can help in getting consistent results over successive runs of the same code. Great for degugging, etc. However I noticed issues with solutions. There is currently no seed initialized in the randomization, and so the results are more accurate. When specifying seeds (for example 42), sometimes the global minimum (SSD error) is never found, and it might need more runs. So for now, it's excluded.
- **K-MEANS++ & INITIAL SEED**: The technique relies heavily on initial seeding of the initial centroid, the rest of the k successive means are weighted selections from the initial seed. Successive initializations result in varied SSDs. Later we choose the solution with the least error.

## **DEMOS**

### RUN 01 

**COMPLEXITY**: Simple point cloud, k=5, iter = 100 | **RUNTIME**: 1 second

_This is a simple dataset with only 26 points. And the clustering is instantaneous._

<br>
<p align="center" width="100%">
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo1_250526.gif" width="500"> 
    </p>
<br>

### RUN 02 

**COMPLEXITY**: 500 points, k=20, iter = 5 | **RUNTIME**: 288 seconds = 4.8 mins

_This is a randomly sampled point cloud of 500 points and we create 20 clusters, 10 runs. The compute time is approx. 111 seconds. We additionally created point groups and respective bounding boxes to visually clarify the solution of the kmeans clustering. Although we also introduced the randomised coloring, it's easier to mine the results with respective bounding boxes._
<br>
<p align="center" width="100%">
<img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_225341_black.jpg" width="250"> <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_210043.jpg" width="250">  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_213704.jpg" width="250">
<br>
<br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo2_250526.gif" width="500">
    </p>
<br>

### RUN 03

**COMPLEXITY**: 500 points, k=50, iter = 200 | **RUNTIME**: 3110 seconds = 50 mins

_I bumped the iterations significantly in this one. In order to see the extents of the "cleanliness" of the kMeans++ solution. The outcome is quite nice. On the flipside, the compute time is quite high, but the algorithm works successfully!_ <br>
_I could either work to reduce the number of runs to see better compute times, vs quality OR work towards code optimization which is another ball-game!_

<br>
<p align="center" width="100%">
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo3_250526.gif" width="500">
  
<br>
  <img src="https://github.com/gasingh/k-means/blob/main/Screenshot%202025-05-26%20231348.png" width="1000">
  </p>

<br>

### RUN 04 

**COMPLEXITY**: 2503 points, k=50, iter = 20 | **RUNTIME**: 219 seconds = 3.5 mins

_Ran the kMeans++ routine on the Stanford Bunny! Clustering seems to be working fine._ <br>
_Mesh source:_[graphics.stanford.edu/~mdfisher/Data/Meshes/bunny.obj](https://graphics.stanford.edu/~mdfisher/Data/Meshes/bunny.obj) <br>

<p align="center" width="100%">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_003344_.jpg" width="250"> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_001621_.jpg" width="250"> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250527_003353_.jpg" width="250"> <br>
  <br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo4_bunny_250526.gif" width="500"> 
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo5_bunny_250526_speedVizOptimized4.gif" width="500"> <br>
  <br>
  <img src="https://github.com/gasingh/k-means/blob/main/Screenshot%202025-05-27%20003152.png" width="1000">
</p>
<br>

### RUN 05 
MESH CLUSTERING BY kMEANS++!! <br>
**COMPLEXITY**: 4945 mesh faces, k=50, iter = 50 | **RUNTIME**: 9824 sec = 163.73 mins = 2 hr 43 min 44 sec <br>

_Ran the kMeans++ routine on the Stanford Bunny! However this time it's clustering meshes directly!_ <br>
_The results look stunning! (Next Step: Optimize the code for speed!!!)_ <br>

<p align="center" width="100%">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175736.jpg" width="250">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175717.jpg" width="250"><br> 
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175730.jpg" width="250">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175724.jpg" width="250"><br>  
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175912.jpg" width="250">
  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250601_175857.jpg" width="250"><br> 
  <br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demoB_250601_tim1_resize1.gif" width="500"> <br>
  <br>
  <img src="https://github.com/gasingh/k-means/blob/main/Screenshot%202025-06-01%20174303.png" width="1000">
</p>
<br>

