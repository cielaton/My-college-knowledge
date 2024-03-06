A **set** is simply a collection of objects (sometimes referred to as elements or members).  For ex:
$$A = \{1, 2, 3, 4\}$$
If a set is a large finite set or an infinite set, we can describe it by listing a property necessary for membership. For ex:
$$B = \{x\;|\; x \; is \; a \;positive,\;even \; interger\}$$
This is called **set-builder notation**

> The elements of a set are not necessary to be of the same type.

---

Two sets X and Y are **equal**, and we write X = Y if X and Y have the same elements. To put in another way, X = Y if:
- For every x, if $x \in X$, then $x\in Y$
- For every x, if $x \in Y$, then $x\in X$

---

If every element of X is an element of Y, we say that X is a **subset** of Y and write $X\subseteq Y$. In other words, X is a subset of Y if for every x, if $x\in X$, then $x\in Y$

>[!note]
>- Any set is a subset of itself.
>- The empty set is a subset of every set.

---

If X is a subset of Y and X does not equal Y, we say that X is a proper subset of Y and write $X\subset Y$.

--- 

The set of all subsets (proper or not) of a set X, denoted $\mathcal{P}(X)$, is called the **power set** of X.

Ex: 
If $A = \{a, b, c\}$, the members of $\mathcal{P}(A)$ are 
$$\emptyset, \{a\}, \{b\}, \{c\}, \{a, b\}, \{a, c\},\{b, c\}, \{a, b, c\}$$ 

--- 

The set
$$X \;\cap \; Y = \{x \; | \; x \in X \; or \; x\in Y\}$$
is called the **union** of X and Y.

The set
$$X \; \cap \; Y = \{x \; | \; x \in X \; and \; x\in Y \}$$
is called the **intersection** of X and Y.

The set
$$X - Y = \{x \; | \; x \in X \; and \; x \notin Y\}$$
is called the **difference** (or **relative complement**). 

> The set **R** - **Q**, called the set of **irrational numbers**, consist of all real numbers that are not rational.

--- 

We call a set $\mathcal{S}$, whose elements are sets, a **collection of sets** or a **family of sets**.

---

Sets X and Y are **disjoint** if  $X \; \cap \; Y = \emptyset$.
A collection of sets $\mathcal{S}$ is said to be **pairwise disjoint** if, whenever X and Y are distinct sets in $\mathcal{S}$, X and Y are disjoint.

--- 

When all the sets are subsets of a set $\mathcal{U}$, this set $\mathcal{U}$ is called a **universal set** or a **universe**.
> The set $\mathcal{U}$ must be explicitly given or inferred from the context.

Given a universal set $\mathcal{U}$ and a subset X of $\mathcal{U}$, the set $U - X$ is called the **complement** of X and is written $\overline{X}$ 

---

**Venn diagram** provide pictorial views of sets.
Ex 
![[Pasted image 20230402193636.png|center]]

--- 

![[Pasted image 20230402194135.png]]

--- 

We define the union of a collection of sets $\mathcal{S}$ to be those elements x belonging to at least one set X in $\mathcal{S}$. Formally,
$$\cup \; \mathcal {S} = \{x \; | \; x \in X \; for \; some \; X \in\mathcal{S}\}$$
Similarly, we define the intersection of a collection of sets $\mathcal{S}$ to be those elements x belonging to every set X in $\mathcal{S}$. Formally, 
$$\cap\;\mathcal{S} = \{x \;| \; x \in X \; for \; all \; X \in \mathcal{S}\}$$

--- 

A partition of a set X divides X into nonoverlapping subsets. More formally, a collection $\mathcal{S}$ of nonempty subsets of X is said to be a **partition** of the set X if every element in X belongs to exactly one member of $\mathcal{S}$.

Ex
Since each element of $X = \{1,2,3,4,5,6,7,8\}$ is in exactly one member of $S = \{\{1,4,5\}, \{2, 6\}, \{3\}, \{7, 8\}\}$, $\mathcal{S}$ is a partition of X.

--- 

We call $X \times Y$ the **Cartesian product** of X and Y.

Ex:
If $X = \{1,2,3\}$ and $Y = \{a, b\}$, then
	$X \times Y = \{(1, a), (1,b), (2, a),(2,b),(3,a),(3,b)\}$ 
	$Y \times Y = \{(a,a), (a,b), (b,a), (b,b)\}$
