# Pandas, NumPy, Functions & Classes — Quick Reference

A compact refresher on the Python data-science stack and core programming patterns.

---

## 🔹 Pandas DataFrames

```python
import pandas as pd

# Read / Write
df = pd.read_csv("data.csv")       # also pd.read_excel()
df.to_csv("out.csv", index=False)

# Inspect
df.head(); df.tail(); df.shape
df.describe(include="all")

# Access
df["col"]                 # Series
df[["a","b"]]             # multiple cols
df.loc[2, "col"]          # by label
df.iloc[2, 0]             # by integer index

Add / Remove / Sort
df["new"] = df["a"] * 2
df.drop(columns=["unneeded"], inplace=True)
df.sort_values("a", ascending=False)

🔹 Filtering & Cleaning
df[df["a"] > 0]
df.query("a > 0 and b == 'yes'")

# Missing data
df.dropna(subset=["a"])
df["a"].fillna(df["a"].mean(), inplace=True)

# Rename
df.rename(columns={"old":"new"}, inplace=True)

df[df["a"] > 0]
df.query("a > 0 and b == 'yes'")

# Missing data
df.dropna(subset=["a"])
df["a"].fillna(df["a"].mean(), inplace=True)

# Rename
df.rename(columns={"old":"new"}, inplace=True)

Reshape / Tidy
pd.melt(df, id_vars="id", var_name="feature", value_name="value")
df.pivot(index="id", columns="feature", values="value")
df.pivot_table(values="val", index="group", aggfunc="mean")


🔹 Strings & Regex
# Python
s = "Galaxy"
s.find("l"); s.replace("a","@"); "-".join(["A","B"])

# Pandas vectorized
df["col"].str.lower()
df["col"].str.contains("pattern", regex=True)
df["col"].str.extract(r"(\d{4})")

🔹 Dates & Times
pd.Timestamp("2020-01-01")
pd.date_range("2020-01-01", periods=7, freq="D")

df["date"] = pd.to_datetime(df["date"])
df["year"] = df["date"].dt.year
df.set_index("date").resample("M").mean()

🔹 Combine / Aggregate
pd.concat([df1, df2], axis=0)
df1.merge(df2, on="id", how="left")

# Apply / Map
df["new"] = df["a"].map(lambda x: x**2)
df.applymap(lambda x: str(x).upper())

# Grouping
df.groupby("cat")["val"].agg(["mean","max"])

🔹 NumPy Basics
import numpy as np

a = np.arange(6).reshape(2,3)
a[0,1]; a[:,1]
a.sum(axis=0); a.mean()
np.linspace(0,1,5)
np.random.rand(2,3)

# Broadcasting
a + np.array([1,2,3])

🔹 Python Core Patterns
# Lists / Dicts / Sets
lst = [1,2,3]; d = {"a":1, "b":2}
lst.append(4); d["c"] = 3

# Comprehensions
squares = [x**2 for x in range(5)]
doubled = {k:v*2 for k,v in d.items()}

# Loops & Conditionals
for x in lst:
    if x % 2 == 0:
        print(x)

🔹 Functions & Testing
def area(r, pi=3.14):
    """Return circle area."""
    assert r >= 0, "radius must be non-negative"
    return pi * r**2

# Lambda
f = lambda x: x**2

# Error handling
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print("Error:", e)

🔹 Classes & OOP Short-Form
class Circle:
    pi = 3.14                      # class attribute
    def __init__(self, r):
        self.r = r                 # instance attribute
    def area(self):
        return Circle.pi * self.r**2

class ColoredCircle(Circle):
    def __init__(self, r, color):
        super().__init__(r)
        self.color = color

🔹 Code Style Tools
flake8 script.py     # linter – find style issues
black script.py      # autoformat code




