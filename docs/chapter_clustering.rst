
Clustering
==========

Clustering is grouping a set of objects such that objects in the same group (i.e. cluster) are more similar to each other in some sense than to objects of different groups.

To exploit data for diagnostics, prediction and control, dominant features of the data must be extracted. In the opening chapter of this book, SVD and PCA were introduced as methods for determining the dominant correlated structures contained within a data set. In the eigenfaces example of Sec. 1.6, for instance, the dominant features of a large number of cropped face images were shown. These eigenfaces, which are ordered by their ability to account for commonality (correlation) across the data base of faces was guaranteed to give the best set of r features for reconstructing a given face in an l2 sense with a rank-r truncation. The eigenface modes gave clear and interpretable features for identifying faces, including highlighting the eyes, nose and mouth regions as might be expected. Importantly, instead of working with the high-dimensional measurement space, the feature space allows one to consider a significantly reduced subspace where diagnostics can be performed.

K-means algorithm
-----------------
The term "k-means" was first used by James MacQueen in 1967, though the idea goes back to Hugo Steinhaus in 1957. Our specific clustering problem:

Given: a set of :math:`n` observations :math:`\{x_{1}, x_{2},\ldots, x_{n}\}`, where each observation is a d-dimensional real vector
Given: a number of clusters :math:`k`
Compute: a cluster assignment mapping :math:`C(x_{i}) \in \{1, \ldots, k\}` that minimizes the *within cluster sum of squares (WCSS)*:

.. math::
  
  \sum_{i=1}^{n}\left\|x_{i}-\mu_{C\left(i_{i}\right)}\right\|^{2}
  
where centroid :math:`\mu_{C\left(i_{i}\right)}` is the mean of the points in cluster :math:`C\left(i_{i}\right)`. 

General algorithm goes like this:

Randomly choose :math:`k` cluster centroids :math:`\mu_{1}, \mu_{2}, \ldots \mu_{k}` and arbitrarily initialize cluster assignment mapping :math:`C`.
While remapping :math:`C` from each 𝒙_𝑖 to its closest centroid :math:`\mu_{j}` causes a change in :math:`C`:
Recompute :math:`\mu_{1}, \mu_{2}, \ldots \mu_{k}` according to the new :math:`C`

In order to minimize the WCSS, we alternately:

Recompute :math:`C` to minimize the WCSS holding :math:`\mu_{j}` fixed.
Recompute :math:`\mu_{j}` to minimize the WCSS holding :math:`C` fixed.

In minimizing the WCSS, we seek a clustering that minimizes Euclidean distance variance within clusters.

