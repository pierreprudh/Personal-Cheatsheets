# **1. Foundations of Statistics**

Statistics is the language used to reason about uncertainity through mathematics 
In data-science it helps us making evaluation and assumptions

## 1.1 What Is Statistics in Data Science?

In practice, statistics helps answer questions like :
- Is this pattern real or just random ?
- How confident are we in this estimate ?
- Is one model truly better than another ?

### Descriptive vs Inferential statistics

#### Descriptive Statistics
Describe what the data **looks like**

Examples :
- mean, median, ...
- variance, standard deviation
- histograms, boxplots

Mathematically, descriptive statistics summarize a dataset  
\[
X = \{x_1, x_2, \dots, x_n\}
\]



#### Inferential Statistics
Use samples to **draw conclusions about a population**

Examples :
- confidence intervals
- hypothesis tests
- statistical significance


## 1.2 Population vs Sample

### Population
The **entire set** of interest/individuals

Example :
- All customers


Denoted conceptually as :
\[
\mathcal{P}
\]

### Sample
A **subset** of the population used for analysis 

\[
X = \{x_1, x_2, \dots, x_n\} \subset \mathcal{P}
\]


**Sample Risks** : 
- biased 
- too small 
- unrepresentative

This will directly impacts model ``performance`` and ``generalization``

## 1.3 Bias, Variance & Noise 

### Bias
Systematic error due to incorrect assumptions

Example :
- sampling only active users
- measurement errors
- flawed data collection

Formally, bias measures the error between the expected prediction and the true value:

\[
\text{Bias} = \mathbb{E}[\hat{f}(x)] - f(x)
\]


### Variance
Sensitivity of a model to fluctuations in the training data

Example :
- different samples => different model results

Mathematically :

\[
\text{Variance} = \mathbb{E}[(\hat{f}(x) - \mathbb{E}[\hat{f}(x)])^2]
\]


### Noise
Random, irreducible uncertainty

Example :
- human behavior
- sensor inaccuracies


### Bias–Variance–Noise Decomposition

The expected prediction error can be decomposed as:

\[
\mathbb{E}[(y - \hat{f}(x))^2] =
\text{Bias}^2 + \text{Variance} + \text{Noise}
\]

**In machine learning it results in**

| Concept | Impact |
|------|------|
| High bias | Underfitting |
| High variance | Overfitting |
| Noise | Performance ceiling |

## 1.4 Deterministic vs Stochastic Systems

### Deterministic
Same input => same output.

Example :
- physics formulas
- sorting algorithms

\[
y = f(x)
\]


### Stochastic
Output involves randomness

\[
y = f(x) + \varepsilon
\]

where \(\varepsilon\) is a random variable (noise).

Example :
- user clicks
- stock prices
- biological data


## 1.5 Types of Data

Understanding data types is critical because they determine :
- which statistical methods are valid
- which visualizations make sense
- which ML models can be used


### 1.5.1 Numerical vs Categorical Data

#### Numerical Data
Data that represents **quantitative values**

Mathematically :
\[
x \in \mathbb{R}
\]

Example : 
- age / temperature / revenue

So they support ***arithmetic operations** and **statistical distributions**

#### Categorical Data
Data that represents **labels or groups**

Mathematically : 
\[
x \in \{c_1, c_2, \dots, c_k\}
\]

Example :
- gender/places/species

Categorical data **has no inherent numeric meaning**


### 1.5.2 Discrete vs Continuous Data

#### Discrete Data
Data that takes **countable values**

\[
x \in \mathbb{Z}
\]

Examples :
- number of users
- number of purchases

Common models :
- Binomial distribution
- Poisson distribution

#### Continuous Data
Data that can take **any value in an interval**.

\[
x \in \mathbb{R}
\]

Examples:
- height/weight/time

Common models :
- Normal distribution
- Exponential distribution

### 1.5.3 Ordinal vs Nominal Data

#### Nominal Data
Categories **without intrinsic order**

Examples:
- city/color/country

Key property :
\[
c_1 \neq c_2 \quad \text{but no ordering relation}
\]

Implications :
- One-Hot Encoding
- No distance or ranking


### 1.5.4 Implications for Visualization

| Data Type | Recommended Visualizations |
|--------|---------------------------|
| Numerical | Histogram, KDE, Boxplot, Scatter |
| Categorical | Bar plot, Count plot |
| Numerical vs Categorical | Boxplot, Violin plot |
| Numerical vs Numerical | Scatter, Heatmap |



### 1.5.5 Implications for Modeling

| Data Type | ML Considerations |
|--------|------------------|
| Numerical | Scaling, normalization |
| Categorical (nominal) | One-Hot Encoding |
| Categorical (ordinal) | Ordered encoding |
| Mixed | Pipelines required |

Examples :
- Linear models require numerical inputs
- Tree-based models handle categories better
- Distance-based models are sensitive to encoding


---

# **2. Descriptive Statistics**

Descriptive statistics summarize and describe the **main characteristics of a dataset**.

Let a dataset be :
\[
X = \{x_1, x_2, \dots, x_n\}
\]

## 2.1 Measures of Central Tendency

Central tendency describes the **typical value** of a dataset.

### Mean (Average)

The arithmetic mean is defined as :
\[
\mu = \frac{1}{n} \sum_{i=1}^{n} x_i
\]

Properties :
- Uses all data points
- Sensitive to outliers

Very realist when the distribution is symmetric with no outliers ! 


### Median

The median is the **middle value** when data is sorted.

\[
\text{Median}(X) =
\begin{cases}
x_{(n+1)/2}, & n \text{ odd} \\
\frac{x_{(n/2)} + x_{(n/2+1)}}{2}, & n \text{ even}
\end{cases}
\]

Properties :
- Robust to outliers
- Works well for skewed data

It's also the go to method to fill missing values


## 2.2 Measures of Dispersion

Dispersion measures how **spread out** the data is

### Range

\[
\text{Range} = \max(X) - \min(X)
\]

Simple but very sensitive to outliers


### Variance
Variance is the average of the squared differences from the mean, representing how far a set of numbers is spread out from their average value.

Population variance :
\[
\sigma^2 = \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2
\]

Sample variance ``size n`` (unbiased estimator) :
\[
s^2 = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2
\]
`


### Standard Deviation

Standard deviation is the **square root of the variance**, representing the average distance of data points from the mean in their original units.

\[
\sigma = \sqrt{\sigma^2}
\]

Same units as the data (not the squared value from the variance) => easier to interpret 


### Interquartile Range (IQR)

The Interquartile Range (IQR) is the difference between the 75th and 25th percentiles, representing the spread of the middle 50% of a dataset.

\[
\text{IQR} = Q_3 - Q_1
\]

Properties :
- Robust to outliers
- Used in boxplots and outlier detection


## 2.3 Shape of Distributions

Understanding shape is critical for :
- model assumptions
- transformations
- statistical tests


### Skewness

Skewness measures **asymmetry**

\[
\text{Skewness} = \mathbb{E}\left[\left(\frac{X - \mu}{\sigma}\right)^3\right]
\]

Interpretation :
- Skewness = 0 => symmetric
- Positive => right-skewed
- Negative => left-skewed

### Kurtosis

Kurtosis measures **tail heaviness**.

\[
\text{Kurtosis} = \mathbb{E}\left[\left(\frac{X - \mu}{\sigma}\right)^4\right]
\]

Interpretation :
- High kurtosis => heavy tails, more outliers
- Low kurtosis => light tails



## 2.4 Descriptive Statistics in Pandas

### `pandas .describe()`

```python
df.describe()
```


## Link between Descriptive Statistics and Visualization 

| Statistic	| Visualization|
|-----------|--------------|
| Mean / Median	| Histogram, KDE |
| Variance	| Boxplot |
| IQR	| Boxplot |
| Skewness |	Histogram, KDE |
| Outliers	| Boxplot |

---

# **3. Probability Theory (Core Concepts)**

Probability theory provides the mathematical framework to **model uncertainty**

## 3.1 Random Variables

A **random variable** represents a numerical outcome of a random process.

Formally:
\[
X : \Omega \rightarrow \mathbb{R}
\]

Where:
- \(\Omega\) is the sample space
- \(X\) maps outcomes to numerical values

### Discrete Random Variables

A random variable that takes **countable values**

\[
X \in \{x_1, x_2, \dots\}
\]

Example :
- number of purchases


### Continuous Random Variables

A random variable that takes values in a **continuous interval**

\[
X \in \mathbb{R}
\]

Example :
- height

## 3.2 Probability Mass Function (PMF)

For a discrete random variable :

\[
P(X = x) = p(x)
\]

Properties:
\[
0 \le p(x) \le 1
\]
\[
\sum_x p(x) = 1
\]

Example :
- Bernoulli variable (success / failure)


## 3.3 Probability Density Function (PDF)

For a continuous random variable, probabilities are defined via a **density function**

\[
P(a \le X \le b) = \int_a^b f(x)\,dx
\]

Properties :
\[
f(x) \ge 0
\]
\[
\int_{-\infty}^{+\infty} f(x)\,dx = 1
\]

Important :
> \(f(x)\) is **not** a probability => it is a density.

## 3.4 Cumulative Distribution Function (CDF)

The CDF gives the probability that a random variable is **less than or equal to** a value

\[
F(x) = P(X \le x)
\]

Properties:
- non-decreasing
- \(0 \le F(x) \le 1\)
- fully characterizes a distribution

## 3.5 Expected Value (Mean)

The expected value represents the **long-run average**


### Discrete Case

\[
\mathbb{E}[X] = \sum_x x \cdot p(x)
\]

### Continuous Case

\[
\mathbb{E}[X] = \int_{-\infty}^{+\infty} x \cdot f(x)\,dx
\]


## 3.6 Variance

Variance measures **dispersion around the mean**.

\[
\mathrm{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2]
\]

Equivalent form:
\[
\mathrm{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2
\]


## 3.7 Joint Probability

The probability of two random variables occurring together

\[
P(X = x, Y = y)
\]

Joint distributions capture **dependencies**


## 3.8 Conditional Probability

Probability of an event given another event occurred

\[
P(X|Y) = \frac{P(X,Y)}{P(Y)}
\]

Interpretation :
> Our belief about \(X\) changes after observing \(Y\)


## 3.9 Independence

Two random variables are independent if:

\[
P(X,Y) = P(X)P(Y)
\]

Equivalent :
\[
P(X|Y) = P(X)
\]

**Why Independence Matters in ML**
- Naive Bayes assumes conditional independence
- Feature engineering often tries to reduce dependence 

---

# **4. Common Probability Distributions**

Probability distributions describe **how random variables behave**
Choosing the right distribution is essential 

## 4.1 Discrete Distributions

Discrete distributions model **countable outcomes**

### 4.1.1 Bernoulli Distribution

Models a **single binary trial**.

\[
X \sim \text{Bernoulli}(p)
\]

\[
P(X = 1) = p,\quad P(X = 0) = 1 - p
\]

Expected value :
\[
\mathbb{E}[X] = p
\]

Variance :
\[
\mathrm{Var}(X) = p(1 - p)
\]

Example :
- CoinFlip repetition 

### 4.1.2 Binomial Distribution

Models the **number of successes in \(n\) independent Bernoulli trials**

\[
X \sim \text{Binomial}(n, p)
\]

\[
P(X = k) = \binom{n}{k} p^k (1 - p)^{n-k}
\]

Expected value :
\[
\mathbb{E}[X] = np
\]

Variance :
\[
\mathrm{Var}(X) = np(1 - p)
\]

Example :
- gym's weight utilisation


### 4.1.3 Poisson Distribution

Models the **number of events occurring in a fixed interval**, given a known average rate

\[
X \sim \text{Poisson}(\lambda)
\]

\[
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}
\]

Expected value :
\[
\mathbb{E}[X] = \lambda
\]

Variance :
\[
\mathrm{Var}(X) = \lambda
\]

Example :
- number of website visits per minute
- number of system failures per day


## 4.2 Continuous Distributions

Continuous distributions model **measurements on a continuous scale**.

### 4.2.1 Uniform Distribution

All values in an interval are *equally likely*

\[
X \sim \mathcal{U}(a, b)
\]

PDF :
\[
f(x) = \frac{1}{b - a}, \quad a \le x \le b
\]

Expected value :
\[
\mathbb{E}[X] = \frac{a + b}{2}
\]

Variance :
\[
\mathrm{Var}(X) = \frac{(b - a)^2}{12}
\]

Examples:
- random initialization

ML link :
- Random sampling
- Monte Carlo methods

### 4.2.2 Normal (Gaussian) Distribution

The most important distribution in statistics

\[
X \sim \mathcal{N}(\mu, \sigma^2)
\]

PDF :
\[
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left(-\frac{(x - \mu)^2}{2\sigma^2}\right)
\]

Properties :
- symmetric around \(\mu\)
- fully defined by mean and variance

Example :
- measurement noise

ML link :
- Linear regression assumptions
- Squared error loss
- Central Limit Theorem

### 4.2.3 Exponential Distribution

Models **time until an event occurs**

\[
X \sim \text{Exponential}(\lambda)
\]

PDF :
\[
f(x) = \lambda e^{-\lambda x}, \quad x \ge 0
\]

Expected value :
\[
\mathbb{E}[X] = \frac{1}{\lambda}
\]

Variance :
\[
\mathrm{Var}(X) = \frac{1}{\lambda^2}
\]

Key property (memoryless) :
\[
P(X > s + t \mid X > s) = P(X > t)
\]

Examples:
- time until failure
- waiting time between events


## 4.3 Choosing the right distribution

Always verify the normality with statistical checks. 
Don't ignore the outliers or skewness.

| Data Type | Typical Distribution |
|--------|--------------------|
| Binary outcome | Bernoulli |
| Count (fixed trials) | Binomial |
| Count (time-based) | Poisson |
| Continuous (noise) | Normal |
| Waiting time | Exponential |

---

# **5. Sampling & the Central Limit Theorem**

Sampling is unavoidable when working with big dataset
The Central Limit Theorem (CLT) explains **why we can still make reliable inferences** from samples

## 5.1 Sampling

Sampling is the process of selecting a **subset** from a population to estimate its properties

Let :
- population mean : \(\mu\)
- population variance : \(\sigma^2\)
- sample : \(X = \{x_1, x_2, \dots, x_n\}\)

### 5.1.1 Random Sampling

Each individual has an equal probability of being selected

Properties :
- unbiased estimates
- simplest assumption in statistics

Used when :
- data is i.i.d (independent and identically distributed)
- population is homogeneous


### 5.1.2 Stratified Sampling

Population is divided into **subgroups (strat)**, then sampled within each group

Examples :
- class-balanced datasets
- demographic fairness

Benefits :
- lower variance
- better representation of minorities


### 5.1.3 Sampling Bias

Occurs when the sample is **not representative**

Examples :
- selection bias
- temporal bias

Impact :
- misleading statistics
- poor generalization
- invalid conclusions


## 5.2 Sample Mean as an Estimator

The sample mean is defined as :
\[
\bar{X} = \frac{1}{n} \sum_{i=1}^{n} x_i
\]

Properties :
- unbiased estimator of \(\mu\)
- variance decreases as \(n\) increases

\[
\mathbb{E}[\bar{X}] = \mu
\]

\[
\mathrm{Var}(\bar{X}) = \frac{\sigma^2}{n}
\]


## 5.3 The Central Limit Theorem (CLT)

### Statement

Let \(X_1, X_2, \dots, X_n\) be i.i.d random variables with :
- mean \(\mu\)
- variance \(\sigma^2 < \infty\)

Then, as \(n \to \infty\) :

\[
\frac{\bar{X} - \mu}{\sigma / \sqrt{n}}
\;\xrightarrow{d}\;
\mathcal{N}(0,1)
\]


## 5.4 Why CLT Is So Important

CLT explains why :
- confidence intervals work
- hypothesis tests work
- many ML losses behave nicely
- averages are stable estimators

Without CLT, inferential statistics would collapse


## 5.5 Practical Implications in Data Science

### Sample Size Matters

- Small \(n\) => high uncertainty
- Large \(n\) => stable estimates

Rule of thumb :
- \(n \ge 30\) => CLT often applies
- but depends on distribution shape

### Error Shrinks with Data

Standard error :
\[
\text{SE} = \frac{\sigma}{\sqrt{n}}
\]

Doubling data does **not** halve error => it shrinks by \(\sqrt{2}\).

## 5.6 CLT in Machine Learning

CLT explains :
- why cross-validation averages are meaningful
- why ensemble methods reduce variance
- why training loss converges smoothly

Example :
- Bagging = averaging weak learners → lower variance


## 5.7 Common Misunderstandings 

- CLT does **not** say the data becomes normal
- CLT applies to the **mean**, not individual samples
- Heavy-tailed distributions need larger \(n\)

---

# **6. Statistical Inference**
## 6.1 Estimation
- Point estimates
- Bias vs variance
- Maximum Likelihood Estimation (MLE)

## 6.2 Confidence Intervals
- Interpretation (what they *really* mean)
- Confidence level
- CI for mean & proportion

---

# **7. Hypothesis Testing**
## 7.1 Hypothesis Testing Framework
- Null vs Alternative hypothesis
- Test statistics
- p-values
- Significance level (α)

## 7.2 Common Statistical Tests
- Z-test
- Student’s t-test
- Chi-square test
- ANOVA

## 7.3 Common Mistakes
- p-value misinterpretation
- p-hacking
- Statistical vs practical significance

---

# **8. Correlation & Dependence**
## 8.1 Correlation Measures
- Pearson
- Spearman
- Kendall

## 8.2 Correlation vs Causation
- Confounders
- Simpson’s paradox
- Spurious correlations

## 8.3 Visualization + Correlation
- Heatmaps
- Pairplots
- Joint plots

---

# **9. Regression from a Statistical Perspective**
## 9.1 Simple Linear Regression
- Statistical assumptions
- Error terms
- Residual analysis

## 9.2 Multiple Linear Regression
- Multicollinearity
- Interpretation of coefficients
- R² vs adjusted R²

## 9.3 Regularization (Statistical View)
- Ridge
- Lasso
- Bias–variance tradeoff

---

# **10. Statistical Assumptions in ML**
## 10.1 Common Assumptions
- Linearity
- Independence
- Homoscedasticity
- Normality of errors

## 10.2 Diagnosing Violations
- Residual plots
- QQ plots
- Statistical tests

---

# **11. Statistics for Model Evaluation**
## 11.1 Metrics as Statistical Quantities
- Mean squared error
- Log loss
- Cross-entropy

## 11.2 Cross-Validation
- Why it works statistically
- Bias vs variance
- K-fold intuition

---

# **12. Practical Statistics Workflow**
## 12.1 From Data to Decision
- EDA → hypothesis
- Test → conclusion
- Model → validation

## 12.2 Common Pitfalls in Real Projects
- Small sample sizes
- Multiple testing
- Leakage
- Overconfidence

---

# **13. Statistics vs Machine Learning**
- When statistics is enough
- When ML is needed
- Interpretability vs performance
- Business decision perspective

---

# **14. To-Go Further (Advanced Topics)**
- Bayesian statistics
- Bootstrapping
- Permutation tests
- Causal inference
- A/B testing