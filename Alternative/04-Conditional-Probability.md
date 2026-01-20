# `04. Conditional Probability and Information`

1. Incomplete information and sub-sigma-algebras. 
2. Bayes’ formula as a ratio of measures. 
3. Prior probability and its update. 
4. Definition of independence.

---

### **`Topic 4.1` Incomplete Information and Sub-$\sigma$-algebras**:

In probability theory, our "information set" is formally represented by a **$\sigma$-algebra ($\mathcal{F}$)**. When we only have *partial* information, we work with a smaller sub $\sigma$ algebra ($\mathcal{G} \subset \mathcal{F}$).

*   **Meaning**: We can only discern events contained within the partitions of $\mathcal{G}$. Events outside of $\mathcal{G}$ are indistinguishable based on our current information.
*   **Example**: In a medical trial, $\mathcal{F}$ could describe the full health record of a patient. $\mathcal{G}$ might only contain the information "Patient took the drug" or "Patient took the placebo." We can't use $\mathcal{G}$ to determine the patient's cholesterol level.

---

### **`Topic 4.2` Bayes' Formula as a Ratio of Measures**:

**Bayes' Formula** is the foundational rule for updating our belief about an event ($A$) when we receive new information that another event ($B$) has occurred. It formally defines the **conditional probability** $P(A|B)$.

$$P(A|B) = \frac{P(B|A) P(A)}{P(B)}$$

#### **The Denominator: Total Probability Rule**
$P(B)$ is often found using the Law of Total Probability, which acts as a normalizing constant:
$$P(B) = P(B|A)P(A) + P(B|A^c)P(A^c)$$

#### **Terminology Table**

| Term      | Formal Name               | Meaning |
|-----------|---------------------------|---------|
| $P(A)$    | **Prior Probability**     | Our initial belief about A before observing B. |
| $P(B\|A)$ | **Likelihood**            | How likely B is, given A is true. |
| $P(B)$    | **Evidence**              | The total probability of observing B. |
| $P(A\|B)$ | **Posterior Probability** | Our *updated* belief about A *after* observing B. |

---

### **`Topic 4.3` Prior Probability and its Update**:

This topic is the practical application of Bayes' Formula in sequential reasoning: Statistics is often an iterative process of belief revision.

1.  **Start with a Prior ($P_{prior}$)**: This is your initial belief or baseline knowledge (e.g., $P(\text{Disease}) = 0.01$).
2.  **Gather Evidence ($E$)**: You conduct a test or observe data (e.g., test result is positive).
3.  **Calculate the Likelihood ($P(E|\text{State})$)**: How often does the test correctly identify the state?
4.  **Compute the Posterior ($P_{posterior}$)**: Use Bayes' rule to formally calculate the new, updated probability (e.g., $P(\text{Disease}|\text{Positive Test})$).

> **Key Concept**: The **posterior probability** from one experiment becomes the **prior probability** for the next experiment.

---

### **`Topic 4.4` Definition of Independence**:

**Independence** is the absence of a relationship between events or variables. Knowing the outcome of one provides zero information about the other.

#### A. Events
Two events $A$ and $B$ are independent if any of the following equivalent conditions hold:

1.  $$P(A \cap B) = P(A)P(B)$$
2.  $$P(A|B) = P(A) \quad (\text{if } P(B)>0)$$
3.  $$P(B|A) = P(B) \quad (\text{if } P(A)>0)$$

#### B. Random Variables
Random variables $X$ and $Y$ are independent if their joint PDF/PMF factors entirely into their marginals:

$$f_{X,Y}(x, y) = f_X(x)f_Y(y)$$

**Difference from Conditional Probability**:
*   **Conditional Probability**: Assumes dependence and calculates the revised probability *given* information.
*   **Independence**: Assumes no information linkage, so conditioning does not change the initial probability.
