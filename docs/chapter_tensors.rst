
*******
Tensors
*******

What is a tensor
================

What is a Tensor? Tensors are simply mathematical objects that can be used to describe physical properties, just like scalars and vectors. In fact tensors are merely a generalisation of scalars and vectors; a scalar is a zero rank tensor, and a vector is a first rank tensor.


.. code-block:: matlab

  function z=Fast_Fourier_Transform(x,nfft)
  N=length(x);
  z=zeros(1,nfft);
  Sum=0;
  for k=1:nfft
      for jj=1:N
          Sum=Sum+x(jj)*exp(-2*pi*j*(jj-1)*(k-1)/nfft);
      end
      z(k)=Sum;
      Sum=0;
  end
  end
  
  
