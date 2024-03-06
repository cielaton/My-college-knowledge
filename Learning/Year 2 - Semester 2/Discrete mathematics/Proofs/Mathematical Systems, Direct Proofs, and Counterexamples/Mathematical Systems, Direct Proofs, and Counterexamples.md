A **mathematical system** consists of **axioms, definitions**, and **undefined terms**. 
- Axioms are assumed to be true.
- Definitions are used to create new concepts in terms of existing ones.
- Some terms are not explicitly defined, but rather are implicitly defined by the axioms.

A **theorem** is a proposition that has been proved to be true.
A **lemma** is a theorem that is usually not too interesting in its own right, but useful in proving another theorem.
A **corollary** is a theorem that follows easily from another theorem.

An argument that establishes the truth of a theorem is called a **proof**.

---

#### Direct Proofs
Theorems are often of the form
$$\mathrm{For \; all \;} x_1, x_2....,x_n \mathrm{\; if \;} p(x_1, x_2,...,x_n), \mathrm{\; then \;} q(x_1, x_2,..., x_n).$$
This universally quantified statement is true provided that the conditional proposition
$$\mathrm{if \;} p(x_1, x_2,..., x_n), \mathrm{\; then \;} q(x_1, x_2,...,x_n)$$
is true for all $x_1, x_2, ..., x_n$ in the domain of discourse.

A **direct proof** assumes that $p(x_1, x_2, ..., x_n)$ is true and then, using $p(x_1, x_2, ..., x_n)$ as well as other axioms, definitions, previously derived theorems, and rules of inference, show directly that $p(x_1, x_2, ..., x_n)$ is true.

>An integer *n* is *even* if there exists an integer *k* such that $n = 2k$.
>An integer *n* is *odd* if there exists an integer *k* such that $n = 2k +1$.

---

#### Disproving a Universally Quantified Statement

>To *disprove* $\forall x P(x)$, we simply need to find one member *x* in the domain of discourse that makes $P(x)$ false. Such a value for $x$ is called a *counterexample*.

Ex:
The statement $\forall n \in \mathbb{Z}^+ \; (2^n + 1 \; is \; prime)$ is false. A counterexample is $n = 3$ since $2^3 + 1 =9$, which is not prime.