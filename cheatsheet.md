# R ↔ Python cheatsheet

Assumes `import numpy as np` and `import pandas as pd`.

## Language

| R | Python |
| --- | --- |
| `x <- 5` | `x = 5` |
| `c(1, 2, 3)` | `[1, 2, 3]` or `np.array([1, 2, 3])` |
| `list(a = 1, b = 2)` | `{"a": 1, "b": 2}` |
| `x[1]` (first element) | `x[0]` |
| `x[2:4]` | `x[1:4]` |
| `length(x)` | `len(x)` |
| `TRUE`, `FALSE`, `NULL` | `True`, `False`, `None` |
| `&`, `\|`, `!` | `and`, `or`, `not` (scalars); `&`, `\|`, `~` (arrays) |
| `x %in% y` | `x in y` (scalar); `s.isin(y)` (Series) |
| `paste0("a", "b")` | `"a" + "b"` or `f"{a}{b}"` |
| `function(x) x + 1` | `lambda x: x + 1` |
| `sapply(x, f)` | `[f(i) for i in x]` |
| `library(pkg)` | `import pkg` |
| `pkg::fn()` | `pkg.fn()` |
| `?fn` | `help(fn)` or `fn?` |

## Data frames

| R | Python |
| --- | --- |
| `read_csv("f.csv")` | `pd.read_csv("f.csv")` |
| `head(df)` | `df.head()` |
| `glimpse(df)` / `str(df)` | `df.info()` |
| `summary(df)` | `df.describe()` |
| `dim(df)` | `df.shape` |
| `names(df)` | `df.columns` |
| `df$col` | `df["col"]` |
| `filter(df, x > 1)` | `df[df["x"] > 1]` or `df.query("x > 1")` |
| `select(df, a, b)` | `df[["a", "b"]]` |
| `mutate(df, z = x + y)` | `df.assign(z=df["x"] + df["y"])` |
| `arrange(df, desc(x))` | `df.sort_values("x", ascending=False)` |
| `group_by(df, g) \|> summarise(m = mean(x))` | `df.groupby("g").agg(m=("x", "mean"))` |
| `count(df, g)` | `df["g"].value_counts()` |
| `distinct(df)` | `df.drop_duplicates()` |
| `rename(df, new = old)` | `df.rename(columns={"old": "new"})` |
| `left_join(a, b, by = "k")` | `a.merge(b, on="k", how="left")` |
| `bind_rows(a, b)` | `pd.concat([a, b])` |
| `pivot_longer()` | `df.melt()` |
| `pivot_wider()` | `df.pivot()` |
| `is.na(x)` | `s.isna()` |
| `drop_na(df)` | `df.dropna()` |

## Plotting and models

| R | Python |
| --- | --- |
| `ggplot(df, aes(x, y)) + geom_point()` | `ggplot(df, aes("x", "y")) + geom_point()` (plotnine) |
| `lm(y ~ x, data = df)` | `smf.ols("y ~ x", data=df).fit()` |
| `summary(model)` | `model.summary()` |
| `predict(model, newdata)` | `model.predict(newdata)` |
