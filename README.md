# InfiniteArrays.jl
A Julia package for representing infinite-dimensional arrays


This is a WIP package. When finished, the following behaviour should work:
```julia
B = ones(1,∞)  # creates 1 x ∞ InfMatrix of all ones
T = diagm(repeated(0.5)) + diagm(repeated(-0.5),2)  # a Toeplitz operator
e₁ = [1; zeros(∞)]   # a PaddedInfVector
(e₁*e₁')/2 # a PaddedInfMatrix: it knows to manipulate on the data
C = T + (e₁*e₁')/2    # a PlusInfMatrix, it adds the rank-1 perturbation lazily
D = diagm(1:∞,1)   # Chebyshev derivative, represented as a DiagonalInfMatrix
A = [B; D+C]   # A ConcatenatedInfMatrix
u = A \ [2; zeros(∞)]  # Finds Chebyshev coefficients of solution to u'+u = 0, u(1) = 2, using adaptive QR
```