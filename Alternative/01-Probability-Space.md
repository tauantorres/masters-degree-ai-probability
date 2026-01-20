# `01. Probability Space & Measure Theory`

1. Measure function and its properties. 
2. Measurable spaces. 
3. Absolutely continuous and mixed measures. 
4. Radon–Nikodym derivative. 
5. Kolmogorov axioms. 
6. Sample space. 
7. Event space. 
8. Probability measure. 
9. Joint (product) spaces. 
10. Conditional measure and partial information.

---

### **`Topic 1.1 - 1.2` Measure Function and Measurable Spaces**:

A **Measurable Space** is a pair $(\Omega, \mathcal{F})$ where $\Omega$ is the sample space and $\mathcal{F}$ is a $\sigma$-algebra (a collection of subsets where we can "measure" probability).

*   **Measure Function ($\mu$)**: A function $\mu: \mathcal{F} \to [0, \infty]$ that assigns a "size" to sets.
*   **Properties**:
    1. **Non-negativity**: $\mu(A) \ge 0$ for all $A \in \mathcal{F}$.
    2. **Null empty set**: $\mu(\emptyset) = 0$.
    3. **Countable Additivity**: For disjoint sets $A_1, A_2, \dots$, then $\mu(\cup A_i) = \sum \mu(A_i)$.

---

### **`Topic 1.3 - 1.4` Absolutely Continuous Measures & Radon–Nikodym**:

These concepts explain how one measure (like probability) relates to another (like length/volume).

*   **Absolute Continuity ($\nu \ll \mu$)**: Measure $\nu$ is absolutely continuous with respect to $\mu$ if $\mu(A) = 0$ implies $\nu(A) = 0$. (If $\mu$ sees "nothing," $\nu$ must also see "nothing").
*   **Radon–Nikodym Derivative**: If $\nu \ll \mu$, there exists a measurable function $f$ such that:
    $$\nu(A) = \int_A f d\mu$$
    In probability, if $\nu$ is our distribution and $\mu$ is the Lebesgue measure, then **$f$ is the Probability Density Function (PDF)**.

---

### **`Topic 1.5 - 1.8` The Kolmogorov Framework**:

Probability is defined by the **Probability Triple** $(\Omega, \mathcal{F}, P)$.

| Element | Name | Description |
| :--- | :--- | :--- |
| **$\Omega$** | **Sample Space** | The set of all possible outcomes (e.g., $\{H, T\}$). |
| **$\mathcal{F}$** | **Event Space** | A $\sigma$-algebra of subsets of $\Omega$ that we can assign probabilities to. |
| **$P$** | **Probability Measure** | A measure where the total mass is exactly 1 ($P(\Omega) = 1$). |
| **A** | Subset $A \in \mathcal{F}$ | An outcome (event) or collection of outcomes we can assign a probability to. |

**Kolmogorov Axioms**:
1. $P(A) \ge 0$ for all $A \in \mathcal{F}$.
2. $P(\Omega) = 1$ (Normalization).
3. If $A_1, A_2, \dots$ are disjoint, $P(\cup A_i) = \sum P(A_i)$.

---

### **`Topic 1.9` Joint (Product) Spaces**:

When we observe two experiments simultaneously, we use a **Product Space** $(\Omega_1 \times \Omega_2, \mathcal{F}_1 \otimes \mathcal{F}_2, P_{1,2})$.

*   **Joint Measure**: $P(X \in A, Y \in B)$ describes the probability of pairs of outcomes.
*   **Fubini’s Theorem**: Allows us to compute joint integrals by integrating one variable at a time.

---

### **`Topic 1.10` Conditional Measure and Partial Information**:

**Conditional Probability** $P(A|B)$ is a way to redefine our probability measure when we have "Partial Information" (we know $B$ has occurred).

*   **Formula**: $P(A|B) = \frac{P(A \cap B)}{P(B)}$
*   **Information Theory perspective**: Conditioning on an event $B$ reduces the sample space from $\Omega$ to $B$.
*   **Sub-$\sigma$-algebras**: More advanced conditioning is done with respect to a sub-$\sigma$-algebra $\mathcal{G} \subset \mathcal{F}$, representing the "information available" to us at a certain time.

---

### **Summary of Measure Types**

| Measure Type | Definition | Probability Analog |
| :--- | :--- | :--- |
| **Discrete** | Mass at specific points. | **PMF** (Probability Mass Function) |
| **Absolutely Continuous** | Smoothly spread over a range. | **PDF** (Probability Density Function) |
| **Mixed** | Combination of points and ranges. | A variable that is 0 with prob. 0.5, and $U(0,1)$ otherwise. |
