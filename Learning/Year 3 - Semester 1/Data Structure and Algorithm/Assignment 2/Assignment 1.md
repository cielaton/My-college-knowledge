#### Prob 1:

**a.**
The first for loop takes n + 1 times
The second for loop takes n \* (n + 1) times
The third line takes n \* n times
$$T(n) = n^2$$
**b.**
The first and second for loop takes:
$\Large{\frac{(n + 1)*n}{2}} + 2$ if n is odd
$\Large{\frac{(n+1)*n}{2} + \frac{n+1}{2}} + 2$ if n is even
Since $\Large{\frac{n+1}{2}} + 2$ is constant, we only need to care about $\Large{\frac{(n+1)*n}{2}}$.
$$T(n) = \frac{(n+1) * n}{2}$$ 
**c.**
The first loop takes $2^{k}= n => k = \log_2n$ times
The second loop takes n times
$$T(n) = n * log_2n$$
**d.**

#### Prob 2:
**a.** Addition
The first loop takes n + 1 times
The second loop takes n \* (n + 1) times
The third line takes n \* n times
$$T(n) = n^2$$
**b.** Multiplication
The first loop takes n + 2 times
The second loop takes (n + 1) \* (n + 2) times
The line `sum = 0` takes (n + 1) \* (n + 1) times
The third for loop takes (n + 1) \* (n + 1) \* (n + 2) times
The line `sum = sum + b[i][k] * c[k][j]` takes $(n + 1)^3$ times
The line `a[i][j] = sum;` takes $(n+1)^2$ times
$$T(n) = n^3$$
**c.** Transposition
The first loop takes n + 1 times
The second loop takes $\Large{\frac{(n + 1) * (n + 1)}{2}}$
$$T(n) = \frac{(n + 1)^{2}}{2} = n ^ 2$$

#### Prob 3:
The complexity of the function is given mainly by the for loop, which takes n + 1 times.
$$T(n) = n$$
#### Prob 4:
**a.**
Let $c = 8$, $n_{0}= 1$
Substitute $n = 2$ into the left side: $4*2^2 + 7*2 + 1 = 31$
Substitute c and $n = 2$ to the right side: $8 * 4 = 32$
→ There exist a positive value of c and $n_0$ such that $f(n) < cg(n)$ when $n \geq n_0$ 

**b.**
Let $c = 1$, $n_{0}= 1$
Substitute $n= 4$ into the left side: $4^{2}- 3*4 + 1 = 5$
Substitute c and $n = 2$ to the right side: $1 * 4 = 4$ 
→ There exist a positive value of c and $n_0$ such that $f(n) > cg(n)$ when $n \geq n_0$

**c.**
