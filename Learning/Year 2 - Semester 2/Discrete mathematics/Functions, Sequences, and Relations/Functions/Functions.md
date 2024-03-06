>[!note]
>Let $X$ and $Y$ be sets. A *function f* from $X$ to $Y$ is a subset of the Cartesian product $X \times Y$ having the property that for each $x \in X$, there is exactly one $y\in Y$ with $(x, y) \in f$. We sometimes denote a function $f$ from $X$ to $Y$ as $f: X \rightarrow Y$.
>
The set $X$ is called the *domain of f* and the set $Y$ is called the *codomain of f*. The set
$$\{y \; | \;(x,y)\in f\}$$
is called the *range of f*.

Ex:
The set $f=\{(1,a),(2,b),(3,a)\}$ is a function from $X = \{1,2,3\}$ to $Y = \{a, b, c\}$.
We can demonstrate this relationship using an **arrow diagram**:

![[Pasted image 20230404173628.png]]


--- 

>[!note]
>If x is an integer and y is a positive integer, we define x **mod** y to be the remainder when x is divided by y

---

>[!note]
>The *floor* of $x$, denoted $\lfloor x \rfloor$, is the greatest integer less than or equal to $x$. The *ceiling* of $x$, denoted $\lceil x \rceil$, is the least interger greater than or equal to x.

--- 

>[!note]
>A function $f$ from $X$ to $Y$ is said to be *one-to-one* (or *injective*) if for all $x_1, x_2 \in X$, if $f(x_1) = f(x_2)$ then $x_1 = x_2$

---

>[!note]
>A function $f$ from $X$ to $Y$ is said to be *onto* $Y$ (or *surjective*) if for every $y \in Y$, there exists $x \in X$ such that $f(x) = y$

---

>[!note]
>A function that is both one-to-one and onto is called a *bijection*

---

>[!note]
>Let $g$ be a function from $X$ to $Y$ and let $f$ be a function from $Y$ to $Z$. The *composition of f with g*, denoted $f \circ g$, is the function
>$$(f \circ g) (x) = f(g(x))$$

Ex:
![[Pasted image 20230404180400.png]]

---

>[!note]
>A function from $X \times X$ to $X$ is called a *binary operator* on $X$.

Ex:
Let $X = \{1, 2, ...\}$. If we define $f(x, y) = x + y$, where $x,y \in X$, then $f$ is a binary operator on $X$.

>[!note]
>A function from $X$ to $X$ is called a *unary operator* on $X$.

Ex:
Let $U$ be a universal set. If we define $f(X) = \overline {X}$, where $X \in \mathcal{P}(U)$, then $f$ is a unary operator on $X$.
