## **`Information & Entropy — guiding questions`**

*(Slide “Questions to consider”, pages 4–7)*

---

### **`Question 01: Measure theory aside, what is studied by Probability Theory?`**

Even if we already know the formal setup
$$
(\Omega,\mathcal F,P),
$$
probability theory is not “only about measures”.

What we *really* study is **uncertainty** and how it behaves when we:
- observe events,
- combine experiments,
- compress outcomes into random variables,
- and pass through transformations (sums, limits, conditioning).

So, informally:
> Probability theory studies **uncertain information** about the world,
> and builds tools to **quantify**, **propagate**, and **update** it.

This naturally connects probability to **information theory**, because “uncertainty” is exactly what information measures try to quantify.

---

### **`Question 02: How can these questions be approached?`**

There are (at least) two complementary approaches:

1. **Probabilistic / measure-theoretic approach**  
We describe uncertainty by a probability measure and compute quantities like
$$
P(A),\quad \mathbb E[X],\quad \operatorname{Var}(X),
$$
and study convergence, limit theorems, etc.

2. **Informational approach (Shannon’s viewpoint)**  
We treat outcomes/events as “messages” and ask:
- how *surprising* is an event?
- how much *uncertainty* is removed when we learn the outcome?

This approach builds **numerical measures of uncertainty**, leading to:
- information content $I(p)$,
- entropy $H(X)$,
- mutual information, KL divergence, etc. (later topics).

---

### **`Question 03: Are the objects we define of informational nature?`**

Yes — many classical probability objects can be read as **information objects**:

- An event $A$ with probability $P(A)=p$ can be viewed as a “message” that happens with likelihood $p$.
- A random variable $X$ is a mechanism that produces symbols/outcomes with probabilities.
- A $\sigma$-algebra $\mathcal F$ represents **what questions we are able to ask** (what can be distinguished / observed).

So even when we speak in measure language, we are often implicitly studying:
$$
\text{uncertainty} \quad \leftrightarrow \quad \text{information}.
$$

This is why entropy fits naturally into probability theory.

---

### **`Question 04: What is information, exactly?`**

Shannon’s key move is to define “information” **quantitatively** in terms of probability.

If an event has probability $p$, its **information content** should satisfy:
- very likely events carry little information,
- rare events carry lots of information,
- independent events add their information.

This leads to the logarithmic form:
$$
I(p) = -k \log_b(p),
\qquad p\in(0,1].
$$

Here:
- $b$ is the base (often $2$ for bits, or $e$ for nats),
- $k>0$ is a scaling constant.

In particular:
- if $p=1$ (certain event), then
$$
I(1)=0,
$$
meaning a sure thing gives no new information.

This is the building block for **entropy**, which is the *average information* of a random variable.

---

### **`Big picture takeaway`**

Probability theory can be seen as:
- **measures and integrals** (formal foundation),
but also as:
- **uncertainty and information** (meaning + interpretation).

Entropy is the bridge:
$$
\text{probabilities} \longrightarrow \text{information content} \longrightarrow \text{entropy}.
$$

## **`Entropy & distributions — guiding questions (I)`**

---

### **`Question 01: What distributions do we know, and why are they cool (or not)?`**

Some of the most common distributions we know are:

- **Discrete**: Bernoulli, Binomial, Poisson  
- **Continuous**: Uniform, Exponential, Normal, Pareto, Cauchy

They are *cool* because:
- many of them arise naturally from simple assumptions,
- they are mathematically tractable,
- they appear as limits of more complicated models.

For example:
- the **Poisson** distribution models rare independent events,
- the **Exponential** distribution appears in waiting-time problems,
- the **Normal** distribution emerges from aggregation of randomness.

They are *not cool* when:
- moments do not exist (e.g. Cauchy),
- tails dominate behavior and break intuition,
- analytical tools fail or diverge.

So distributions are powerful models, but they must be treated with care.

---

### **`Question 02: Any way to derive a distribution other than based on calculus?`**

Yes — distributions can be derived using **principle-based arguments**, not only calculus.

Examples include:
- **Symmetry arguments** (uniform distributions),
- **Limit theorems** (Normal via CLT),
- **Independence and memorylessness** (Exponential),
- **Maximum entropy principle** (key idea here).

The maximum entropy principle says:
> *Among all distributions satisfying given constraints, choose the one with the largest entropy.*

This avoids detailed microscopic modeling and relies only on:
- what we know,
- and nothing we don’t.

---

### **`Question 03: What physics-inspired ways of optimization do you recall?`**

Several optimization ideas come directly from physics:

- **Energy minimization**  
Systems evolve toward states minimizing free energy.

- **Equilibrium distributions**  
Boltzmann–Gibbs distributions arise by maximizing entropy under energy constraints:
$$
p(x) \propto e^{-\beta E(x)}.
$$

- **Variational principles**  
Physical laws often result from optimizing an action functional.

Entropy maximization plays the same role:
- entropy replaces disorder,
- constraints replace conservation laws.

---

### **`Question 04: Why do we care about “normal objects”?`**

Normal (Gaussian) objects are special because:

- they appear as **universal limits**,
- they are stable under addition,
- they are completely characterized by mean and variance.

By the Central Limit Theorem:
$$
\frac{1}{\sqrt n}\sum_{i=1}^n (X_i - \mathbb E[X_i])
\;\longrightarrow\;
\mathcal N(0,\sigma^2),
$$
regardless of the original distribution (under mild assumptions).

This makes normal distributions:
- mathematically convenient,
- empirically ubiquitous,
- central to both probability and statistics.

---

## **`Entropy & information — guiding questions (II)`**

---

### **`Question 01: Is our information content all-encompassing?`**

No. Information content of a single event
$$
I(p) = -\log p
$$
only measures *surprise* of that event.

It does not capture:
- variability across outcomes,
- structure of the distribution,
- typical behavior.

So it is **local**, not global.

---

### **`Question 02: How to look at everything we need at once?`**

To capture global uncertainty, we must **average information content** over all outcomes.

This leads naturally to **entropy**, which aggregates:
- all possible outcomes,
- weighted by their probabilities.

We move from:
$$
\text{information of one event}
$$
to:
$$
\text{information of a whole distribution}.
$$

---

### **`Question 03: What did we do with probabilities to “average” everything?`**

In probability theory, averaging is done using **expectation**:
$$
\mathbb E[X] = \sum_x x\,P(X=x)
\quad\text{or}\quad
\mathbb E[X] = \int x\,dP_X(x).
$$

Expectation compresses randomness into a single representative quantity.

This idea works because probabilities provide the correct weights.

---

### **`Question 04: Can we do the same with information?`**

Yes — entropy is exactly that.

For a discrete random variable $X$ with distribution $p(x)$, entropy is defined as:
$$
H(X) = \mathbb E[I(p(X))]
= -\sum_x p(x)\log p(x).
$$

So entropy is:
- an **expected information content**,
- a measure of **uncertainty**,
- a global descriptor of a distribution.

In one line:
$$
\text{entropy} = \text{average surprise}.
$$

---

### **`Big picture takeaway`**

- Probability weights outcomes,
- information measures surprise,
- entropy averages information.

This makes entropy the natural bridge between **probability**, **optimization**, and **physics**.
