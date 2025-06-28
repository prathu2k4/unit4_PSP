### **Definition of a Random Process:**

A **random process** (or **stochastic process**) is a collection of random variables indexed by time (or space). Formally, a random process is a function:

$$
\{X(t, \omega) : t \in T, \omega \in \Omega\}
$$

where:

* $X(t)$ is the value of the process at time $t$,
* $\omega$ is an outcome from the sample space $\Omega$,
* $T$ is the index set (usually time),
* For each fixed $\omega$, $X(t, \omega)$ is a **sample function (realization)**,
* For each fixed $t$, $X(t)$ is a **random variable**.



### **Types of Random Processes (based on index set and value set):**

1. **Discrete-time, discrete-state** (e.g., Markov chains)
2. **Discrete-time, continuous-state** (e.g., stock prices sampled daily)
3. **Continuous-time, discrete-state** (e.g., Poisson process)
4. **Continuous-time, continuous-state** (e.g., Brownian motion)



### **Examples:**

#### **1. Tossing a Coin Repeatedly**

* Let $X_n$ be the outcome of the $n^\text{th}$ toss, where:

  $$
  X_n = 
  \begin{cases}
  1 & \text{if Head} \\
  0 & \text{if Tail}
  \end{cases}
  $$
* $\{X_n\}$ is a **discrete-time, discrete-state random process**.

#### **2. Thermal Noise in a Resistor**

* $X(t)$ is the instantaneous voltage across a resistor due to thermal agitation of electrons.
* This is a **continuous-time, continuous-state random process**.

#### **3. Queue Length in a Bank**

* Let $X(t)$ be the number of customers at time $t$.
* It changes randomly depending on arrivals and service times.
* This is a **continuous-time, discrete-state random process**.

#### **4. Stock Price Sampling Every Hour**

* $X_n$ is the stock price at the $n^\text{th}$ hour.
* This is a **discrete-time, continuous-state process**.

---

