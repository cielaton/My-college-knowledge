Let $P(x)$ be a statement involving the variable $x$ and let $D$ be a set. We call $P$ a *propositional function* or *predicate* (with respect to $D$) if for each $x\in D, P(x)$ is a proposition. We call $D$ is the *domain of discourse* of $P$.

--- 

Let $P$ be a propositional function with domain of discourse $D$. The statement
$$\mathrm{for \; every \;} x, P(x)$$ is said to be a *universally quantified statement*. The symbol $\forall$  means "for every". Thus, the statement

$$\mathrm{for \; every \;} x, P(x)$$
may be written as
$$\forall x\;P(x)$$
The symbol $\forall$ is called a *universal quantifier*.

---

Let $P$ be a propositional function with domain of discourse $D$. The statement
$$\mathrm{there\;exists\;}x, P(x)$$
is said to be an *existentially quantified statement*. The symbol $\exists$ means "there exists". Thus, the above statement can be written as
$$\exists x P(x)$$

---

### Rules of Interference for Quantified Statements
Suppose that $\forall x P(x)$ is true. By definition, $P(x)$ is true for every $x$ in $D$, the domain of discourse. In particular, if $d$ is in $D$, then $P(d)$ is true, We have shown that the argument
$$\frac{\forall x P(x)}{\therefore P(d) \;if\; f \in D}$$
This rule of interference is called **universal instantiation**. 

<center><em> Rules of Interference for Quantified Statements</em></center>
![[Pasted image 20230404165549.png]]
