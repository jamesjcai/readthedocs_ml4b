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
