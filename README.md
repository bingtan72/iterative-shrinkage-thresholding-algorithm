# iterative-shrinkage-thresholding-algorithm

## Reference
Proximal Gradient Methods for learning
- https://en.wikipedia.org/wiki/Proximal_gradient_methods_for_learning

## Iterative Shrinkage Thresholding Algorithm (ISTA)
The class of iterative shrinkage-thresholding algorithms (ISTA) for solving linear inverse problems arising in signal/image processing. This class of methods, which can be viewed as an extension of [the classical gradient algorithm](https://en.wikipedia.org/wiki/Gradient_descent), is attractive due to its simplicity and thus is adequate for solving large-scale problems even with dense matrix data.

## Cost function 
        (P1) arg min_x 1/2 || A(x) - y ||_2^2 + L * || x ||_1.

Equivalently,

        (P2) arg min_x 1/2 || x - x_(k) ||_2^2 + L * || x ||_1,

where,

        x_(k)    = x_(k-1) - t_(k) * AT(A(x) - y).
        
(P2) is equal to `l1` [proximal operator](https://en.wikipedia.org/wiki/Proximal_operator),

        prox_(l1)(x_(k)) = soft_threshold(x, L)
        
where, 

        l1 regularization is || x ||_1.

soft_threshold is defined by,
        
        function y = soft_threshold(x, L)
        y = (max(abs(x) - L, 0)).*sign(x);
        end

## The basic iteration ISTA for solving problem (P2)
        for iter = 1 : N
            x_(k+1) = p_L( x_(k) )
        end
        
where, 

        p_(L)(x) = soft_threshold(x, L).

