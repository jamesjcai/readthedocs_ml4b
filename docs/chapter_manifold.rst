

********
Manifold
********

What is a manifold
==================

https://youtu.be/evGm6IJKrDI?t=2336

Kernel PCA
----------

use their eigen dimensions as your new kernel pca dimensions this is the basic idea behind a lot of non-linear dimensionality reduction methods several of them and we'll talk about two specific variants uh which are diffusion maps and laplacian eigenmaps which turn out to be very useful for example for clustering the data or for understanding progressions in the data and but they're not necessarily specifically optimized for visualization so the first method i'll talk about is diffusion maps so diffusion maps do something a little bit beyond just computing the affinity matrix so in computing a diffusion map you go from the data here the data's in two dimensions you compute the distance matrix which is pairwise distances between all points now you turn the distance into an infinity so you start to get affinities that drop off quickly so your strong connections kind of go along the shape of the data and you could already i can decompose this matrix and get some kind of kernel pca the diffusion maps go a little bit beyond this in order to denoise and really coalesce to the main nonlinear dimensions of the data and the way they do this is on top of this graph that you've defined they define another probabilistic affinity matrix or probabilistic transition matrix which is a markov matrix and the way they do that is they take your affinities in each row in each row of the affinity matrix you have the you have some affinities to all the other points in the data what they do is they just divide by the sum of those affinities and then you get probabilities you get a probability that something is a neighbor and it'll
 
Diffusion Map
--------------
https://youtu.be/evGm6IJKrDI?t=2940
variants uh which are diffusion maps and laplacian eigenmaps which turn out to be very useful for example for clustering the data or for understanding progressions in the data and but they're not necessarily specifically optimized for visualization so the first method i'll talk about is diffusion maps so diffusion maps do something a little bit beyond just computing the affinity matrix so in computing a diffusion map you go from the data here the data's in two dimensions you compute the distance matrix which is pairwise distances between all points now you turn the distance into an infinity so you start to get affinities that drop off quickly so your strong connections kind of go along the shape of the data and you could already i can decompose this matrix and get some kind of kernel pca the diffusion maps go a little bit beyond this in order to denoise and really coalesce to the main nonlinear dimensions of the data and the way they do this is on top of this graph that you've defined they define another probabilistic affinity matrix or probabilistic transition matrix which is a markov matrix and the way they do that is they take your affinities in each row in each row of the affinity matrix you have the you have some affinities to all the other points in the data what they do is they just divide by the sum of those affinities and then you get probabilities you get a probability that something is a neighbor and it'll be a very high probability if your affinity was high and a low probability if your infinity was low because it's just a normalization on the affinity that turns them into probabilities now the next step the diffusion maps use is they actually use a random walk based on these probabilities so you're standing on a particular point and you have a particular probability of jumping to this neighbor and a particular probability of jumping to this neighbor a random walk on a graph is also called diffusion on a graph it turns out if you had infinite number of points it would be equivalent to heat diffusion and that's why it's called diffusion rather than random walking sometimes but they're exactly the same thing so if i was at this point we have some probability of jumping to this point 0.4 and that means that this point in the future dimensional space was actually more similar to this point so you're jumping the similar points with more higher probability jumping to dissimilar points with lower probability it turns out this kind of a markov transition matrix that you get from diffusion um is very useful because you can sort of clean up your affinities and really hone in on the non-linear non-linear coil dimension of the data when you eigen decompose it as well so 

Laplacian Eigenmap
------------------

.. code-block:: matlab

 %% create swiss roll data
 N = 2^11; % number of points considered
 t = rand(1,N);
 t = sort(4*pi*sqrt(t))'; 

 %t = sort(generateRVFromRand(2^11,@(x)1/32/pi^2*x,@(x)4*pi*sqrt(x)))';
 z = 8*pi*rand(N,1); % random heights
 x = (t+.1).*cos(t);
 y = (t+.1).*sin(t);
 data = [x,y,z]; % data of interest is in the form of a n-by-3 matrix

 %% visualize the data
 cmap = jet(N);
 scatter3(x,y,z,20,cmap);
 title('Original data');

 %% Changing these values will lead to different nonlinear embeddings
 knn    = ceil(0.03*N); % each patch will only look at its knn nearest neighbors in R^d
 sigma2 = 100; % determines strength of connection in graph... see below

 %% now let's get pairwise distance info and create graph 
 m                = size(data,1);
 dt               = squareform(pdist(data));
 [srtdDt,srtdIdx] = sort(dt,'ascend');
 dt               = srtdDt(1:knn+1,:);
 nidx             = srtdIdx(1:knn+1,:);

 % nz   = dt(:) > 0;
 % mind = min(dt(nz));
 % maxd = max(dt(nz));

 % compute weights
 tempW  = exp(-dt.^2/sigma2); 

 % build weight matrix
 i = repmat(1:m,knn+1,1);
 W = sparse(i(:),double(nidx(:)),tempW(:),m,m); 
 W = max(W,W'); % for undirected graph.

 % The original normalized graph Laplacian, non-corrected for density
 ld = diag(sum(W,2).^(-1/2));
 DO = ld*W*ld;
 DO = max(DO,DO');%(DO + DO')/2;

 % get eigenvectors
 [v,d] = eigs(DO,10,'la');

 eigVecIdx = nchoosek(2:4,2);
 for i = 1:size(eigVecIdx,1)
     figure,scatter(v(:,eigVecIdx(i,1)),v(:,eigVecIdx(i,2)),20,cmap)
     title('Nonlinear embedding');
     xlabel(['\phi_',num2str(eigVecIdx(i,1))]);
     ylabel(['\phi_',num2str(eigVecIdx(i,2))]);
 end

 figure,subplot(1,2,1)
 scatter3(x,y,z,20,cmap);
 title('Original data');
 subplot(1,2,2)
 scatter(v(:,2),v(:,4),20,cmap)
 title('Nonlinear embedding')




