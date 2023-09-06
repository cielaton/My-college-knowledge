**a.**
The first for loop takes n+1
The second for loop takes n*(n+1)
The third line cost n * n
$$Total\;cost = n * (n + 1) + n + 1 + n^2 = 2n ^{2}+ 2n + 1$$
→ Complexity: $O(n^2)$ 
**b.**
The first and second for loop takes:
$\Large{\frac{(n + 1)*n}{2}} + 2$ if n is odd
$\Large{\frac{(n+1)*n}{2} + \frac{n+1}{2}} + 2$ if n is even
Since $\Large{\frac{n+1}{2}} + 2$ is constant, we only need to care about $\Large{\frac{(n+1)*n}{2}}$.
→The third line takes $\Large{\frac{(n+1)*n}{2}}$ 
$$Total \; cost = 2*\frac{(n+1)*n}{2} = n*(n+1) = n^{2}+ n$$
→ Complexity: $O(n^2)$
**c.**
