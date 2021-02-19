.. _chapter_vectors:

*******
Vectors
*******


What is a vector
================

https://stattrek.com/matrix-algebra/matrix.aspx
https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#headings


How do you calculate a vector perpendicular to another? 
https://www.quora.com/How-do-I-find-a-vector-perpendicular-to-another-vector

In 3D there are many vectors that are perpendicular to a given vector. Just imagine stem of hair brush to be given vector then each hair of the brush is a vector perpendicular to stem-vector. While there are of course infinite vectors perpendicular to any one 3d vector, here is a simple answer to your question. If your vector is (i,j,k) then one possible orthogonal vector is: (j-k, k-i, -i-j)

In 2D if the given vector is (a,b) then vector perpendicular to it is (-b, a). Their dot product is zero.

In three dimensions, there’s a special technique: Suppose you start with a vector (x,y,z).

Take another vector (a,b,c) - any vector will do. Now, consider (yc-zb,az-cx,bx-ay). That vector will be perpendicular to (x,y,z) [and also to (a,b,c)] - I leave proving this to you. In order to get a nonzero vector, just choose an (a,b,c) appropriately.

If you start with a 2-d vector (x,y), pretend you have the vector (x,y,0) and let (a,b,c)=(0,0,1). This will give some other vector (f,g,0), which means a perpendicular vector is (f,g). This gives a special formula: a vector perpendicular to (x,y) is (y,-x) [or (-y,x)].

To get a magnitude of 1, just divide any of those vectors by their magnitude.

.. code:: text

  function [a1cmp] = ortc(a1)
  %ORTC Orthogonal complement of column matrix.
  %
  % [A1CMP] = ORTC(A1) produces an orthogonal complement of a column
  %         type matrix via QR decomposition.
  %

  % R. Y. Chiang & M. G. Safonov 7/85
  % Copyright 1988-2004 The MathWorks, Inc.
  % All Rights Reserved.
  % ----------------------------------------------------------------
  %
  [ra1,ca1] = size(a1);
  if ra1 == ca1
       a1cmp = zeros(ra1);
  else
       [u,r] = qr(a1);
       a1cmp = u(:,ca1+1:ra1);
  end
  %
  % ----- End of ORTC.M ---- RYC/MGS 7/85 %
