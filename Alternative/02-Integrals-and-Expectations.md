# `02. Integrals and Expectation`:

1. Indicator functions.
2. Simple functions.
3. Measurable functions.
4. Lebesgue integral and its properties. 
5. L^p spaces. 
6. Integration with respect to a kernel. 
7. Expectation as a functional (discrete and continuous cases). 
8. Connection with distribution moments.

---

### **`Topic 2.1` Indicator Functions**:

An **Indicator Function** (or Characteristic Function, $\mathbb{I}_A$) is the **simplest possible measurable function**. It only answers a **yes/no** question: ***"Did the outcome ω belong to the event A?"***

*   **Definition**: $\mathbb{I}_A : \Omega \to \{0, 1\}$ defined as:
$$
\mathbb{I}_A(\omega) = \begin{cases} 1 & \text{if } \omega \in A \\ 0 & \text{if } \omega \notin A \end{cases}
$$
*   **Use in Probability**: The expected value of an indicator function gives the probability of the event: $E[\mathbb{I}_A] = P(A)$.

---

### **`Topic 2.2` Simple Functions**:

A **Simple Function** is a function that takes on only a finite number of distinct values. It is a linear combination of indicator functions.
In another words, is basically a “categorizer”: it splits outcomes into finitely many buckets, and assigns a constant value to each bucket.

*   **Definition**: A function $s: \Omega \to \mathbb{R}$ is simple if $s(\omega) = \sum_{i=1}^{n} a_i \mathbb{I}_{A_i}(\omega)$, where $a_i \in \mathbb{R}$ are the finite values taken by the function, and $A_i$ are disjoint measurable sets.
*   **Importance**: Simple functions are the bridge used to define the Lebesgue integral for more complex functions.

---

### **`Topic 2.3` Measurable Functions**:

A **Measurable Function** is a function for which we can consistently define integrals and probabilities. It maps a measurable space $(\Omega, \mathcal{F})$ to another measurable space $(Y, \mathcal{Y})$.

*   **Definition**: A function $X: \Omega \to Y$ is measurable if the pre-image of every measurable set in $Y$ is a measurable set in $\Omega$.
    $$\forall B \in \mathcal{Y}, \quad X^{-1}(B) = \{\omega \in \Omega : X(\omega) \in B\} \in \mathcal{F}$$
*   **In Probability**: A **random variable** is formally defined as a *measurable function* from a probability space to the real numbers ($\mathbb{R}$).

---

### **`Topic 2.4` Lebesgue Integral and its Properties**:

The **Lebesgue Integral** is a generalized and more powerful definition of integration than the standard Riemann integral taught in calculus. It integrates over the *range* of the function rather than the domain.

*   **Steps (Informal)**:
    1. Define the integral for indicator functions.
    2. Define the integral for simple functions using a weighted sum of probabilities.
    3. Extend to all non-negative measurable functions using the limit of simple functions.
    4. Extend to general measurable functions by splitting them into positive and negative parts ($f^+ - f^-$).
*   **Properties**: Linearity ($E[aX+bY] = aE[X]+bE[Y]$), Monotone Convergence Theorem (MCT), Dominated Convergence Theorem (DCT), and Fatou's Lemma.

---

### **`Topic 2.5` $L^p$ Spaces**:

The $L^p$ spaces are collections of functions for which a certain norm is finite. They are function spaces crucial for functional analysis and probability.

*   **Definition**: $L^p(\Omega, \mathcal{F}, P)$ is the set of all measurable functions $X$ such that the $p$-th moment of $|X|$ is finite:
    $$E[|X|^p] = \int_{\Omega} |X(\omega)|^p dP(\omega) < \infty$$
*   **Key Spaces**:
    *   $L^1$: Functions with finite expectation ($E[|X|] < \infty$).
    *   $L^2$: Functions with finite variance ($E[X^2] < \infty$).
    *   $L^\infty$: Bounded functions.
*   **Relevance**: Convergence in $L^p$ spaces relates directly to the "Modes of Convergence" (e.g., $L^2$ convergence is Mean Square convergence).

---

### **`Topic 2.6` Integration with Respect to a Kernel**:

A **Markov Kernel** (or transition kernel) is a function $K(x, A)$ that acts like a conditional probability measure. Integration with respect to a kernel is key to describing how probability distributions evolve over time (e.g., in Markov Chains).

*   **Interpretation**: $K(x, A)$ is the probability of transitioning from state $x$ into a set of states $A$.
*   **Evolution of Measures**: If $\mu$ is the starting distribution, the next distribution $\nu$ is found by integrating $\mu$ with respect to the kernel $K$:
    $$\nu(A) = \int K(x, A) d\mu(x)$$

---

### **`Topic 2.7` Expectation as a Functional**:

Expectation is a *functional* (a function that takes a function as input). It formally translates a random variable into a single number (the average value).

| Case | Notation | Formula |
| :--- | :--- | :--- |
| **Discrete RV** | $E[X]$ | $\sum_{i} x_i P(X = x_i)$ |
| **Continuous RV** | $E[X]$ | $\int_{-\infty}^{\infty} x f_X(x) dx$ |
| **Measure Theory** | $E[X]$ | $\int_{\Omega} X(\omega) dP(\omega)$ (Lebesgue Integral) |

---

### **`Topic 2.8` Connection with Distribution Moments**:

The integral definition of expectation is used to define all moments of a distribution. A **moment** is just the expected value of some function of the random variable.

*   **$n$-th Raw Moment**: $E[X^n] = \int X(\omega)^n dP(\omega)$.
*   **Variance**: $Var(X) = E[X^2] - (E[X])^2$.
*   **Definition**: The integral provides the rigorous foundation for the formulas for mean, variance, skewness, and kurtosis.
