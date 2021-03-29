.. _chapter_regression:

**********
Regression
**********

Machine learning is based upon optimization techniques for data. The goal is to find both a low-rank subspace for optimally embedding the data, as well as regression methods for clustering and classification of different data types.
Machine learning thus provides a principled set of mathematical methods for extracting meaningful features from data, i.e. data mining, as well as binning the data into distinct and meaningful patterns that can be exploited for decision making, state estimation and forecasting. 
Specifically, it learns from and makes predictions based on data.
For business applications, this is often called predictive analytics, and it is at the forefront of modern data-driven decision making. In an integrated system, such as is found in autonomous robotics, various machine learning components (e.g., for processing visual and tactile stimulus) can be integrated to form what we now call artificial intelligence (AI). To be explicit: AI is built upon integrated machine learning algorithms, which in turn are fundamentally rooted in optimization.
Regression methods are used to find the best model for the given labeled data, via optimization. This model is then used for prediction and classification using new data. There are important variants of supervised methods, including semi-supervised learning in which incomplete training is given so that some of the input/output relationships are missing, i.e. for some input data, the actual output is missing. Active learning is another common subclass of supervised methods whereby the algorithm can only obtain training labels for a limited set of instances, based on a budget, and also has to optimize its choice of objects to acquire labels for. In an interactive framework, these can be presented to the user for labeling. Finally, in reinforcement learning, rewards or punishments are the training labels that help shape the regression architecture in order to build the best model.


Least squares using matrices
----------------------------
https://www.youtube.com/watch?v=RlQBEhLhM8Y&list=PLkZjai-2Jcxlg-Z1roB0pUwFU-P58tvOx&index=27

Normal equation solution of the least-squares problem
-----------------------------------------------------

Adopted from https://www.geeksforgeeks.org/ml-normal-equation-in-linear-regression/

Normal Equation in Linear Regression - Normal Equation is an analytical approach to Linear Regression with a Least Square Cost Function. We can directly find out the value of :math'`\theta' without using Gradient Descent. Following this approach is an effective and a time-saving option when are working with a dataset with small features.

The normal equation is as follows:

.. math::

  \theta = (X^{T}X)^{-1}\cdot(X^{T}y)
  
In the above equation, :math:`theta` is the hypothesis parameters that define it the best, :math:`X`, input feature value of each instance, and :math:`y`, output value of each instance. Maths Behind the equation – Given the hypothesis function

.. math::
  
  h(\theta)=\theta_{0}x_{0}+\theta_{1}x_{1}+\ldots+\theta_{n}x_{n}
  
where, n : the no. of features in the data set. x0 : 1 (for vector multiplication). Notice that this is dot product between θ and x values. So for the convenience to solve we can write it as: :math:`h(\theta)=\theta^{T}x`.

The motive in Linear Regression is to minimize the cost function:

.. math::

  \mathrm{J}(\Theta)=\frac{1}{2 m} \sum_{i=1}^{m} \frac{1}{2}\left[h_{\Theta}\left(x^{(i)}\right)-y^{(i)}\right]^{2}
  
where, xi : the input value of iih training example. m : no. of training instances n : no. of data-set features yi : the expected result of ith instance  

Let us representing cost function in a vector form. This can further be reduced to :math:`X\theta - y`. But each residual value is squared. We cannot simply square the above expression. As the square of a vector/matrix is not equal to the square of each of its values. So to get the squared value, multiply the vector/matrix with its transpose. So, the final equation derived is

.. math::
  
  (X\theta - y)^{T}(X\theta - y)
  
Therefore, the cost function is

.. math::
  
  Cost = (X\theta - y)^{T}(X\theta - y)
  
So, now getting the value of θ using derivative

.. math::
  
  \frac{\partial J_{\theta}}{\partial \theta}=\frac{\partial}{\partial \theta}\left[(X \theta-y)^{T}(X \theta-y)\right]
  
That is

.. math::
  
  \frac{\partial J_{\theta}}{\partial \theta}=2X^{T}X\theta - 2X^{T}y

When we set :math:`Cost'(\theta)=0`, i.e., :math:`2X^{T}X\theta - 2X^{T}y = 0`, we obtain

.. math::

  2X^{T}X\theta = 2X^{T}y
  
In other words,

.. math::

  (X^{T}X)^{-1}(X^{T}X)\theta = (X^{T}X)^{-1})(X^{T}y)
  
Therefore, we obtain the final format   

.. math::

  2X^{T}X\theta = 2X^{T}y

So, this is the finally derived Normal Equation with θ giving the minimum cost value.



  





