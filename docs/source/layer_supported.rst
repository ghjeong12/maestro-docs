.. _Layers Supported:

=================
Layers Supported
=================

Current MAESTRO supports the following layer operations in a mapping.

*	  CONV2D (CONV)
MAESTRO supports CONV2D operations (CONV layers in most CNNs)
*    Depth-wise convolution (DWCONV)
MAESTRO supports depth-wise convolutions. To specify depth-wise separable convolutions, please use CONV2D for point-wise convolution part.
*    Transposed Convolution (TRCONV)
MAESTRO supports transposed convolution that doubles the resolution of a featuremap (2X upconv)
*    Fully-connected (FC)
FC layers are indirectly supported via CONV2D operation. To model FC, please follow the following rule regarding layer dimension sizes: Y = R = 1, X = S, c = number of input features, k = number of output features
*    Matrix Multiplication (GEMM)
GEMM operations are indirectly supported via CONV2D operation. To specify GEMM, please follow the following rule regarding layer dimension sizes: Assuming standard M, N, K convention of GEMMs, C = K (in GEMM), Y = M (in GEMM), K = N (in GEMM), X =  R = S = 1

.. note::
   For more information on the Mapping, please see
   :ref:`Mapping Definition`.
