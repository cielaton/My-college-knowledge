Let $S_n$ denote the sum of the first $n$ positive integers:
$$S_n = 1 + 2 + ... + n$$
Suppose that someone claims that 
$$S_n = \frac{n(n+1)}{2} \mathrm{\hspace{20pt} for \; all\;} n \geq 1$$
A sequence of statements is really being made, namely,
$$S_1 = \frac{1(2)}{2} = 1, \hspace{10pt} S_2 = \frac{2(3)}{2} = 3, \hspace{10pt} S_3 = \frac{3(4)}{2} = 6, ...$$

We must show that for all $n$, if equation $n$ is true, then equation $n+1$ is also true. Equation $n$ is
$$S_n = \frac{n(n+1)}{2}$$
Assuming that this equation is true, we must show that equation $n+1$
$$S_{n+1} = \frac{(n+1)(n+2)}{2}$$
is true,

According to definition:
$$S_{n+1} = 1 + 2 +...+n + (n+1) = S_n + (n+1)$$
$$= \frac{n(n+1)}{2} + (n+1)$$
$$= \frac{(n+1)(n+2)}{2}$$
Therefore, assuming that equation $n$ is true, we have proved that equation $n+1$ is true.

>[!note]
>Our proof consisted of two steps:
>- We verified that the statement corresponding to $n= (\text{the least n value})$ was true.
>- We *assumed* that statement $n$ was true, and then *proved* that statement $n+1$ was also true.
>In proving statement $n+1$, we were permitted to make use of statement $n$

---

#### Principle of Mathematical Induction
Suppose that we have a propositional function $S(n)$ whose domain of discourse is the set of positive integers. Suppose that
	$S(1)$ is true;
	for all $n\geq 1$, if $S(n)$ is true, then $S(n+1)$ is true

Then $S(n)$ is true for every positive integer $n$.

---

n *factorial* is defined as
$$n! = \begin{cases}1 & if \; n = 0 \\ n(n-1)(n-2) ...2 \times 1 & if \; n\geq 1  \end{cases}$$
Show that 
$$n! \geq 2^{n-1} \hspace{20pt} \text{for all } n\geq 1$$
##### Basic step (n=1)
This is easily accomplished since $1! = 1 \geq 1 = 2^{1 -1}$

##### Inductive Step
We assume that $n! \geq 2^{n-1}$ is true, we must then prove that $(n+1)! \geq 2^n$ is true.

$$(n+1)! = (n+1)(n!)$$
$$\geq (n+1)2^{n-1}$$
$$\geq 2 \cdot 2^{n-1} \; \text{since } n+1 \geq 2$$ $$= 2^n$$
Therefore, the given statement is true

---

#### Problem-Solving tips
To prove
$$a_1 + a_2 + ... + a_n = F(n) \hspace{10pt} \text{for all } n\geq 1$$
where $F(n)$ is the formula for the sum, first verify the equation for $n = 1 : a_1 = F(1)$ (**Basis step**). 

Now assume that the statement is true for $n$; that is, assume
$$a_1 + a_2+ ... + a_n = F(n)$$
and add $a_{n+1}$ to both sides to get
$$a_1 + a_2 + ... + a_n + a_{n+1} = F(n) + a_{n+1}$$
Finally, show that
$$F(n) + a_{n+1} = F(n+1)$$
