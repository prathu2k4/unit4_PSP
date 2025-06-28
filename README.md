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
### **Definition: Wide Sense Stationary (WSS) Random Process**

A random process $X(t)$ is said to be **Wide Sense Stationary (WSS)** (also called **Weakly Stationary** or **Second-Order Stationary**) if its **first and second-order statistical properties** do **not change with time shift**.



### **Conditions for WSS:**

A random process $X(t)$ is **WSS** if:

1. **Constant Mean:**

   $$
   \mathbb{E}[X(t)] = \mu = \text{constant}, \quad \forall t
   $$

   The mean is **independent of time**.

2. **Autocorrelation Depends Only on Time Difference:**

   $$
   R_X(t_1, t_2) = \mathbb{E}[X(t_1) X(t_2)] = R_X(\tau), \quad \text{where } \tau = t_2 - t_1
   $$

   That is, the **autocorrelation function** depends only on the **lag $\tau$**, not the absolute time.



### **Notes:**

* WSS is **weaker** than strict-sense stationarity, which requires all joint distributions to be time-invariant.
* WSS is often sufficient for engineering applications, especially in signal processing and communications.



### **Example:**

Let $X(t) = A \cos(\omega_c t + \theta)$, where:

* $A$ and $\omega_c$ are constants,
* $\theta$ is a random variable uniformly distributed in $[0, 2\pi)$

Then $X(t)$ is **WSS** but not **strict-sense stationary**, because:

* Mean is constant: $\mathbb{E}[X(t)] = 0$
* Autocorrelation:

  $$
  R_X(\tau) = \frac{A^2}{2} \cos(\omega_c \tau)
  $$

  depends only on $\tau$

---
### **First-Order Stationarity (Mathematically):**

A random process $X(t)$ is said to be **first-order stationary** if its **first-order distribution**, or equivalently its **mean**, does not change with time. That is, the expected value of the process is constant for all time instants:

$$
\mathbb{E}[X(t)] = \mu, \quad \forall t
$$

This implies that the probability distribution of $X(t)$ is invariant to shifts in time, at least in terms of its mean. However, this condition alone does not say anything about the variance or correlation structure of the process.



### **Second-Order Stationarity (Wide Sense Stationarity - WSS):**

A random process $X(t)$ is said to be **second-order stationary** or **wide sense stationary (WSS)** if it satisfies two conditions:

1. The **mean is constant** over time:

$$
\mathbb{E}[X(t)] = \mu, \quad \forall t
$$

2. The **autocorrelation function** depends only on the **time difference (lag)** between any two time instants $t_1$ and $t_2$, i.e.,

$$
R_X(t_1, t_2) = \mathbb{E}[X(t_1) X(t_2)] = R_X(\tau), \quad \text{where } \tau = t_2 - t_1
$$

This means the second-order statistics (like variance and correlation) remain unchanged under time shifts. Second-order stationarity implies first-order stationarity, but not vice versa.

---
Here are examples of random processes that are **first-order stationary** but **not second-order stationary**:



### **Example 1: Time-Varying Variance (Heteroscedastic Process)**

Let:

$$
X(t) = A(t) \cdot Z(t)
$$

Where:

* $Z(t)$ is a zero-mean white noise process with constant variance $\sigma^2$
* $A(t) = \sqrt{t}$, a deterministic function increasing with time

Then:

* **Mean:**

  $$
  \mathbb{E}[X(t)] = \mathbb{E}[A(t) Z(t)] = A(t) \cdot \mathbb{E}[Z(t)] = 0 \quad \text{(constant)}
  $$
* **Variance:**

  $$
  \mathbb{E}[X^2(t)] = A^2(t) \cdot \mathbb{E}[Z^2(t)] = t \cdot \sigma^2 \quad \text{(changes with time)}
  $$

Hence, $X(t)$ is **first-order stationary** (mean is constant) but **not second-order stationary** (variance is not constant).

### **Example 2: Additive Drift**

Let:

$$
X(t) = Z(t) + bt
$$

Where:

* $Z(t)$ is a zero-mean WSS process with constant variance,
* $b$ is a non-zero constant

Then:

* **Mean:**

  $$
  \mathbb{E}[X(t)] = \mathbb{E}[Z(t) + bt] = 0 + bt = bt \quad \text{(not constant)}
  $$

This process **does not satisfy even first-order stationarity**, so to fix that, modify:

Let:

$$
X(t) = Z(t) \quad \text{(mean 0)}, \quad \text{but let the autocorrelation decay differently at each time}
$$

Or, in more concrete terms, take:

$$
X(t) = \cos(\omega t + \phi(t))
$$

Where $\phi(t)$ is a time-varying phase shift (non-stationary), such that:

* $\mathbb{E}[X(t)] = 0$ (assuming $\phi(t)$ is symmetrically distributed),
* But autocorrelation $R_X(t_1, t_2)$ depends on both $t_1$ and $t_2$ due to nonstationary $\phi(t)$

Thus, $X(t)$ can have **constant mean**, yet **nonstationary second-order structure**.
---

### **Autocorrelation Function (ACF):**

The **autocorrelation function** of a random process $X(t)$ measures the **statistical dependence** between values of the process at different times. It is defined as:

$$
R_X(t_1, t_2) = \mathbb{E}[X(t_1) \cdot X(t_2)]
$$

* For a **wide-sense stationary (WSS)** process, it depends only on the **time lag** $\tau = t_2 - t_1$, so:

  $$
  R_X(\tau) = \mathbb{E}[X(t) \cdot X(t + \tau)]
  $$
* It gives insight into how similar the process is to itself after a delay $\tau$.
* $R_X(0)$ is the **mean square value**, i.e., $R_X(0) = \mathbb{E}[X^2(t)]$



### **Autocovariance Function (ACVF):**

The **autocovariance function** removes the effect of the mean and captures only the fluctuations around the mean. It is defined as:

$$
C_X(t_1, t_2) = \mathbb{E}[(X(t_1) - \mu_1)(X(t_2) - \mu_2)]
$$

* Where $\mu_1 = \mathbb{E}[X(t_1)]$ and $\mu_2 = \mathbb{E}[X(t_2)]$
* For a **WSS process**, $\mu_1 = \mu_2 = \mu$, so:

  $$
  C_X(\tau) = \mathbb{E}[(X(t) - \mu)(X(t + \tau) - \mu)] = R_X(\tau) - \mu^2
  $$


  ### **Relation Between Autocorrelation and Autocovariance:**

$$
C_X(t_1, t_2) = R_X(t_1, t_2) - \mathbb{E}[X(t_1)] \cdot \mathbb{E}[X(t_2)]
$$

---
To prove that the **autocorrelation function** $R_X(\tau) = R_X(-\tau)$ for a **wide sense stationary (WSS)** process, we proceed using the definition of autocorrelation and the properties of expectation.



### **Given:**

For a **WSS random process** $X(t)$, the autocorrelation function is defined as:

$$
R_X(\tau) = \mathbb{E}[X(t) \cdot X(t + \tau)]
$$

Our goal is to prove that:

$$
R_X(\tau) = R_X(-\tau)
$$



### **Proof:**

Start with:

$$
R_X(-\tau) = \mathbb{E}[X(t) \cdot X(t - \tau)]
$$

By the **commutativity of multiplication**:

$$
R_X(-\tau) = \mathbb{E}[X(t - \tau) \cdot X(t)]
$$

Now, make a **change of variable**: let $t' = t - \tau$
Then $t = t' + \tau$, and since expectation is taken over the ensemble (not time), this is valid:

$$
R_X(-\tau) = \mathbb{E}[X(t') \cdot X(t' + \tau)] = R_X(\tau)
$$



### **Hence,**

$$
\boxed{R_X(\tau) = R_X(-\tau)}
$$

This shows that the autocorrelation function of a WSS process is **even**.]
---
### **Definition: Power Spectral Density (PSD)**

The **Power Spectral Density (PSD)** of a random process describes how its power (or variance) is distributed over frequency. For a **wide-sense stationary (WSS)** process $X(t)$, the PSD is the **Fourier transform** of its autocorrelation function:

$$
S_X(f) = \int_{-\infty}^{\infty} R_X(\tau) \, e^{-j 2\pi f \tau} \, d\tau
$$

Where:

* $S_X(f)$ is the **PSD** at frequency $f$,
* $R_X(\tau)$ is the **autocorrelation function** of $X(t)$,
* The result is a **real**, **non-negative**, and **even** function of frequency.



### **Wiener–Khintchine Theorem:**

The **Wiener–Khintchine theorem** establishes a fundamental connection between the **time-domain** and **frequency-domain** representations of a WSS random process.

**Statement:**

> For a real-valued, WSS random process $X(t)$ with autocorrelation function $R_X(\tau)$, the **Power Spectral Density** $S_X(f)$ is the **Fourier transform** of $R_X(\tau)$, and vice versa:

$$
S_X(f) = \mathcal{F} \left\{ R_X(\tau) \right\} = \int_{-\infty}^{\infty} R_X(\tau) \, e^{-j 2\pi f \tau} \, d\tau
$$

$$
R_X(\tau) = \mathcal{F}^{-1} \left\{ S_X(f) \right\} = \int_{-\infty}^{\infty} S_X(f) \, e^{j 2\pi f \tau} \, df
$$



### **Implications:**

* PSD tells you **how the power of a signal is distributed** across frequencies.
* Knowing either $R_X(\tau)$ or $S_X(f)$, you can compute the other.
* This is especially useful in analyzing random signals in communication and signal processing.

---
We are given the **autocorrelation function** of a WSS random process $X(t)$ as:

$$
R_X(\tau) = A e^{-\alpha |\tau|}, \quad A > 0, \, \alpha > 0
$$

We are to **find the Power Spectral Density (PSD)** $S_X(f)$ and **interpret** it.



### **Step 1: Use the Wiener–Khintchine Theorem**

The PSD is the **Fourier Transform** of the autocorrelation function:

$$
S_X(f) = \int_{-\infty}^{\infty} R_X(\tau) \, e^{-j2\pi f \tau} \, d\tau
$$

Substitute $R_X(\tau) = A e^{-\alpha |\tau|}$:

$$
S_X(f) = \int_{-\infty}^{\infty} A e^{-\alpha |\tau|} \, e^{-j2\pi f \tau} \, d\tau
$$



### **Step 2: Break Integral Using Symmetry**

Since $e^{-\alpha |\tau|}$ is **even**, split the integral:

$$
S_X(f) = A \left[ \int_{-\infty}^0 e^{\alpha \tau} e^{-j2\pi f \tau} \, d\tau + \int_0^{\infty} e^{-\alpha \tau} e^{-j2\pi f \tau} \, d\tau \right]
$$

Evaluate both parts:

**First integral:**

$$
\int_{-\infty}^0 e^{\alpha \tau} e^{-j2\pi f \tau} \, d\tau = \int_{-\infty}^0 e^{(\alpha - j2\pi f)\tau} \, d\tau = \frac{1}{\alpha - j2\pi f}
$$

**Second integral:**

$$
\int_0^{\infty} e^{-\alpha \tau} e^{-j2\pi f \tau} \, d\tau = \int_0^{\infty} e^{-(\alpha + j2\pi f)\tau} \, d\tau = \frac{1}{\alpha + j2\pi f}
$$

So,

$$
S_X(f) = A \left( \frac{1}{\alpha + j2\pi f} + \frac{1}{\alpha - j2\pi f} \right)
$$



### **Step 3: Simplify**

Use the identity:

$$
\frac{1}{\alpha + j2\pi f} + \frac{1}{\alpha - j2\pi f} = \frac{2\alpha}{\alpha^2 + (2\pi f)^2}
$$

Thus:

$$
\boxed{S_X(f) = \frac{2A\alpha}{\alpha^2 + (2\pi f)^2}}
$$



### **Interpretation:**

* The PSD is a **Lorentzian** function (bell-shaped, but with longer tails than Gaussian).
* It is **maximum at $f = 0$** and decays as frequency increases.
* The **bandwidth** is proportional to $\alpha$. Larger $\alpha$ → faster decay in $R_X(\tau)$, and hence **broader spectrum**.
* As $\alpha \to 0$, the spectrum becomes **narrower**; as $\alpha \to \infty$, $R_X(\tau) \to 0$ rapidly and spectrum flattens (like white noise).

---
### **Definition: White Noise**

**White noise** is a random process with a constant **power spectral density (PSD)** over all frequencies. It is the idealized signal that has **equal power across the entire frequency spectrum**—analogous to white light having equal intensity of all visible wavelengths.

Mathematically, a zero-mean **white noise process** $W(t)$ satisfies:

* **Autocorrelation function**:

  $$
  R_W(\tau) = N_0 \delta(\tau)
  $$

  where $\delta(\tau)$ is the **Dirac delta function**, and $N_0$ is a constant representing the **power spectral density level**.


### **PSD of White Noise**

Using the **Wiener–Khintchine theorem**:

$$
S_W(f) = \mathcal{F}\left\{ R_W(\tau) \right\} = \mathcal{F}\left\{ N_0 \delta(\tau) \right\} = N_0
$$

So,

$$
\boxed{S_W(f) = N_0}
$$

* This means the PSD is **constant** for all $f \in (-\infty, \infty)$.
* White noise has **equal power at all frequencies**, and hence is called *white* by analogy to white light.


### **Interpretation:**

* In practice, **ideal white noise** doesn't exist, since infinite bandwidth would imply **infinite power**.
* Real systems use **band-limited white noise**, where the PSD is flat over a limited frequency range.


---


### **Effects of White Noise on Systems:**

#### **1. Linear Time-Invariant (LTI) System Response:**

If a white noise process $W(t)$ is passed through an LTI system with impulse response $h(t)$, the **output PSD** is:

$$
S_Y(f) = |H(f)|^2 \cdot S_W(f) = N_0 |H(f)|^2
$$

* $H(f)$: frequency response of the system
* Output PSD takes the shape of the system's **magnitude squared response** scaled by $N_0$

#### **2. Filtering Effect:**

* A **low-pass filter** will pass low-frequency components of white noise → resulting output is **colored noise** (not white).
* A **band-pass filter** produces band-limited noise with flat PSD only in that band.

#### **3. Real-World Impact:**

* White noise is used to model **thermal noise** in resistors or amplifiers.
* It acts as a **disturbance** or **test signal** in control and signal processing systems.
* It **excites all frequencies**, so it's useful for system identification.

---

### **Mean of a Random Process:**

The **mean** of a random process $X(t)$ at time $t$ is the **expected value** of $X(t)$ over all possible outcomes $\omega$ in the probability space:

$$
\mu_X(t) = \mathbb{E}[X(t)] = \int_{-\infty}^{\infty} x \cdot f_{X(t)}(x) \, dx
$$

* $f_{X(t)}(x)$: probability density function of $X(t)$
* If the mean is **independent of time** (i.e., constant), the process is **first-order stationary**



### **Autocovariance of a Random Process:**

The **autocovariance function** of a random process $X(t)$ at times $t_1$ and $t_2$ is defined as the expected value of the **product of deviations from the mean**:

$$
C_X(t_1, t_2) = \mathbb{E}\left[(X(t_1) - \mu_X(t_1))(X(t_2) - \mu_X(t_2))\right]
$$

* Measures **how much two values of the process co-vary** as a function of time.
* For a **wide-sense stationary (WSS)** process, it depends only on the time difference $\tau = t_2 - t_1$, and the mean is constant $\mu$. Then:

$$
C_X(\tau) = \mathbb{E}\left[(X(t) - \mu)(X(t + \tau) - \mu)\right]
$$

---

### **Cross-Correlation Function:**

The **cross-correlation function** measures the **statistical similarity** between **two random processes** $X(t)$ and $Y(t)$ at different time instants. It is defined as:

$$
R_{XY}(t_1, t_2) = \mathbb{E}[X(t_1) \cdot Y(t_2)]
$$

This captures how the value of $X(t)$ at time $t_1$ is related, on average, to the value of $Y(t)$ at time $t_2$.



### **For Wide Sense Stationary (WSS) Processes:**

If both $X(t)$ and $Y(t)$ are WSS and jointly stationary, then the cross-correlation depends only on the **time difference** $\tau = t_2 - t_1$, and we write:

$$
R_{XY}(\tau) = \mathbb{E}[X(t) \cdot Y(t + \tau)]
$$

* $R_{XY}(0)$: correlation at the same time
* $R_{XY}(\tau)$: how much $X(t)$ and $Y(t+\tau)$ are linearly related



### **Properties:**

* $R_{XY}(-\tau) = R_{YX}(\tau)$
* If $X(t) = Y(t)$, then $R_{XY}(\tau)$ becomes the **autocorrelation** $R_X(\tau)$

---

The **cross-correlation function** plays a key role in analyzing the output of a **Linear Time-Invariant (LTI) system** when a random process is used as input.



### **System Setup:**

Let:

* $X(t)$: input random process
* $h(t)$: impulse response of the LTI system
* $Y(t)$: output of the system

Then, the output is given by **convolution**:

$$
Y(t) = \int_{-\infty}^{\infty} h(\tau) X(t - \tau) \, d\tau
$$



### **Cross-Correlation Between Input and Output:**

The **cross-correlation** between input $X(t)$ and output $Y(t)$ is:

$$
R_{XY}(\tau) = \mathbb{E}[X(t) \cdot Y(t + \tau)]
$$

Substitute the expression for $Y(t + \tau)$:

$$
R_{XY}(\tau) = \mathbb{E} \left[ X(t) \cdot \int_{-\infty}^{\infty} h(u) X(t + \tau - u) \, du \right]
$$

Interchanging expectation and integration (valid under mild conditions):

$$
R_{XY}(\tau) = \int_{-\infty}^{\infty} h(u) \mathbb{E}[X(t) \cdot X(t + \tau - u)] \, du
= \int_{-\infty}^{\infty} h(u) R_X(\tau - u) \, du
$$

So:

$$
\boxed{R_{XY}(\tau) = (h * R_X)(\tau)}
$$

This means the **cross-correlation between input and output** is the **convolution** of the **system's impulse response** and the **autocorrelation function** of the input.



### **Implication in Frequency Domain:**

Using Fourier Transforms:

$$
S_Y(f) = |H(f)|^2 S_X(f)
$$

This shows how the **output PSD** is shaped by the **magnitude-squared frequency response** of the system.

---

### **Impact of LTI Systems on Random Processes**

When a **Linear Time-Invariant (LTI) system** processes a **random process** as input, it transforms its statistical properties—particularly the **mean**, **autocorrelation**, and **power spectral density (PSD)**—in predictable ways.



### **1. Mean of Output:**

Let:

* $X(t)$: input random process
* $Y(t)$: output random process
* $h(t)$: impulse response of the LTI system

Then, if $\mu_X = \mathbb{E}[X(t)]$ is the mean of the input, the mean of the output is:

$$
\mu_Y = \mathbb{E}[Y(t)] = \mu_X \cdot \int_{-\infty}^{\infty} h(\tau) \, d\tau
$$

* The output mean is **scaled** by the area under the system’s impulse response.



### **2. Autocorrelation of Output:**

If $X(t)$ is **WSS** with autocorrelation $R_X(\tau)$, then the output autocorrelation is:

$$
R_Y(\tau) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} h(u) h(v) R_X(\tau + u - v) \, du \, dv
$$

This shows that the output autocorrelation is the **double convolution** of the input autocorrelation with the impulse response.



### **3. Power Spectral Density (PSD):**

The most practical and widely used result is in the frequency domain. If $S_X(f)$ is the input PSD and $H(f)$ is the Fourier Transform of $h(t)$, then:

$$
\boxed{S_Y(f) = |H(f)|^2 \cdot S_X(f)}
$$

* The output PSD is the input PSD **shaped** by the **squared magnitude of the system’s frequency response**.
* The system acts as a **spectral filter**: low-pass, high-pass, band-pass, etc.



### **Interpretation:**

* An LTI system **does not introduce new randomness**; it **reshapes existing randomness**.
* If the input is white noise $S_X(f) = N_0$, then the output PSD becomes $S_Y(f) = N_0 |H(f)|^2$, which is **colored noise**.
* This principle is crucial in **filter design**, **noise analysis**, and **signal detection**.

---

