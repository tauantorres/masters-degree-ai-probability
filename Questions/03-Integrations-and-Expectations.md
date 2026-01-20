## **`Closing questions — probability, measure, expectation`**

---

### **`Question 01: How did we define a probability?`**

To formalize randomness, we introduced a **probability space**, which is a triple
$$
(\Omega,\mathcal F,P).
$$

Here:
- $\Omega$ is the set of all possible outcomes,
- $\mathcal F$ is a $\sigma$-algebra of measurable events,
- $P$ is a function assigning probabilities to events.

Formally, a probability is a map
$$
P:\mathcal F \to [0,1]
$$
satisfying three axioms:

1. **Normalization**
$$
P(\Omega)=1.
$$

2. **Non-negativity**
$$
P(A)\ge 0 \quad \text{for all } A\in\mathcal F.
$$

3. **Countable additivity**
If $A_1,A_2,\dots$ are pairwise disjoint events, then
$$
P\!\left(\bigcup_{n=1}^{\infty} A_n\right)
=
\sum_{n=1}^{\infty} P(A_n).
$$

These axioms ensure that probability behaves consistently even for infinitely many events.

---

### **`Question 02: Is any probability some kind of measure? Why?`**

Yes. Probability is a **special case of a measure**.

A general measure is a function
$$
\mu:\mathcal F \to [0,\infty]
$$
that satisfies:
- $\mu(\varnothing)=0$,
- countable additivity.

A probability $P$ satisfies **all** measure axioms, with one extra condition:
$$
P(\Omega)=1.
$$

So:
- every probability measure **is** a measure,
- not every measure is a probability.

For example, Lebesgue measure on $\mathbb R$ assigns
$$
\mu(\mathbb R)=\infty,
$$
so it cannot be a probability.

---

### **`Question 03: What else would we like to know about our experiments, just to make sure?`**

Knowing probabilities of individual events is often not enough.

What we usually want is a **numerical summary** of outcomes.

To do this, we introduce a **random variable**
$$
X:\Omega \to \mathbb R,
$$
which turns outcomes into numbers.

Once we have $X$, we want to know:

- the **typical value** of the experiment,
- how **spread out** the outcomes are,
- whether averages are even **well-defined**.

This leads naturally to **expectation**, defined as an integral:
$$
\mathbb E[X] = \int_\Omega X(\omega)\,dP(\omega).
$$

However, this only makes sense if
$$
\int_\Omega |X|\,dP < \infty,
$$
otherwise the expectation may not exist.

So expectation forces us to care about **integrability**, not just probabilities.

---

### **`Question 04: How can everything we ran through today be of some help?`**

The key idea of the lecture is that **probability theory is integration theory**.

First, events are turned into functions via **indicator functions**:
$$
\mathbf 1_A(\omega)=
\begin{cases}
1, & \omega\in A, \\
0, & \omega\notin A.
\end{cases}
$$

Then, simple random variables are built as finite sums:
$$
\varphi(\omega)=\sum_{i=1}^n a_i\,\mathbf 1_{A_i}(\omega).
$$

The integral is defined first on indicators,
$$
\int \mathbf 1_A\,dP = P(A),
$$
then extended step by step to general measurable functions.

As a result:
$$
\mathbb E[X] = \int X\,dP
$$
is not a new object — it is just a Lebesgue integral.

Finally, expectations can often be computed using the distribution of $X$:
$$
\mathbb E[g(X)] = \int_{\mathbb R} g(x)\,dP_X(x),
$$
which in concrete cases becomes:
- discrete:
$$
\mathbb E[g(X)] = \sum_i g(x_i)P(X=x_i),
$$
- continuous:
$$
\mathbb E[g(X)] = \int g(x)f_X(x)\,dx.
$$

This framework allows us to handle **discrete, continuous, and mixed models** in exactly the same way.

---

### **`Big picture takeaway`**

Probability is a **measure**,  
expectation is an **integral**,  
and random variables are **measurable functions**.

Once this structure is in place, all calculations follow naturally.
