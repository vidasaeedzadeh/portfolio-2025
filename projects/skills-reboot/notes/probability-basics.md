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


