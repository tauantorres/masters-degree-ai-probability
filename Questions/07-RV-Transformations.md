## **`Random Variable Transformations — guiding questions`**

---

## **`Block I — why Random Variables and transformations exist`**

### **`Question 01: Why did we need Random Variables?`**

Random Variables were introduced to convert abstract outcomes
$$
\omega \in \Omega
$$
into numerical objects that can be:
- compared,
- averaged,
- transformed,
- and integrated.

Formally, a Random Variable is a measurable function
$$
X:\Omega \to \mathbb R.
$$

This allows us to move from set-based probability
$$
P(A)
$$
to numerical quantities such as
$$
\mathbb E[X], \quad \operatorname{Var}(X), \quad P(X\le x),
$$
which are the objects we actually compute and interpret.

---

### **`Question 02: What’s the point of defining yet another Random Variable as a function?`**

Because many quantities of interest are **functions of existing variables**.

Given a Random Variable $X$ and a measurable function $g$, we define
$$
Y = g(X).
$$

This lets us:
- model derived quantities (energy, distance, cost, log-returns),
- reuse existing distributions without rebuilding probability spaces,
- study how randomness propagates through transformations.

Importantly, $Y$ lives on the **same probability space**, but has a **new distribution**.

---

### **`Question 03: Any properties preserved after such transfiguration?`**

Yes — several fundamental structures are preserved:

- **Measurability**:  
If $X$ is measurable and $g$ is measurable, then $Y=g(X)$ is measurable.

- **Probability mass conservation**:  
Probability is not created or destroyed, only rearranged:
$$
P_Y(B) = P_X(g^{-1}(B)).
$$

- **Expectation structure**:  
For suitable test functions $h$,
$$
\mathbb E[h(Y)] = \mathbb E[h(g(X))].
$$

So transformations change *where* mass lives, not *how much* there is.

---

### **`Question 04: Were we indeed conscious about the whole thing?`**

Yes — the entire construction is deliberately measure-theoretic.

The distribution of $Y=g(X)$ is defined as a **pushforward measure**:
$$
P_Y = g_\# P_X,
$$
meaning
$$
P_Y(B) = P_X(g^{-1}(B)).
$$

This guarantees:
- mathematical consistency,
- compatibility with integration,
- and invariance under equivalent representations.

Nothing ad-hoc is happening — it is all built into the framework.

---

## **`Block II — values, transformations, and multivariate extensions`**

### **`Question 05: Which values can Random Variables take?`**

In principle, a Random Variable can take values in **any measurable space**.

In this course, we mostly consider:
$$
X:\Omega \to \mathbb R,
$$
but the same ideas apply to:
- vectors in $\mathbb R^n$,
- discrete spaces,
- function spaces.

The only requirement is **measurability**, not continuity or smoothness.

---

### **`Question 06: What about the transformations?`**

Transformations are simply **measurable maps** between value spaces.

In the univariate case:
$$
Y = g(X), \qquad g:\mathbb R \to \mathbb R.
$$

In the multivariate case:
$$
Y = g(X_1,\dots,X_n).
$$

All transformation results are consequences of one principle:
$$
P_Y = g_\# P_X.
$$

So instead of transforming densities directly, we transform **measures**.

---

### **`Question 07: Any obvious way to generalize for more variables?`**

Yes — by working with **joint distributions**.

For a random vector
$$
X=(X_1,\dots,X_n):\Omega\to\mathbb R^n,
$$
and a measurable map
$$
g:\mathbb R^n \to \mathbb R^m,
$$
we define
$$
Y = g(X),
$$
and again
$$
P_Y = g_\# P_X.
$$

The theory remains unchanged — only the dimension increases.

---

### **`Question 08: What’s cool about linear multivariate maps?`**

Linear maps are special because they:
- preserve Gaussianity,
- interact cleanly with moments,
- are easy to invert or analyze via matrices.

If
$$
Y = AX + b,
$$
then expectations and covariances transform as:
$$
\mathbb E[Y] = A\mathbb E[X] + b,
\qquad
\operatorname{Cov}(Y) = A\,\operatorname{Cov}(X)\,A^\top.
$$

This makes linear maps central in statistics, signal processing, and ML.

---

## **`Block III — test functions, integration, and identification`**

### **`Question 09: Do some of these transformations ring a bell?`**

Yes — they are the same objects used in **integration theory**.

Expressions like
$$
\mathbb E[h(Y)] = \int h(y)\,dP_Y(y)
$$
are exactly integrals of test functions against measures.

This is the same structure used in:
- Fourier transforms,
- Laplace transforms,
- weak convergence.

---

### **`Question 10: Are the theorems we’ve seen useful for derivations?`**

Very much so.

The **fundamental transformation theorem** states that for bounded measurable $h$:
$$
\int h(Y)\,dP = \int h(g(x))\,dP_X(x)
= \int h(y)\,dP_Y(y).
$$

This is the engine behind:
- distribution derivations,
- change-of-variables formulas,
- identification of laws.

---

### **`Question 11: Those test functions remind of integration-related stuff, don’t they?`**

Exactly.

Test functions act as **probes**:
- they “scan” a distribution,
- extract specific information,
- and determine convergence or equality of measures.

Choosing different classes of test functions gives different notions of convergence and equivalence.

---

### **`Question 12: What was very useful for characterizing a distribution before?`**

Characteristic functions.

They are expectations of special test functions:
$$
\varphi_X(t) = \mathbb E[e^{itX}].
$$

Because:
- they uniquely identify distributions,
- always exist,
- behave well under limits,

they are a powerful instance of the general “test function” philosophy.

---

### **`Final takeaway`**

Random Variable transformations are not about formulas —
they are about **moving probability mass through measurable maps**.

Once you understand:
$$
P_Y = g_\# P_X
$$
everything else is just a special case.
