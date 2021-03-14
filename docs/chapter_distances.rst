
Distances
=========

Euclidean Distance
------------------
In mathematics, the Euclidean distance between two points in Euclidean space is the length of a line segment between the two points. It can be calculated from the Cartesian coordinates of the points using the Pythagorean theorem, therefore occasionally being called the Pythagorean distance. These names come from the ancient Greek mathematicians Euclid and Pythagoras, although Euclid did not represent distances as numbers, and the connection from the Pythagorean theorem to distance calculation was not made until the 18th century.

The distance between two objects that are not points is usually defined to be the smallest distance among pairs of points from the two objects. Formulas are known for computing distances between different types of objects, such as the distance from a point to a line. In advanced mathematics, the concept of distance has been generalized to abstract metric spaces, and other distances than Euclidean have been studied. In some applications in statistics and optimization, the square of the Euclidean distance is used instead of the distance itself.


Role for cross-referencing equations via their label.  This currently works only within the same document.  Example::

.. math:: e^{i\pi} + 1 = 0
  :label: euler

Euler's identity, equation :eq:`euler`, was elected one of the most beautiful mathematical formulas.

Cosine Distance
---------------

.. raw:: html

    <object data="https://www.intmath.com/trigonometric-functions/svg/svgphp-sin-cos-tan-csc-sec-cot-2-s0.svg" type="image/svg+xml"></object>

https://www.intmath.com/trigonometric-functions/2-sin-cos-tan-csc-sec-cot.php

Relation between Euclidean Distance and Cosine Distance
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Mahalinobis Distance
--------------------



Distance Matrix
---------------
EDM 


Gram Matrix
-----------
https://mathworld.wolfram.com/GramMatrix.html
https://en.wikipedia.org/wiki/Gramian_matrix
An important application is to compute linear independence: a set of vectors are linearly independent if and only if the Gram determinant (the determinant of the Gram matrix) is non-zero.

Multidimensional Scalling
-------------------------


Distance to Affinity via Kernels
--------------------------------

https://youtu.be/RS5xoGE2yZ4?t=2670

o usually in a graph things with small distances have high weights or high adjacency scores and things with low distances or high distances have low similarity so usually graphs are actually represented by matrices that look more like this where things that are um close like points to each other have high weights so the in this graph there's high weights for self edges and low weights for things that are farther away so the farthest away are a0 and for example here a2 so these have low weights so the way you get from distances to similarities is actually pretty well studied and one of the ways you can get from distances to similarities or affinities that's another term for similarity is to take your distance and put it through what's called a kernel function um notice these are examples of many kernel functions and notice they all have this property where they reach their maximum value at zero and anything after that anything positive which all distances are has a lower value than zero and so they have this kind of inverting quality so if you put in a high distance into a kernel you'll get a low similarity if you put in zero or perfect perfectly similar no distance you get a high similarity so the basic idea for getting from distances to similarities which directly describe the edge weights in a graph are to take your distance and put it through one of these functions with the most common one being the gaussian kernel here you have kind of a rather wide gaussian kernel and if you put it through this gaussian kernel depending on the bandwidth of the kernel the bandwidth of the kernel is going to be a parameter that you play with in this this kind of graph model um it's going to give you a similarity that's scaled so here i actually did that i put the distances that you saw here through a gaussian kernel which is describing a normal distribution with mean zero and standard deviation one and when i do that these are the affinities that i get i could and i would get completely different affinities from this um but now what i've done is i've taken this data and i've re-represented it as a graph the weights on the graph are given by these off-diagonal entries in this adjacency or affinity matrix and now i have an idea of how the points are all related to each other now notice that in this representation i don't i no longer have the features the features aren't explicitly in this representation but it turns out you can use derivations of this representation to understand what's going on with the features this is the reason why a lot of the unsupervised machine learning algorithms are more sensitive to the number of observations than they are to the number of features and would work just as well with 10 features as they do with 20 000 as a single cell rna sequence okay um a modification of this graph so these these are fully connected graphs they just have different weights on each of the edges a modification of that is to zero out some of those edges especially the small ones with low weights and a really common way to do that is using what's called a nearest neighbor's graph a nearest neighbor's graph will only have connections between a vertex and its k nearest neighbors it could still be weighted so for here for example if we did a one nearest neighbor's graph then we'd zero out the connection between a0 and a2 because a0 is most connected to a1 and vice versa um and so in this row we'd zero this one out but a2 still has distances and it turns out a2 is closer to a1 so you zero out the a2 a0 edge um so that leads to a sparser representation which is good computationally 


