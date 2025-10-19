# 🎲 DSCI 551 – Lecture 1 Notes : Depicting Uncertainty

## 1️⃣ Core Concepts of Probability
- **Experiment** → an action with uncertain outcome (coin toss, die roll).  
- **Sample space (S)** → all possible outcomes.  
  - Example: `S = {Heads, Tails}`  
- **Event (E)** → subset of S (e.g. `E = {Heads}`).

**Empirical probability**
\[
P(E) = \frac{\text{# times E occurs}}{\text{# total experiments}}
\]
approaches the true value as n → ∞.

---

## 2️⃣ Axioms & Laws
1. **Axiom 1 (Sample space)** → `P(S)=1`  
2. **Axiom 2 (Mutually exclusive events)** → `P(A∪B)=P(A)+P(B)` if A∩B=∅  
3. **Complement rule** → `P(Ac)=1−P(A)`  
4. **Law of Total Probability** → probability of E = sum of probabilities of its disjoint parts  
5. **Inclusion–Exclusion Principle**


P(A ∪ B) = P(A) + P(B) − P(A ∩ B)

extended to 3+ events by alternating + / – terms.  
6. **Independence** → `P(A ∩ B)=P(A)·P(B)`

---

## 3️⃣ Odds ↔ Probability
\[
o = \frac{p}{1-p}, \quad p = \frac{o}{o+1}
\]
Example: p = 0.8 ⇒ o = 4 : 1 (4 wins per loss)

---

## 4️⃣ Random Variables (RV)
- **Discrete RV:** countable outcomes → Probability Mass Function (PMF) `P(X=x)`
- **Continuous RV:** uncountable outcomes → Probability Density Function (PDF) `fX(x)`
- Example: X = # heads in 10 coin tosses.

---

## 5️⃣ Measures of Central Tendency & Uncertainty

| Measure | Meaning | Formula |
|----------|----------|----------|
| **Mean (E[X])** | expected/typical value | `Σ x P(X=x)` or `∫ x f(x) dx` |
| **Variance (Var[X])** | spread/uncertainty | `E[(X−E[X])²] = E[X²]−E[X]²` |
| **Std Dev (σ)** | sqrt of variance | `σ = √Var[X]` |
| **Mode** | most probable outcome | argmax P(X=x) |
| **Entropy H(X)** | randomness in bits/nats | `−Σ P(X=x) log P(X=x)` |

---

## 6️⃣ Examples to Remember
- **Mario Kart items** as a discrete distribution: probs sum to 1.  
- **Complement example:** P(not Coin) = 1 − 0.75 = 0.25.  
- **Inclusion–Exclusion example:** Explosion ∨ Blue-shell item = 0.08.  
- **Entropy example:** H ≈ 0.87 → some randomness but not uniform.

---

## 7️⃣ Key Formulas Summary
```text
P(Ac) = 1 − P(A)
P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
P(A ∩ B) = P(A)·P(B)   # if independent
Var(X) = E[X²] − (E[X])²
H(X) = −Σ P(x)·log P(x)
```
---

# 🎯 DSCI 551 Lecture 2 – Parametric Families

Refresher on probability distributions, random-variable transformations, and the most common discrete distribution families.

---

## 1️⃣ Review — Properties of Distributions
Example PMF (Number of crabs per nest):

| x | P(X = x) |
|---|-----------|
| 0 | 0.4 |
| 1 | 0.1 |
| 2 | 0.1 |
| 3 | 0.4 |

**Mean**

\[
E[X] = \sum x P(X=x) = 1.5
\]

**Variance**

\[
Var(X) = E[(X−E[X])²] = 1.85
\]

**Mode** → values with max probability → 0 and 3  
**Entropy**

\[
H(X) = − \sum P(X=x) log P(X=x) = 1.19
\]

- Higher variance ⇒ values further from mean.  
- Higher entropy ⇒ probabilities more uniform.

---

## 2️⃣ Random-Variable Transformations
- Define a new variable: `Z = X²`  
- **Law of the Unconscious Statistician (LOTUS):**

\[
E[g(X)] = \sum g(x) P(X=x)
\]

No need to derive PMF of Z; use X’s PMF directly.

### Expectation Properties
If a,b constants and X,Y RVs:

\[
E(aX)=aE(X),\quad E(X+Y)=E(X)+E(Y),\quad E(aX+bY)=aE(X)+bE(Y)
\]

⚠️ Not always: `E(XY) ≠ E(X)E(Y)` (unless independent).  
Also `E(X²) ≠ [E(X)]²`.

### Variance Properties (Independent X,Y)
\[
Var(aX)=a²Var(X),\quad Var(X+Y)=Var(X)+Var(Y)
\]

---

## 3️⃣ Distribution Families
A *family* = set of distributions defined by its parameters.

Example: Binomial family has parameters n and p.  
Choosing specific n,p → a unique distribution.

---

## 4️⃣ Key Discrete Distribution Families

### **Bernoulli (p)**
Experiment = success/failure.

\[
P(X=x) = p^x (1-p)^{1-x},\quad x∈{0,1}
\]

E[X] = p Var[X] = p(1−p)

---

### **Binomial (n,p)**
n independent Bernoulli trials.

\[
P(X=x) = {n\choose x} p^x (1-p)^{n-x},\; x=0…n
\]

E[X] = np Var[X] = np(1−p)

*Example:* P(win exactly 2 of 5) = C(5,2)(0.25)²(0.75)³ = 0.26

---

### **Geometric (p)**
### of failures before 1st success.

\[
P(X=x)=p(1-p)^x,\; x=0,1,2…
\]
E[X]=(1−p)/p Var[X]=(1−p)/p²

---

### **Negative Binomial (k,p)**
### of failures before k successes.

\[
P(X=x)={k−1+x\choose x} p^k(1−p)^x
\]
E[X]=k(1−p)/p Var[X]=k(1−p)/p²  
Special case k=1 → Geometric.

---

### **Poisson (λ)**
### of events in fixed interval (time or space).

\[
P(X=x)=\frac{λ^x e^{−λ}}{x!},\; x=0,1,2…
\]
E[X]=λ Var[X]=λ  
Typical uses: # emails/day, # arrivals/hour, etc.

---

## 5️⃣ Parameters & Parameterization
- **Parameter:** numeric value that defines distribution shape (e.g., p or λ).  
- **Parameterization:** how those parameters identify a member within the family.  
- *Canonical parameterization* = most common form (e.g., Binomial → n,p).

---

## 🧠 Key Takeaways
- Mean = expected value; variance = spread; entropy = uncertainty.  
- Transformations → use LOTUS for E[g(X)].  
- Families group distributions by parameters.  
- Common families: Bernoulli, Binomial, Geometric, Negative Binomial, Poisson.  
- Poisson notable: mean = variance.

---

# 📊 DSCI 551 Lecture 3 — Joint Distributions & Dependence

A refresher on how multiple random variables interact through joint, marginal, and conditional distributions, and how dependence is measured.

---

## 1️⃣ Joint Distributions

- A **joint distribution** gives the probability of every possible combination of two (or more) random variables.  
  Example: two fair coins (X = first coin, Y = second coin)

| X\Y | H  | T  |
|------|----|----|
| H | 0.25 | 0.25 |
| T | 0.25 | 0.25 |

Each cell → `P(X=x, Y=y)`.

> For independent fair coins:  
> `P(X=H ∩ Y=H) = P(X=H)·P(Y=H) = 0.5·0.5 = 0.25`.

The full table must sum to 1.

---

## 2️⃣ Marginal Distributions

The probability distribution of one variable alone.  
Compute by **summing** over the other variable:

\[
P(X=x) = \sum_y P(X=x, Y=y)
\]
\[
P(Y=y) = \sum_x P(X=x, Y=y)
\]

> Only the *whole table* sums to 1 — not each row/column.

---

## 3️⃣ Independence of Random Variables

Two RVs X, Y are independent iff

\[
P(X=x, Y=y) = P(X=x) · P(Y=y)\quad \forall x,y
\]

Equivalent properties:

- \(E[XY]=E[X]E[Y]\)  
- \(Var(X+Y)=Var(X)+Var(Y)\) when independent  

Independence means knowing one variable gives no information about the other.

---

## 4️⃣ Dependence & Covariance

When X and Y are not independent, we can measure their dependence.

**Covariance**
\[
Cov(X,Y)=E[(X−E[X])(Y−E[Y])]=E[XY]−E[X]E[Y]
\]

- \(Cov>0\) ⇒ as X increases, Y tends to increase.  
- \(Cov<0\) ⇒ as X increases, Y tends to decrease.  
- \(Cov=0\) ⇒ no *linear* relationship (but not necessarily independent).

**Example:**  
Ship length of stay (LOS) vs gang demand  
→ negative covariance ≈ −0.74 → longer stays → fewer gangs requested.

---

## 5️⃣ Correlation Coefficients

### **Pearson Correlation (ρ)**  
Standardizes covariance to (−1 … 1):

\[
ρ(X,Y)=\frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}
\]

- -1 → perfect negative linear relation  
- 0 → no linear relation (≠ independence)  
- 1 → perfect positive linear relation  
Invariant to scaling: Corr(10X, Y)=Corr(X,Y)

---

### **Kendall’s τ (Rank Correlation)**
For ordinal or non-linear relations.

\[
τ_K=\frac{\# concordant pairs−\# discordant pairs}{n(n−1)/2}
\]

- τ ≈ 1 → strong positive association  
- τ ≈ 0 → no monotonic relationship  
- τ ≈ −1 → strong negative association

Captures *monotonic* (not just linear) dependence.

---

## 6️⃣ Variance of a Sum

For any two RVs:

\[
Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)
\]

If independent → Cov(X,Y)=0 → \(Var(X+Y)=Var(X)+Var(Y)\).

---

## 7️⃣ Quick Reference Formulas

| Concept | Formula | Notes |
|----------|----------|-------|
| Joint probability | \(P(X,Y)\) | table of combined outcomes |
| Marginal | \(\sum P(X,Y)\) | sum over other var |
| Independence | \(P(X,Y)=P(X)P(Y)\) | or \(E[XY]=E[X]E[Y]\) |
| Covariance | \(E[XY]−E[X]E[Y]\) | can be ± |
| Pearson ρ | \(Cov(X,Y)/√(Var(X)Var(Y))\) | linear dependence (−1→1) |
| Kendall τ | rank-based measure | monotonic dependence |

---

## 🧠 Key Takeaways
- Marginals are derived by summing joint probabilities.  
- Independence simplifies joint → product of marginals.  
- Covariance and correlation quantify dependence.  
- Pearson = linear relationship; Kendall τ = monotonic relationship.  
- Variance of sum includes covariance term if variables dependent.

---

# 🎯 DSCI 551 Lecture 4 — Conditional Probability & Independence

Clear, practical refresher on conditional probabilities, conditional expectations, and conditional independence.

---

## 1️⃣ Univariate Conditional Probability

**Definition**

\[
P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0
\]

Interpretation → event B becomes the new sample space.

---

### Example: Ship Length of Stay (L)

| L (days) | P(L) |
|-----------|------|
| 1 | 0.25 |
| 2 | 0.35 |
| 3 | 0.20 |
| 4 | 0.10 |
| 5 | 0.10 |

**Find:** distribution of L given L > 2

\[
P(L=l \mid L>2)=\frac{P(L=l)}{P(L>2)}
\]
\[
P(L>2)=0.2+0.1+0.1=0.4
\]

| L | P(L=l \| L>2) |
|---|----------------|
| 3 | 0.50 |
| 4 | 0.25 |
| 5 | 0.25 |

→ conditional distribution must still sum to 1 (renormalized).

---

## 2️⃣ Conditional Probability Distributions (Multivariate)

For discrete random variables X and Y:

\[
P(X=x \mid Y=y) = \frac{P(X=x, Y=y)}{P(Y=y)}
\]

A proper PMF:
\[
\sum_x P(X=x \mid Y=y) = 1
\]

---

### Example: Cargo Ships (L = length of stay, G = gangs)

Conditional on L = 1:

\[
P(G=g \mid L=1) = \frac{P(G=g, L=1)}{P(L=1)}
\]

| G | P(G=g \| L=1) |
|---|----------------|
| 1 | 0.0068 |
| 2 | 0.1701 |
| 3 | 0.4988 |
| 4 | 0.3242 |

✅ Check: probabilities sum to 1.

---

### Conditional Expectation

For discrete X | Y=y:

\[
E(X \mid Y=y)=\sum_x x P(X=x\mid Y=y)
\]

**Example:**  
\(E(G)=2.3\);  
\(E(G \mid L=1)=3.14\) ⇒ expected # of gangs increases when stay = 1 day.

---

## 3️⃣ Independence & Conditional Independence

### Independence
\[
P(X=x, Y=y)=P(X=x)\,P(Y=y)
\]
\[
P(Y=y\mid X=x)=P(Y=y)
\]

→ knowing X does not change belief about Y.

---

### Conditional Independence
X and Y are conditionally independent given Z if:
\[
P(X=x, Y=y \mid Z=z)=P(X=x \mid Z=z)\,P(Y=y \mid Z=z)
\]

---

#### Example: DSCI 551 Grades

- L = Lab grade (low/high)  
- Q = Quiz grade (low/high)  
- S = Statistics major (yes/no)

Without conditioning → L and Q not independent.  
Given S = yes or S = no → conditionally independent.

So:  
> Lab and quiz grades become independent *after conditioning* on whether the student is a Statistics major.

---

## 4️⃣ Law of Total Expectation

A marginal mean can be reconstructed from conditional means:

\[
E[Y] = \sum_x E[Y\mid X=x]\,P(X=x)
\]
or equivalently  
\[
E[Y]=E_X[E[Y\mid X]]
\]

**Example (ships):**

| L | E(G | L) | P(L) | Product |
|---|-----------|-------|----------|
| 1 | 3.14 | 0.25 | 0.785 |
| 2 | 2.41 | 0.35 | 0.844 |
| 3 | 1.92 | 0.20 | 0.383 |
| 4 | 1.60 | 0.10 | 0.160 |
| 5 | 1.27 | 0.10 | 0.127 |

\[
E(G)=\sum E(G\mid L)\,P(L)=2.3
\]

---

## 5️⃣ Key Takeaways

- **Conditional probability:** restrict sample space → renormalize.  
- **Conditional distribution:** table or formula form; sums to 1.  
- **Conditional expectation:** expected value under new condition.  
- **Independence:** joint = product of marginals.  
- **Conditional independence:** joint conditional = product of conditionals.  
- **Law of Total Expectation:** marginal = weighted average of conditionals.

---





