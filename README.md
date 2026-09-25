# Gabriella Angelica Jemima Hasian — DSCI 521 Computational Blog

This repository contains my DSCI 521 Quarto website and computational blog posts.

The website contains:

- an R computational post using the Palmer Penguins dataset;
- a Python computational post using the Palmer Penguins dataset; and
- a bonus post demonstrating R and Python working together in the same Quarto document using the `mtcars` dataset.

The website is built with Quarto and published using GitHub Pages.

## 1. Install the Required Software

Before starting, install the following software:

- Git
- Quarto 1.10.18
- Python 3.14
- uv 0.12.5
- R 4.6.1

The R environment is managed by `renv`. The project contains the files needed to restore the R environment.

The Python environment is managed by `uv`.

## 2. Clone the Repository

Open **Terminal** and run:

    git clone https://github.com/gabriellaangelica/gabriellaangelica.github.io.git

Wait until the repository finishes cloning.

## 3. Enter the Repository

In **Terminal**, run:

    cd gabriellaangelica.github.io

All commands below should be run from the repository root unless stated otherwise.

Check that you are in the correct directory:

    pwd

The path should end with:

    gabriellaangelica.github.io

## 4. Set Up the Python Environment

Make sure you are inside the repository root.

First, clear any inherited Python virtual environment:

    unset VIRTUAL_ENV

Restore the project Python environment:

    uv sync

This restores the Python environment using the dependencies recorded in `pyproject.toml` and `uv.lock`.

Check the Python version:

    uv run python --version

The project uses Python 3.14.

## 5. Set Up the R Environment

Make sure you are still inside the repository root.

Start R from **Terminal**:

    R

Inside the R console, restore the project environment:

    renv::restore(prompt = FALSE)

Then check the environment:

    renv::status()

The expected result is:

    No issues found -- the project is in a consistent state.

Exit R:

    q()

When asked:

    Save workspace image?

enter:

    n

You should now be back in Terminal.

The R environment is defined by:

    renv.lock
    .Rprofile
    renv/activate.R

The R package library itself is not committed to the repository.

## 6. Render the Website

Make sure you are in the repository root.

Clear any inherited virtual environment:

    unset VIRTUAL_ENV

Render the entire Quarto website:

    uv run quarto render

A successful render should end with something similar to:

    Output created: docs/index.html

The rendered website is generated in:

    docs/

## 7. Verify the Rendered Website

Check that the main website was built:

    test -f docs/index.html && echo "Website built successfully"

Expected output:

    Website built successfully

Check the Python post:

    test -f docs/posts/penguin-python/index.html && echo "Python post built successfully"

Check the R post:

    test -f docs/posts/penguin-r/index.html && echo "R post built successfully"

Check the R + Python bonus post:

    test -f docs/posts/bonus-r-python/index.html && echo "Bonus post built successfully"

The expected outputs are:

    Python post built successfully
    R post built successfully
    Bonus post built successfully

## 8. Preview the Website

From the repository root, run:

    uv run quarto preview

Quarto will display a local URL.

Open that URL in a browser and check that:

- Home works
- About works
- Blog works
- Python post works
- R post works
- Bonus R + Python post works
- Navigation works
- Figures are displayed
- Code is displayed
- Code output is displayed
- Figure captions are displayed

To stop the preview server, press:

    Ctrl+C

## 9. Data Sources and Network Requirements

### Palmer Penguins

The R and Python penguin posts use the Palmer Penguins dataset.

Data source:

https://allisonhorst.github.io/palmerpenguins/

The penguin data are read from the public GitHub source during rendering.

Therefore, an internet connection is required when rendering the penguin posts and running:

    uv run quarto render

### mtcars

The bonus R + Python post uses the `mtcars` dataset.

Data source:

https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/mtcars.html

The `mtcars` dataset is included in R's `datasets` package and does not require downloading a separate data file.

The bonus post uses `reticulate` to connect R and Python within the same Quarto document. Python is configured to use the project's `.venv`.

## 10. Reproducible Environment Files

The Python environment is defined by:

    pyproject.toml
    uv.lock
    .python-version

The R environment is defined by:

    renv.lock
    .Rprofile
    renv/activate.R

The Quarto website configuration is defined by:

    _quarto.yml

The bonus R + Python post also uses `reticulate`, which is recorded in `renv.lock`.

## 11. Complete Fresh-Clone Workflow

The following is the complete workflow for rebuilding the website from a fresh clone.

### Terminal

Run:

    git clone https://github.com/gabriellaangelica/gabriellaangelica.github.io.git
    cd gabriellaangelica.github.io
    unset VIRTUAL_ENV
    uv sync
    R

### R

Inside R, run:

    renv::restore(prompt = FALSE)
    renv::status()
    q()

When asked to save the workspace, enter:

    n

### Terminal

Back in Terminal, run:

    unset VIRTUAL_ENV
    uv run quarto render

A successful build should create:

    docs/index.html

Verify the main website:

    test -f docs/index.html && echo "Website built successfully"

Verify the three computational posts:

    test -f docs/posts/penguin-python/index.html && echo "Python post built successfully"
    test -f docs/posts/penguin-r/index.html && echo "R post built successfully"
    test -f docs/posts/bonus-r-python/index.html && echo "Bonus post built successfully"

Preview the website:

    uv run quarto preview

The rebuilt website is generated in:

    docs/

## 12. Repository Structure

The main reproducibility files are located at the top level of the repository:

    gabriellaangelica.github.io/
    ├── _quarto.yml
    ├── README.md
    ├── pyproject.toml
    ├── uv.lock
    ├── .python-version
    ├── .Rprofile
    ├── renv.lock
    ├── renv/
    ├── posts/
    │   ├── penguin-python/
    │   ├── penguin-r/
    │   ├── bonus-r-python/
    │   └── first-weeks/
    └── docs/

The `docs/` directory contains the rendered website used by GitHub Pages.