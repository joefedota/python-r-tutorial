# Python for R

Some example notebooks showing translations from R fundamentals to python fundamentals.
Each chapter shows the R code you already know next to its Python equivalent, using datasets my claude had the notion you'd be familiar with (`penguins`,
`gapminder`, `nycflights13`).

No R installation is needed. The R snippets are for reference only; the Python
cells are the ones you run.

## Setup

You need three things: `git`, `uv`, and an editor.

### 1. Install uv

[uv](https://docs.astral.sh/uv/) manages both Python itself and the packages
for this project. It plays the role `renv` plays in R.

Open Terminal and run:

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Open a new terminal afterwards so `uv` is on your path.

### 2. Clone the repo and install the environment

```sh
git clone https://github.com/joefedota/python-r-tutorial.git
cd python-r-tutorial
uv sync
```

`uv sync` downloads the right Python version and every package pinned in
`uv.lock` into a `.venv/` folder inside the project. Nothing is installed
system-wide.

### 3. Open it in Positron

[Positron](https://positron.posit.co/) is Posit's successor to RStudio. It has
the same console, variables pane, data viewer and plots pane, and it runs
Python and Jupyter notebooks natively.

1. Install Positron and choose **File → Open Folder…** on `python-r-tutorial`.
2. Open `notebooks/00_orientation.ipynb`.
3. When asked for a kernel or interpreter, pick the one in `.venv`
   (Positron usually detects it on its own).

Prefer the browser? Run `uv run jupyter lab` instead.

## How to work through it

Go through `notebooks/` in order. After each chapter, try the matching notebook
in `exercises/`, then compare against `solutions/`.

| Chapter | R concepts | Python concepts |
| --- | --- | --- |
| `00_orientation` | RStudio, `library()`, `renv` | Positron, `import`, `uv` |
| `01_language_basics` | vectors, lists, 1-based indexing | lists, dicts, NumPy, 0-based indexing |
| `02_dataframes` | `data.frame`, tibble, `NA` | `DataFrame`, `Series`, the index, `NaN` |
| `03_data_wrangling` | dplyr verbs, `\|>` | pandas, method chaining |
| `04_reshape_and_join` | tidyr, `*_join()` | `melt`, `pivot`, `merge` |
| `05_plotting` | ggplot2 | seaborn, matplotlib |
| `06_stats_and_models` | `lm()`, `glm()` | statsmodels, scikit-learn |
| `07_gotchas` | copy-on-modify | references, mutability, index alignment |

`cheatsheet.md` is a quick R ↔ Python lookup table.

## Layout

```
data/                 example datasets as CSV
notebooks/            the tutorial chapters
exercises/            practice notebooks, one per chapter
solutions/            worked solutions, one per chapter
cheatsheet.md         R ↔ Python lookup table
pyproject.toml        package list (like DESCRIPTION)
uv.lock               exact pinned versions (like renv.lock)
```

## Adding a package

```sh
uv add polars
```

This is the equivalent of `install.packages()` followed by `renv::snapshot()`:
it installs the package and records it in `pyproject.toml` and `uv.lock`.

## Data sources

- `penguins.csv`: [palmerpenguins](https://allisonhorst.github.io/palmerpenguins/)
- `gapminder.csv`: the [gapminder](https://github.com/jennybc/gapminder) R package
- `flights.csv`, `airlines.csv`, `airports.csv`:
  [nycflights13](https://github.com/tidyverse/nycflights13). `flights.csv` is a
  random 10,000-row sample of the full 336,776-row table.
