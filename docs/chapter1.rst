.. _chapter1:

Vectors & Matrices
==================

Norm
----
https://medium.com/towards-artificial-intelligence/basic-linear-algebra-for-deep-learning-and-machine-learning-ml-python-tutorial-444e23db3e9e#60ee

Dot product
-----------

Eigenvalues & Eigenvectors
--------------------------


[https://link.springer.com/chapter/10.1007/978-981-10-6808-9\_1](https://link.springer.com/chapter/10.1007/978-981-10-6808-9_1) -



[https://julienbeaulieu.gitbook.io/wiki/sciences/math/linear-algebra/operations](https://julienbeaulieu.gitbook.io/wiki/sciences/math/linear-algebra/operations) -

In this chapter, you will discover the eigendecomposition, eigenvectors, and eigenvalues in linear algebra. After completing this tutorial, you will know: What an eigendecomposition is and the role of eigenvectors and eigenvalues. How to calculate an eigendecomposition in Python with NumPy. How to confirm a vector is an eigenvector and how to reconstruct a matrix from eigenvectors and eigenvalues. This tutorial is divided into 5 parts; they are: Eigendecomposition of a Matrix, Eigenvectors and Eigenvalues, Calculation of Eigendecomposition, Confirm an Eigenvector and Eigenvalue, Reconstruct Original Matrix Transpose a vector Find The Maximum And MinimumDescribe An ArrayCreate A VectorCreate A Sparse Matrix

[https://textbooks.math.gatech.edu/ila/overview.html](https://textbooks.math.gatech.edu/ila/overview.html) - Most engineering problems, no matter how complicated, can be reduced to linear algebra: 

![](../.gitbook/assets/image%20%2859%29.png)

### Scale values in a vector

zscore\(x\)\(x-mean\(x\)\)/\(max\(x\)-min\(x\)\)

[https://stats.stackexchange.com/questions/281162/scale-a-number-between-a-range](https://stats.stackexchange.com/questions/281162/scale-a-number-between-a-range)[https://stats.stackexchange.com/questions/178626/how-to-normalize-data-between-1-and-1](https://stats.stackexchange.com/questions/178626/how-to-normalize-data-between-1-and-1)

```text
function dataNormalized=normalizeData(data)
    %Normalize Sample Data
    dataNormalized=zeros(size(data));
    for j=1:size(data,2)
    dataNormalized(:,j)=(data(:,j)-min(data(:,j)))/( max(data(:,j))-min(data(:,j)) );
    end
end
```

### Mean normalization

[https://en.wikipedia.org/wiki/Feature\_scaling](https://en.wikipedia.org/wiki/Feature_scaling)

Normalization rescales the values into a range of \[0,1\]. This might be useful in some cases where all parameters need to have the same positive scale. However, the outliers from the data set are lost.Xchanged=X−XminXmax−XminStandardization rescales data to have a mean \(μ\) of 0 and standard deviation \(σ\) of 1 \(unit variance\).Xchanged=X−μσ

## 

## Linear independence

[https://www.youtube.com/watch?v=xfhzwNkMNg4](https://www.youtube.com/watch?v=xfhzwNkMNg4) - 

## Inverse of a 3x3 Matrix using Adjoint

[https://www.youtube.com/watch?v=xfhzwNkMNg4](https://www.youtube.com/watch?v=xfhzwNkMNg4) - 

[https://www.youtube.com/watch?v=HYWeEx21WWw](https://www.youtube.com/watch?v=HYWeEx21WWw) -

![](../.gitbook/assets/image%20%2862%29.png)

[Transpose A Vector Or Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/transpose_a_vector_or_matrix/)

* [Selecting Elements In An Array](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/selecting_elements_in_an_array/)
* [Reshape An Array](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/reshape_an_array/)
* [Invert A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/invert_a_matrix/)
* [Getting The Diagonal Of A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/getting_the_diagonal_of_a_matrix/)
* [Flatten A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/flatten_a_matrix/)
* [Find The Rank Of A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/find_the_rank_of_a_matrix/)
* [Create A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/create_a_matrix/)
* [Converting A Dictionary Into A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/converting_a_dictionary_into_a_matrix/)
* [Calculate The Trace Of A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/calculate_the_trace_of_a_matrix/)
* [Calculate The Determinant Of A Matrix](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/calculate_the_determinant_of_a_matrix/)
* [Calculate The Average, Variance, And Standard Deviation](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/calculate_average_variance_and_standard_deviation/)
* [Calculate Dot Product Of Two Vectors](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/calculate_dot_product_of_two_vectors/)
* [Apply Operations To Elements](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/apply_operations_to_elements/)
* [Adding And Subtracting Matrices](https://chrisalbon.com/machine_learning/vectors_matrices_and_arrays/adding_and_subtracting_matrices/)

### Cosine similarity between two vectors

 [https://stackoverflow.com/questions/48101542/cosine-similarity-built-in-function-in-matlab/48102614](https://stackoverflow.com/questions/48101542/cosine-similarity-built-in-function-in-matlab/48102614)

```text
u=rand(100,1);
v=randn(100,1);
pdist([u'; v'],'cosine')
1-u'*v./(norm(u)*norm(v))
```



{% embed url="http://mathonline.wikidot.com/determining-a-vector-given-two-points" %}

## Distance from a point to a line

### Line defined by an equation

[https://en.wikipedia.org/wiki/Distance\_from\_a\_point\_to\_a\_line\#Line\_defined\_by\_an\_equation](https://en.wikipedia.org/wiki/Distance_from_a_point_to_a_line#Line_defined_by_an_equation) - 

see application in SVM

In the case of a line in the plane given by the equation  where ''a'', ''b'' and ''c'' are \[\[real number\|real\]\] constants with ''a'' and ''b'' not both zero, the distance from the line to a point \(''x''0,''y''0\) is

:\operatorname{distance}\(ax+by+c=0, \(x\_0, y\_0\)\) = \frac{\|ax\_0+by\_0+c\|}{\sqrt{a^2+b^2}}.

The point on this line which is closest to \(''x''0,''y''0\) has coordinates: :x = \frac{b\(bx\_0 - ay\_0\)-ac}{a^2 + b^2} \text{ and } y = \frac{a\(-bx\_0 + ay\_0\) - bc}{a^2+b^2}.

In the case of a line in the plane given by the equation ax + by + c = 0, where a, b and c are [real](https://en.wikipedia.org/wiki/Real_number) constants with a and b not both zero, the distance from the line to a point \(x0,y0\) is[\[1\]](https://en.wikipedia.org/wiki/Distance_from_a_point_to_a_line#cite_note-1)[\[2\]](https://en.wikipedia.org/wiki/Distance_from_a_point_to_a_line#cite_note-2):p.14{\displaystyle \operatorname {distance} \(ax+by+c=0,\(x\_{0},y\_{0}\)\)={\frac {\|ax\_{0}+by\_{0}+c\|}{\sqrt {a^{2}+b^{2}}}}.}![\operatorname{distance}\(ax+by+c=0, \(x\_0, y\_0\)\) = \frac{\|ax\_0+by\_0+c\|}{\sqrt{a^2+b^2}}. ](https://wikimedia.org/api/rest_v1/media/math/render/svg/baff35b2a747a59d5a113dcabea8fda7d2c09288)

The point on this line which is closest to \(x0,y0\) has coordinates:

$$x={\frac {b(bx_{0}-ay_{0})-ac}{a^{2}+b^{2}}}$$ and 



### Line defined by two points





## Nonlinear correlation coefficient <a id="author-label-460226"></a>

[http://www.diva-portal.org/smash/record.jsf?pid=diva2%3A551505&dswid=-1600](http://www.diva-portal.org/smash/record.jsf?pid=diva2%3A551505&dswid=-1600)

## R-squared explained

![https://www.youtube.com/watch?v=2AQKmw14mHM](../.gitbook/assets/image.png)

![](../.gitbook/assets/image%20%286%29.png)

## References <a id="author-label-230020"></a>

[https://www.amazon.com/No-bullshit-guide-linear-algebra/dp/0992001021/ref=as\_li\_ss\_tl?ie=UTF8&linkCode=sl1&tag=inspiredalgor-20&linkId=1b4431e89d8fd65f6d4cbeb67fe9105c](https://www.amazon.com/No-bullshit-guide-linear-algebra/dp/0992001021/ref=as_li_ss_tl?ie=UTF8&linkCode=sl1&tag=inspiredalgor-20&linkId=1b4431e89d8fd65f6d4cbeb67fe9105c)

## What is a Matrix? <a id="author-label-649942"></a>

Sparse matrix NormEigenSVDMatrix regularizationRank of matrix

## Matrix transpose   <a id="author-label-126340"></a>

The transpose of a matrix is an operator which flips a matrix over its diagonal, that is it switches the row and column indices of the matrix by producing another matrix denoted as AT \(also written A′, Atr, tA or At\)

## Matrix inverse <a id="author-label-834751"></a>

The inverse of a matrix is commonly denoted A^\(-1\), which should not be interpreted to mean 1/A

## Matrix power <a id="author-label-242574"></a>

The power of a matrix  is defined as the matrix product of n copies of A.  A^n of a matrix A for n a nonnegative integer. Definition: Given a square matrix A, for n being a nonnegative integer, An is defined as the product matrix taking A and multiplying it by itself n-times. If A is invertible, then A−n=\(A−1\)n, or the product matrix taking A−1 and multiplying it by itself n-times.

## Covariance matrix <a id="author-label-495132"></a>

 [https://www.visiondummy.com/2014/04/geometric-interpretation-covariance-matrix/](https://www.visiondummy.com/2014/04/geometric-interpretation-covariance-matrix/)

## Elementwise multiplication of matrices <a id="author-label-651162"></a>

 \(Hadamard product\)Element-wise multiplication - MATLAB times .\* In mathematics, the Hadamard product \(also known as the Schur product\[1\] or the entrywise product\[2\]:ch. 5\) is a binary operation that takes two matrices of the same dimensions and produces another matrix of the same dimension as the operands where each element i, j is the product of elements i, j of the original two matrices. Hadamard multiplication is built into certain programming languages under various names. In MATLAB, it is known as array multiplication, or in Julia broadcast multiplication, with the symbol .\*

## Sum of the diagonal elements of matrix A <a id="author-label-878042"></a>

trace extracts the diagonal elements and adds them together with the command sum\(diag\(A\)\). The value of the trace is the same \(up to round-off error\) as the sum of the matrix eigenvalues sum\(eig\(A\)\).

## Direct sum of matrices <a id="author-label-314434"></a>

Direct sums are defined for a number of different sorts of mathematical objects, including subspaces, matrices, modules, and groups. The matrix direct sum is defined by [http://mathworld.wolfram.com/DirectSum.html](http://mathworld.wolfram.com/DirectSum.html)

There is a function in Matlab called BLKDIAG, Block diagonal concatenation of input arguments, that does what you want:  `blkdiag(A,B,C,D,...,Z)`[https://en.wikipedia.org/wiki/Matrix\_addition](https://en.wikipedia.org/wiki/Matrix_addition)

## Matrix-vector multiplication <a id="author-label-752387"></a>

[https://machinelearningmastery.com/introduction-matrices-machine-learning/](https://machinelearningmastery.com/introduction-matrices-machine-learning/)

## Matrix-matrix multiplication \(Dot Product\) <a id="author-label-483869"></a>

fdsaf

## Kronecker product <a id="author-label-655925"></a>

K = kron\(A,B\) In mathematics, the Kronecker product, denoted by ⊗, is an operation on two matrices of arbitrary size resulting in a block matrix. It is a generalization of the outer product \(which is denoted by the same symbol\) from vectors to matrices, and gives the matrix of the tensor product with respect to a standard choice of basis. The Kronecker product should not be confused with the usual matrix multiplication, which is an entirely different operation.Centralize a matrix

## scale, normalize, centering <a id="author-label-234690"></a>

function \[KN\] = normalise\(K\); KN = repmat\(1./sqrt\(diag\(K\)\),1,size\(K,1\)\).\*K.\*repmat\(\(1./sqrt\(diag\(K\)\)\)',size\(K,1\),1\);Norm This uses a random initial guess. At each iteration, it reports the 'fit' which is defined as 1-\(norm\(X-M\)/norm\(X\)\) and is loosely the proportion of the data described by the CP model, i.e., a fit of 1 is perfect.

## Centering matrix <a id="author-label-189516"></a>

[https://en.wikipedia.org/wiki/Centering\_matrix](https://en.wikipedia.org/wiki/Centering_matrixhttp://fourier.eng.hmc.edu/e176/lectures/algebra/node13.htmlhttps://stackoverflow.com/questions/37375213/centering-matrix-in-matlab)

[http://fourier.eng.hmc.edu/e176/lectures/algebra/node13.html](https://en.wikipedia.org/wiki/Centering_matrixhttp://fourier.eng.hmc.edu/e176/lectures/algebra/node13.htmlhttps://stackoverflow.com/questions/37375213/centering-matrix-in-matlab)

[https://stackoverflow.com/questions/37375213/centering-matrix-in-matlab](https://en.wikipedia.org/wiki/Centering_matrixhttp://fourier.eng.hmc.edu/e176/lectures/algebra/node13.htmlhttps://stackoverflow.com/questions/37375213/centering-matrix-in-matlab)

`A=randi([-10 10],3,3) Acent=A-repmat(mean(A,1),3,1)-repmat(mean(A,2),1,3)+mean(mean(A))*ones(size(A))function [R] = center(K) %function [R] = center(K) % % Nello Cristianini, September 2001 J = ones(1,length(K)); RowSum = mean(K); R = K - RowSum'*J - J'*RowSum + mean(RowSum);` 

[https://www.gastonsanchez.com/visually-enforced/how-to/2014/01/15/Center-data-in-R/](https://www.gastonsanchez.com/visually-enforced/how-to/2014/01/15/Center-data-in-R/)

`A=[1 4 7;2 5 8;3 6 9]A-repmat(mean(A),size(A,1),1)bsxfun(@minus, A, mean(A))A-mean(A)H=eye(3)-(1/3)*ones(3,1)*ones(3,1)'H*A`

## Center a matrix to its mean

[https://stackoverflow.com/questions/13220508/matlab-center-a-matrix-to-its-mean](https://stackoverflow.com/questions/13220508/matlab-center-a-matrix-to-its-mean)

Using a center-operator We can create the mean-center operator \\(H\\) and use it to premultiply the data matrix like so:

`# center matrix operatorcenter_operator <- function(x) {n = nrow(x)ones = rep(1, n)H = diag(n) - (1/n) * (ones %*% t(ones))H %*% x}# apply itcenter_operator(Data)`

## 

### Matrix regularization <a id="author-label-508246"></a>

### Rank of matrix <a id="author-label-719778"></a>

### Condition number \(CN\) of a matrix <a id="author-label-735498"></a>

∣∣∣∣A∣∣∣∣\*∣∣∣∣A−1∣∣∣∣⁠; where \|\|.\|\| is the matrix norm. Example \(using A and the Frobenius matrix norm\): [https://academic.oup.com/bioinformatics/article/34/11/1969/4813737](https://academic.oup.com/bioinformatics/article/34/11/1969/4813737)
