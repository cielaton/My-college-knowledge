**a.**
The first for loop takes n times
The second for loop takes n times
$$T(n) = n^2$$
**b.**
The first and second for loop takes:
$\Large{\frac{(n + 1)*n}{2}} + 2$ if n is odd
$\Large{\frac{(n+1)*n}{2} + \frac{n+1}{2}} + 2$ if n is even
Since $\Large{\frac{n+1}{2}} + 2$ is constant, we only need to care about $\Large{\frac{(n+1)*n}{2}}$.
$$T(n) = \frac{(n+1) * n}{2}$$ 
**c.**
The f
