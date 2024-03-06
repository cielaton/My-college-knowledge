#### Proof by Contradiction
A **proof by contradiction** establishes $p \rightarrow q$ by assuming that the hypothesis $p$ is true and that the conclusion $q$ is false and then, using $p$ and $\neg q$ as well as other axioms, definitions, previously derived theorems and rules of inference, drives a **contradiction**.

A proof by contradiction is sometimes called an **indirect proof** since to establish $p \rightarrow q$ using proof by contradiction, we follow a direct route: We derive $r \wedge \neg r$ and then conclude that $q$ is true.

Ex: 
Give a proof by contradiction of the following statement:
$$\mathrm{For \; every \;} n \in \mathbb{Z}, \mathrm{\; if \;} n^2 \mathrm{ \; is \; even, \; then \;} n \mathrm{\; is \; even}$$
We assume the hypothesis $n^2$ is even and that the conclusion is false if $n$ is odd. Since $n$ is odd, there exists an integer $k$ such that $n = 2k +1$. Now
$$n^2 = (2k + 1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1$$

Thus, $n^2$ is odd, which contradicts the hypothesis $n^2$ is even.

---

#### Proof by Contrapositive
suppose that we give a proof by contradiction of $p \rightarrow q$ in which we deduce $\neg p$. In effect, we have proved $\neg q \rightarrow \neg p$.
> Recall that $p \rightarrow q$ and $\neg q \rightarrow \neg p$ are equivalent.

This special case of proof by contradiction is called **proof by contrapositive**.

---

#### Proof by Cases
**Proof by cases** is used when the original hypothesis naturally divides itself into various cases.
For example, the hypothesis "$x$ is a real number" can be divided into cases:
- $x$ is a nonnegative real number
- $x$ is a negative real number

Suppose that the task is to prove $p \rightarrow q$ and that $p$ is equivalent to $p_1 \vee p_2 \vee ... \vee p_n(p_1, ..., p_n) \mathrm{\; are \; the \; cases}$. Instead of proving
$$(p_1 \vee p_2 \vee ... \vee p_n) \rightarrow q$$
We prove
$$(p_1 \rightarrow q) \wedge (p_2 \rightarrow q) \wedge ... \wedge (p_n \rightarrow q)$$

Sometimes the number of cases to prove is finite and not too large, so we can check them all one by one. We call this type of proof **exhaustive proof**.

Ex:
Prove that $2m^2 + 3n^2 = 40$ has no solution in positive integers, that is, that $2m^2 + 3n^2 = 40$ is false for all positive integers $m$ and $n$.

If $2m^2 + 3n^2 = 40$, we must have $2m^2 \leq 40$. Thus, $m^2 \leq 20$ and $m \leq 4$. Similarly, we must have $3n^2 \leq 40$ Thus $n^2 \leq \frac{40}{3}$ and $n\leq 3$. Therefore, it suffices to check the cases $m = 1, 2, 3, 4$ and $n = 1, 2, 3$.

The table gives the value of $2m^2 + 3n^2$ for $m$ and $n$

![[Pasted image 20230405180751.png]]

Since $2m^2 + 3n^2 \neq 40$ for $m = 1, 2, 3, 4$ and $n = 1, 2,3$, and $2m^2 + 3n^2  > 40$ for $m > 40$ or $n > 3$, we conclude that $2m^2 + 3n^2 = 40$ has no solution in positive integers.

--- 

#### Proofs of Equivalence
Some theorems are of the form $p$ if and only if $q$. Such theorems are proved by using the equivalence
$$p \leftrightarrow q \equiv (p \rightarrow q) \wedge (q \rightarrow p); $$
that is, to prove "$p$ if and only if $q$", prove "if $p$ then $q$" and "if $q$ then $p$".

Ex: 
prove that for every integer $n$, $n$ is odd if and only if $n - 1$ is even.

- We first prove that *if $n$ is odd, then $n -1$ is even*. If $n$ is odd, then $n = 2k +1$ for some integer $k$. Now $n - 1 = (2k+1) - 1 = 2k$. Therefore, $n-1$ is even.
- Next, we prove *if $n -1$ is even, then $n$ is odd*. If $n - 1$ is even, then $n - 1 = 2k$ for some integer $k$. Now $n = 2k  + 1$. Therefore, $n$ is odd.

--- 

#### Existence Proofs
A proof of 
$$\exists x P(x)$$ is called an **existence proof**.

Ex:
Let $a$ and $b$ be real numbers, with $a < b$. Prove that there exists a real number $x$ satisfying $a < x < b$.

It suffices to find one real number $x$ satisfying $a < x  < b$. The real number 
$$x = \frac{a + b}{2}$$
halfway between $a$ and $b$, surely satisfies $a < x < b$.
