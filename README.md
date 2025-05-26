# kmeans++ for Rhino3D
kMeans++ is an unsupervised machine learning algorithm.

`machine learning` `unsupervised learning` `AI` `3d` `Rhino3D`

## **INTRODUCTION**
K-means (KM) algorithm groups N data points into k clusters by minimizing the sum of squared distances between every point and its nearest cluster mean (centroid). This objective function is called sum-of-squared errors (SSE). K-means was originally designed for minimizing SSE of numerical data. [1]

<img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_205909.jpg" width="300"> <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_210043.jpg" width="300">  <img src="https://github.com/gasingh/k-means/blob/main/ViewCapture20250526_213704.jpg" width="300">
<br>

References:
- [1. How much can k-means be improved by using better initialization and repeats? - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0031320319301608)
- [2. k-means clustering - Wikipedia](https://en.wikipedia.org/wiki/K-means_clustering)
- [3. Stanford: kMeansPP.pdf](https://theory.stanford.edu/~sergei/papers/kMeansPP-soda.pdf)
- [4. k-means++ - Wikipedia](https://en.wikipedia.org/wiki/K-means%2B%2B)
- [5. KMeans — scikit-learn 1.6.1 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)

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
- There is currently no seed initialized in the randomization, and so the results are more accurate. When specifying seeds (for example 42), sometimes the global minimum (SSD error) is never found, and it might need more runs. So for now, it's excluded.
- The technique relies heavily on initial seeding of the initial centroid, the rest of the k successive means are weighted selections from the initial seed. Successive initializations result in varied SSDs. Later we choose the solution with the least error.
- I also coded the traditional k-means. Where the initialization is by random choices (initial randomised cluster), and then clustering data by forming SD based associative collections. The k-means seems to be a more simpler and straightforward solution to code where we employ a simple weights heuristic to compute the centroid clusters.

## **DEMOS**

### **A demo on a simple point cloud** <br>

_This is a simple dataset with only 26 points. And the clustering is instantaneous._

<br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo1_250526.gif" width="500"> 
<br>

### **A demo on a point clouds of 500 points!** <br> 

_This is a randomly sampled point cloud of 500 points and we create 25 clusters. The compute time is approx. 111 seconds. We additionally created point groups and respective bounding boxes to visually clarify the solution of the kmeans clustering. Although we also introduced the randomised coloring, it's easier to mine the results with respective bounding boxes._

<br>
  <img src="https://github.com/gasingh/k-means/blob/main/kMeansPlusPlus_demo2_250526.gif" width="500">
<br>
