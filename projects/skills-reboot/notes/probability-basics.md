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
