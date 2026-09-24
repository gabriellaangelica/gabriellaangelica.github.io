# Gabriella Angelica Jemima Hasian — DSCI 521 Computational Blog

This repository contains my DSCI 521 Quarto website and computational blog posts.

## 1. Install the Required Software

Before starting, install:

- Git
- Quarto
- Python 3.14
- `uv`
- R
- `renv`

## 2. Clone the Repository

Open **Terminal** and run:

```bash
git clone https://github.com/gabriellaangelica/gabriellaangelica.github.io.git
```

Wait until the repository finishes cloning.

## 3. Enter the Repository

In **Terminal**, run:

```bash
cd gabriellaangelica.github.io
```

All commands below should be run from this repository directory unless stated otherwise.

Check that you are in the correct directory:

```bash
pwd
```

The path should end with:

```text
gabriellaangelica.github.io
```

## 4. Set Up the Python Environment

Make sure you are still inside the repository directory.

Run:

```bash
unset VIRTUAL_ENV
```

Then run:

```bash
uv sync
```

Wait until the installation finishes.

Check the Python version:

```bash
uv run python --version
```

The project uses Python 3.14.

## 5. Set Up the R Environment

Make sure you are still inside the repository directory.

In **Terminal**, start R:

```bash
R
```

Inside the R console, run:

```r
renv::restore(prompt = FALSE)
```

Wait until the restoration finishes.

Then check the environment:

```r
renv::status()
```

The expected result is:

```text
No issues found -- the project is in a consistent state.
```

Exit R:

```r
q()
```

When asked:

```text
Save workspace image?
```

type:

```text
n
```

You should now be back in Terminal.

## 6. Render the Website

Make sure you are in the repository directory.

Run:

```bash
unset VIRTUAL_ENV
```

Then render the website:

```bash
uv run quarto render
```

Wait until the rendering finishes.

A successful render should end with something similar to:

```text
Output created: docs/index.html
```

## 7. Verify the Website

Run:

```bash
test -f docs/index.html && echo "Website built successfully"
```

You should see:

```text
Website built successfully
```

Check the Python post:

```bash
test -f docs/posts/penguin-python/index.html && echo "Python post built successfully"
```

Check the R post:

```bash
test -f docs/posts/penguin-r/index.html && echo "R post built successfully"
```

## 8. Preview the Website

From the repository root, run:

```bash
uv run quarto preview
```

Quarto will display a local URL.

Open that URL in your browser.

Check that:

- Home works
- About works
- Blog works
- Python post works
- R post works
- Navigation works
- Figures are displayed
- Code and output are displayed

To stop the preview server, press:

```text
Ctrl+C
```

## 9. Data Source

Both computational posts use the Palmer Penguins dataset.

Data source:

https://allisonhorst.github.io/palmerpenguins/

The dataset is downloaded from its public GitHub source during rendering.

Therefore, an internet connection is required when running:

```bash
uv run quarto render
```

## 10. Reproducible Environment Files

The Python environment is defined by:

```text
pyproject.toml
uv.lock
.python-version
```

The R environment is defined by:

```text
renv.lock
.Rprofile
renv/
```

The Quarto website configuration is defined by:

```text
_quarto.yml
```

## 11. Complete Fresh-Clone Workflow

For a completely fresh rebuild, follow these steps in order.

### Terminal

```bash
git clone https://github.com/gabriellaangelica/gabriellaangelica.github.io.git
cd gabriellaangelica.github.io
unset VIRTUAL_ENV
uv sync
R
```

### R

```r
renv::restore(prompt = FALSE)
renv::status()
q()
```

When asked to save the workspace, enter:

```text
n
```

### Terminal

```bash
cd gabriellaangelica.github.io
unset VIRTUAL_ENV
uv run quarto render
```

Verify the build:

```bash
test -f docs/index.html && echo "Website built successfully"
```

Preview the website:

```bash
uv run quarto preview
```

The rebuilt website is generated in:

```text
docs/
```
