## **`Distributions — Questions to consider (from the PDF)`** :contentReference[oaicite:0]{index=0}

*(These questions appear on pages 4–7 of the “6. Distributions” deck, then additional “why/how/classify” questions appear in your screenshots.)* :contentReference[oaicite:1]{index=1}

---

## **`Block A — distribution vs probability measure`**

### **`Question 01: Essentially, what is a probability distribution?`**

Essentially, a probability distribution is a **rule that tells how probability mass is spread over possible values**.

Formally, for a real-valued random variable
$$
X:\Omega\to\mathbb R,
$$
its distribution is the probability measure on $\mathbb R$ defined by
$$
P_X(B)=P(X\in B), \qquad B\in\mathcal B(\mathbb R).
$$

So the “distribution of $X$” is not the function $X$ itself, but the induced law $P_X$ describing the probabilities of all value-sets $B$.

---

### **`Question 02: What is a probability measure?`**

A probability measure is a measure with total mass $1$.

Given a measurable space $(S,\mathcal A)$, a map
$$
\mu:\mathcal A\to[0,1]
$$
is a probability measure if:

1. **Normalization**
$$
\mu(S)=1.
$$

2. **Countable additivity**
for disjoint $A_1,A_2,\dots\in\mathcal A$,
$$
\mu\!\left(\bigcup_{n=1}^\infty A_n\right)=\sum_{n=1}^\infty \mu(A_n).
$$

(Nonnegativity is implicit from codomain $[0,1]$.)

---

### **`Question 03: Are those measures related? If so, how?`**

Yes — a distribution **is** a probability measure, but on a *value space* rather than on $\Omega$.

- The “original” probability measure is
$$
P:\mathcal F\to[0,1] \quad \text{on } (\Omega,\mathcal F).
$$

- The distribution is a new probability measure
$$
P_X:\mathcal B(\mathbb R)\to[0,1] \quad \text{on } (\mathbb R,\mathcal B(\mathbb R)).
$$

They are linked by the random variable $X$:
$$
P_X(B)=P(X\in B)=P\big(X^{-1}(B)\big).
$$

So the random variable acts as a “bridge” between the two measurable spaces.

---

### **`Question 04: Any way we can transfer from one to the other?`**

Yes — the transfer is done by **pushforward measures**.

Given a measurable function
$$
X:(\Omega,\mathcal F)\to(\mathbb R,\mathcal B(\mathbb R)),
$$
the pushforward of $P$ through $X$ is defined by
$$
P_X = P\circ X^{-1},
$$
meaning
$$
P_X(B)=P(X^{-1}(B)).
$$

This is exactly the “distribution of $X$”.

And if you want to compute expectations using the distribution:
$$
\mathbb E[g(X)] = \int_\Omega g(X(\omega))\,dP(\omega)
= \int_{\mathbb R} g(x)\,dP_X(x).
$$

This is the practical “transfer” you use all the time.

---

## **`Block B — why specific distributions, how to choose, what to share`**

### **`Question 05: Why do we care about specific distributions?`**

Because some distributions are:
- **canonical** models for common mechanisms (counting, waiting times, sums of noise),
- **tractable** (closed-form CDF/PDF/CF/MGF),
- **stable** under operations we actually do (sums, scaling, conditioning, limits),
- and often appear as **universal limits** (e.g. Normal via CLT).

So knowing “named” distributions gives you a toolbox: model + compute + infer.

---

### **`Question 06: How to pick the appropriate distribution for the problem?`**

A good way is to match the **mechanism + support + invariances**:

- **Support**
  - $x\in\{0,1\}$ → Bernoulli
  - counts $k\in\mathbb N$ → Binomial/Poisson
  - $x\ge 0$ waiting times → Exponential/Gamma
  - real-valued noise → Normal / Student-$t$

- **Mechanism**
  - independent trials → Binomial
  - rare independent events in time/space → Poisson
  - memoryless waiting time → Exponential
  - sum of many small independent effects → Normal (CLT)

- **Tail behavior / robustness**
  - heavy tails / outliers → Student-$t$, Pareto, etc.

You’re basically choosing a distribution whose **assumptions match your experiment**.

---

### **`Question 07: What common properties we’d like distributions to share?`**

We like distributions that behave nicely under “standard moves”:

- **Existence of moments** (mean/variance finite when we need them)
$$
\mathbb E[|X|] < \infty,\qquad \mathbb E[X^2]<\infty.
$$

- **Identifiability / uniqueness** via transforms (CF/MGF)

- **Closure properties**
  - sums of independent RVs stay in the family (or close)
  - conditioning/marginalization stays manageable

- **Parameterization** by a small set of meaningful parameters (location/scale/shape)

These “nice” properties are exactly why families (like exponential families) matter.

---

### **`Question 08: Any ideas for the path to take?`**

The deck hints at: instead of treating each distribution as a separate creature, we should **group them into families** with shared structure.

The key idea is:
> find a **common generating mechanism with a few knobs** (parameters) to adjust.

That’s why the PDF moves to:
- **statistical families/models** (page 10: family $\{P_\theta\}_{\theta\in\Theta}$) :contentReference[oaicite:2]{index=2}
- viewing $\Theta$ as a “distribution space” (pages 11–12) :contentReference[oaicite:3]{index=3}
- and then using **statistics** as a way to compress data while preserving parameter information (page 14) :contentReference[oaicite:4]{index=4}

---

## **`Block C — derive, classify, overlap, and “math screws us”`**

### **`Question 09: So… how to derive the distributions?`**

Main routes:

1. **From mechanisms**
   - counting process → Poisson
   - waiting time / memoryless → Exponential
   - sums of independent noise → Normal

2. **From transformations**
   If $Y=g(X)$, derive $P_Y$ as a pushforward:
   $$
   P_Y(B)=P(Y\in B)=P(X\in g^{-1}(B)).
   $$
   (The deck explicitly recalls “function of a RV” on page 13.) :contentReference[oaicite:5]{index=5}

3. **From optimization principles**
   (Later in the course) maximum entropy under constraints.

4. **From limiting arguments**
   CLT, Poisson limit theorem, etc.

---

### **`Question 10: Any suggestions how to classify them?`**

Common classification axes:

- **Discrete vs continuous vs mixed**
- **Support** (bounded, $\mathbb R$, $\mathbb R_+$, integers, simplex)
- **Tail regime** (light tails vs heavy tails)
- **Moment existence** (finite mean/variance or not)
- **Family structure**
  - parametric family $\{P_\theta\}$
  - exponential family (later in your deck)

This is exactly the point of “collecting distributions” and defining a *statistical family* (page 10). :contentReference[oaicite:6]{index=6}

---

### **`Question 11: Is it possible to avoid overlapping categories?`**

Not really — overlaps are unavoidable because categories are based on different criteria.

Example:
- Normal is continuous, light-tailed, in an exponential family, stable under sums.
- Student-$t$ is continuous, heavier-tailed, also parameterized similarly, sometimes close to Normal.

A single distribution can belong to many useful “classes”, and that’s a feature, not a bug:
it lets you choose the viewpoint that fits the task (computation, inference, tail risk, etc.).

---

### **`Question 12: Why math screws us so hard sometimes?`**

Because “intuitive” properties fail when you move from finite objects to infinite/measure-theoretic objects.

In this deck, the main traps are:

- **Different probability measures can look similar** but behave very differently in tails or moments.
- **Transformations** can hide information unless you track measurability and pushforwards carefully.
- **Some quantities do not exist** (moments can diverge), so “mean/variance thinking” breaks.

That’s exactly why the deck emphasizes:
- using the “right language” (measures, pushforward, families),
- and compressing information via statistics (pages 14–20). :contentReference[oaicite:7]{index=7}
