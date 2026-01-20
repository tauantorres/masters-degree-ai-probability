# `Markov Chains`

---

### **`Topic 6.1` Markov Processes and Markov Chains, Markov Property**:

A **Markov Process** is a stochastic process that satisfies the **Markov Property**. A **Markov Chain** is a specific type of Markov process operating in discrete time with a discrete state space (a countable set of possible outcomes).

#### **The Markov Property (Memorylessness)**:
The defining characteristic is that the future state depends **only** on the present state, not on the sequence of events that preceded it.

*   **Formula**:
    $$P(X_{t+1} = j \mid X_t = i, X_{t-1} = i_{t-1}, \dots, X_0 = i_0) = P(X_{t+1} = j \mid X_t = i)$$

*   **Meaning**: The "history" is irrelevant once you know where you are right now.

---

### **`Topic 6.2` Geometric Interpretation**:

A Markov Chain is visually represented as a **directed graph**:

1.  **Nodes (States)**: Each possible outcome (e.g., "sunny", "cloudy", "rainy") is a node.
2.  **Edges (Transitions)**: Arrows indicate movement between states.
3.  **Weights (Probabilities)**: Each arrow is weighted by the probability of moving from one state to the next ($P_{ij}$).

*   **Visualization**: The *set* of transition probabilities from a single state $i$ must sum to 1 ($\sum_j P_{ij} = 1$). The entire system can be viewed as a system that moves between points in space based purely on these local "directions."

---

### **`Topic 6.3` Markov Kernel, Examples and Memory Properties**:

#### A. Markov Kernel (Transition Matrix)
For a finite state space, the transition probabilities are summarized in a matrix (**Markov Kernel** or **Transition Matrix** $\mathbf{P}$), where the entry $P_{ij}$ is the probability of moving from state $i$ to state $j$.

*   **Matrix Property**: $\mathbf{P}$ is a **stochastic matrix**: all entries are non-negative, and every row sums to 1.

#### B. Memory Properties (General vs. Homogeneous)
*   **Homogeneous Chain**: The transition probabilities $P_{ij}$ are **constant over time**. This is the standard assumption in most basic applications.
*   **Inhomogeneous Chain**: The probabilities change with time (e.g., $P_{ij}(t)$), making the process more complex.

---

### **`Topic 6.4` Stationary Distribution ($\pi$)**:

A **Stationary Distribution** (or equilibrium distribution) is a probability distribution over the states that remains unchanged after the chain transitions to the next step.

*   **Formula**: $\pi \mathbf{P} = \pi$
*   **Meaning**: If a system starts in a stationary distribution $\pi$, the distribution of where it will be tomorrow is still $\pi$. The system stops changing on average, even though it keeps moving between states.
*   **Existence**: A unique stationary distribution exists if the chain is irreducible and aperiodic (a common scenario).

---

### **`Topic 6.5` Irreducible and Reducible Chains**:

These terms describe the connectivity of the graph (geometric interpretation):

| Term | Definition | $\mathbf{P}$ Matrix Implication |
| :--- | :--- | :--- |
| **Irreducible** | It is possible to reach *any* state from *any* other state. | The matrix cannot be broken into separate blocks. |
| **Reducible** | There is at least one set of states that, once entered, cannot be exited to reach another set of states. | The matrix has blocks of zeros preventing movement. |

---

### **`Topic 6.6` Transient States**:

A state is **transient** if there is a non-zero probability that the process will never return to that state after leaving it once.

*   **Opposite**: A state is **recurrent** if the process is guaranteed to eventually return to that state.
*   **Long-Run Behavior**: In an irreducible, finite Markov chain, all states are recurrent. If a chain is reducible and has transient states, the process will eventually leave the transient states and get trapped in a closed, recurrent set of states.

---

### **`Topic 6.7` Sampling Problems and Monte Carlo Methods**:

Markov Chains are the basis for powerful computational techniques used to estimate complex systems (e.g., in physics, finance, machine learning).

#### **Markov Chain Monte Carlo (MCMC)**:
A class of algorithms for sampling from a probability distribution.

1.  **The Goal**: To simulate a complex distribution (the target distribution).
2.  **The Method**: Design a Markov Chain where the *stationary distribution* ($\pi$) is exactly the target distribution you want to sample from.
3.  **The Outcome**: Run the chain long enough (until it reaches its "burn-in" period/equilibrium), and the samples generated will behave according to the desired distribution.
*   **Examples**: Metropolis-Hastings algorithm, Gibbs sampling.
