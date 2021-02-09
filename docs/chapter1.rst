.. _chapter1:

Vectors & Matrices
==================

https://stattrek.com/matrix-algebra/matrix.aspx

What is a Matrix?
-----------------
This lesson introduces the matrix - the rectangular array at the heart of matrix algebra. Matrix algebra is used quite a bit in advanced statistics, largely because it provides two benefits.

Compact notation for describing sets of data and sets of equations.
Efficient methods for manipulating sets of data and solving sets of equations.

Matrix Definition
^^^^^^^^^^^^^^^^^
A matrix is a rectangular array of numbers arranged in rows and columns. The array of numbers below is an example of a matrix.

The number of rows and columns that a matrix has is called its dimension or its order. By convention, rows are listed first; and columns, second. Thus, we would say that the dimension (or order) of the above matrix is 3 x 4, meaning that it has 3 rows and 4 columns.

Numbers that appear in the rows and columns of a matrix are called elements of the matrix. In the above matrix, the element in the first column of the first row is 21; the element in the second column of the first row is 62; and so on.

Matrix Notation
^^^^^^^^^^^^^^^
Statisticians use symbols to identify matrix elements and matrices.

Types of Matrices
-----------------
This lesson describes a few of the more important types of matrices: transpose matrices, vectors, and different kinds of square matrices.

Transpose Matrix
^^^^^^^^^^^^^^^^
The transpose of one matrix is another matrix that is obtained by using rows from the first matrix as columns in the second matrix.

For example, it is easy to see that the transpose of matrix A is A'. Row 1 of matrix A becomes column 1 of A'; row 2 of A becomes column 2 of A'; and row 3 of A becomes column 3 of A'.

Square Matrices
^^^^^^^^^^^^^^^
A square matrix is an n x n matrix; that is, a matrix with the same number of rows as columns. In this section, we describe several special kinds of square matrix.


The Geometry of Matrix Multiplication
-------------------------------------

Norm
----
https://medium.com/towards-artificial-intelligence/basic-linear-algebra-for-deep-learning-and-machine-learning-ml-python-tutorial-444e23db3e9e#60ee

Dot product
-----------

Eigenvalues & Eigenvectors
--------------------------



.. _vectors--matrices:

Matrix Multiplication
---------------------
https://xaktly.com/MatrixOperations.html

https://link.springer.com/chapter/10.1007/978-981-10-6808-9\ `\ \_1`_ -

https://julienbeaulieu.gitbook.io/wiki/sciences/math/linear-algebra/operations
-

In this chapter, you will discover the eigendecomposition, eigenvectors,
and eigenvalues in linear algebra. After completing this tutorial, you
will know: What an eigendecomposition is and the role of eigenvectors
and eigenvalues. How to calculate an eigendecomposition in Python with
NumPy. How to confirm a vector is an eigenvector and how to reconstruct
a matrix from eigenvectors and eigenvalues. This tutorial is divided
into 5 parts; they are: Eigendecomposition of a Matrix, Eigenvectors and
Eigenvalues, Calculation of Eigendecomposition, Confirm an Eigenvector
and Eigenvalue, Reconstruct Original Matrix Transpose a vector Find The
Maximum And MinimumDescribe An ArrayCreate A VectorCreate A Sparse
Matrix

https://textbooks.math.gatech.edu/ila/overview.html - Most engineering
problems, no matter how complicated, can be reduced to linear algebra:

.. image:: ../.gitbook/assets/image%20%2859%29.png

Scale values in a vector
~~~~~~~~~~~~~~~~~~~~~~~~

zscore(x)(x-mean(x))/(max(x)-min(x))

https://stats.stackexchange.com/questions/281162/scale-a-number-between-a-range\ https://stats.stackexchange.com/questions/178626/how-to-normalize-data-between-1-and-1

.. code:: text

   function dataNormalized=normalizeData(data)
       %Normalize Sample Data
       dataNormalized=zeros(size(data));
       for j=1:size(data,2)
       dataNormalized(:,j)=(data(:,j)-min(data(:,j)))/( max(data(:,j))-min(data(:,j)) );
       end
   end

Mean normalization
~~~~~~~~~~~~~~~~~~

https://en.wikipedia.org/wiki/Feature\ `\ \_scaling`_

Normalization rescales the values into a range of [0,1]. This might be
useful in some cases where all parameters need to have the same positive
scale. However, the outliers from the data set are
lost.Xchanged=X−XminXmax−XminStandardization rescales data to have a
mean (μ) of 0 and standard deviation (σ) of 1 (unit
variance).Xchanged=X−μσ

Linear independence
-------------------

https://www.youtube.com/watch?v=xfhzwNkMNg4 -

Inverse of a 3x3 Matrix using Adjoint
-------------------------------------

https://www.youtube.com/watch?v=xfhzwNkMNg4 -

https://www.youtube.com/watch?v=HYWeEx21WWw -

.. image:: ../.gitbook/assets/image%20%2862%29.png

`Transpose A Vector Or Matrix`_

-  [Selecting Elements In An Array](https://chrisal

.. _\ \_1: https://link.springer.com/chapter/10.1007/978-981-10-6808-9_1
.. _\ \_scaling: https://en.wikipedia.org/wiki/Feature_scaling
.. _Transpose A Vector Or Matrix: https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/transpose_a_vector_or_matrix/
