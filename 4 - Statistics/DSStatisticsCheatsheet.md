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




## 1.2 Types of Data
- Numerical vs Categorical
- Discrete vs Continuous
- Ordinal vs Nominal
- Implications for visualization & modeling

---

# **2. Descriptive Statistics**
## 2.1 Central Tendency
- Mean
- Median
- Mode
- When each one is appropriate

## 2.2 Dispersion
- Variance
- Standard deviation
- Range
- Interquartile range (IQR)

## 2.3 Shape of Distributions
- Skewness
- Kurtosis
- Symmetry
- Heavy tails

## 2.4 Descriptive Statistics in Pandas
- `.describe()`
- Grouped statistics
- Robust statistics

---

# **3. Probability Theory (Core Concepts)**
## 3.1 Random Variables
- Discrete vs Continuous
- Probability Mass Function (PMF)
- Probability Density Function (PDF)

## 3.2 Probability Rules
- Joint probability
- Conditional probability
- Independence

## 3.3 Bayes’ Theorem
- Intuition
- Why it matters in ML
- Real DS examples

---

# **4. Common Probability Distributions**
## 4.1 Discrete Distributions
- Bernoulli
- Binomial
- Poisson

## 4.2 Continuous Distributions
- Uniform
- Normal (Gaussian)
- Exponential

## 4.3 When to Use Which Distribution
- Mapping real data to distributions
- Assumptions and pitfalls

---

# **5. Sampling & the Central Limit Theorem**
## 5.1 Sampling Techniques
- Random sampling
- Stratified sampling
- Sampling bias

## 5.2 Central Limit Theorem (CLT)
- Intuition (critical!)
- Why averages behave normally
- Impact on confidence intervals & tests

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