# `Inequalities and Limit Theorems`

---

### **`Topic 5.1` Convexity & Jensen's Inequality**:

A function $f: \mathbb{R} \to \mathbb{R}$ is **convex** if the line segment between any two points on the graph lies above or on the graph itself. (e.g., $f(x) = x^2$ is convex, $f(x) = \log(x)$ is concave).

#### **Jensen's Inequality**:
This fundamental inequality relates the expected value of a convex function to the convex function of the expected value.

*   **Formula**:
    $$E[f(X)] \ge f(E[X]) \quad (\text{for convex } f)$$
    $$E[f(X)] \le f(E[X]) \quad (\text{for concave } f)$$

*   **Meaning**: Taking the average *after* applying a convex function gives a larger result than applying the function to the average.

---

### **`Topic 5.2` Gibbs’, Markov’s, and Chebyshev’s Inequalities**:

These inequalities provide **bounds** on the probabilities of events when the exact distribution of the random variable is unknown.

| Inequality | Formula | Purpose |
| :--- | :--- | :--- |
| **Gibbs'** | $H(P) \le \log(\|S\|)$ | Max entropy is uniform distribution. |
| **Markov's** | $P(X \ge a) \le \frac{E[X]}{a}$ | Bounds positive RV probability using only the mean. |
| **Chebyshev's** | $P(\|X - \mu\| \ge k\sigma) \le \frac{1}{k^2}$ | Bounds probability using mean ($\mu$) and standard deviation ($\sigma$). |

---

### **`Topic 5.3` Modes of Convergence**:

Describes how a sequence of random variables $X_n$ approaches a limit $X$.

| Mode | Notation | Meaning | Used by... |
| :--- | :--- | :--- | :--- |
| **Almost Surely** | $X_n \xrightarrow{a.s.} X$ | Converges for almost every outcome. | Strong Law |
| **In Probability** | $X_n \xrightarrow{P} X$ | Probability of being far away vanishes. | Weak Law |
| **In Distribution** | $X_n \xrightarrow{d} X$ | CDFs converge in shape. | Central Limit Thm. |

---

### **`Topic 5.4` Weak and Strong Laws of Large Numbers (WLLN & SLLN)**:

These theorems formalize the intuitive idea that the sample average converges to the population mean.

*   **Set-up**: Let $\bar{X}_n = \frac{1}{n} \sum_{i=1}^{n} X_i$ be the sample mean.

| Law | Formula | Mode of Convergence | Meaning |
| :--- | :--- | :--- | :--- |
| **Weak Law** | $\bar{X}_n \xrightarrow{P} \mu$ | **In Probability** | As $n \to \infty$, the sample mean is *likely* close to the true mean. |
| **Strong Law** | $\bar{X}_n \xrightarrow{a.s.} \mu$ | **Almost Surely** | The sample mean is *almost guaranteed* to be exactly equal to the true mean in the long run. |

---

### **`Topic 5.5` Central Limit Theorem (CLT)**:

The CLT is arguably the most important theorem in statistics. It states that the sum/average of a large number of independent random variables will be **approximately normally distributed**, *regardless* of the original distribution's shape.

*   **Formula (Standardized Sample Mean)**:
    $$\sqrt{n} \frac{(\bar{X}_n - \mu)}{\sigma} \xrightarrow{d} N(0, 1)$$

*   **Meaning**: We can use the Normal Distribution ($N(0, 1)$) to make inferences about means even if our original data isn't normal, provided the sample size ($n$) is large enough.

---

### **`Topic 5.6` Kullback–Leibler (KL) Divergence, Cross-Entropy, Mutual Information**:

These are measures from Information Theory used to quantify the difference between distributions and the amount of information shared between variables.

#### A. Kullback–Leibler (KL) Divergence
Measures how one probability distribution ($P$) is different from a second reference distribution ($Q$).

*   **Formula**: $D_{KL}(P || Q) = \sum_{x} P(x) \log\left(\frac{P(x)}{Q(x)}\right)$
*   **Note**: $D_{KL} \ge 0$, but it is **not** a true distance measure (it's non-symmetric: $D_{KL}(P || Q) \ne D_{KL}(Q || P)$).

#### B. Cross-Entropy ($H(P, Q)$)
Used widely in machine learning as a loss function for classification models. It is the average number of bits required to encode data from distribution $P$ using an optimized encoding scheme for distribution $Q$.

*   **Formula**: $H(P, Q) = H(P) + D_{KL}(P || Q) = -\sum_{x} P(x) \log(Q(x))$

#### C. Mutual Information ($I(X; Y)$)
Measures the amount of information obtained about one random variable ($X$) through observing the other random variable ($Y$).

*   **Formula**: $I(X; Y) = D_{KL}(P_{XY} || P_X P_Y)$
*   **Meaning**: It's the "distance" between the joint distribution and the product of the marginals (which would be zero if $X$ and $Y$ were independent).
