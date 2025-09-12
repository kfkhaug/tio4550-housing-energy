# Project Structure Explained

This document outlines the structure of our project. It's designed to be a standard, maintainable layout, making it easier to maintain the codebase as it expands.

## High-Level Overview

The main idea is to keep different parts of the project separate:
*   **`data/`**: All data files.
*   **`notebooks/`**: Experimental code and analysis.
*   **`src/`**: Reusable, production-quality Python code.
*   **`report/`**: The final report and any figures.
*   **`docs/`**: Project documentation.

## Directory Tree

Here is a simplified view of our project's folder structure:

```
tio4550-housing-energy/
├── .gitignore             # Specifies files and folders for Git to ignore.
├── data/
│   ├── 1_raw/             # Original, immutable data. Do not edit these files.
│   ├── 2_interim/         # Intermediate data that has been transformed.
│   └── 3_processed/       # The final, clean data sets for analysis and modeling.
├── docs/                  # Project documentation (like this file and dev_setup.md).
├── notebooks/             # Jupyter notebooks for EDA, prototyping, and experiments.
│   ├── 1_exploratory_data_analysis.ipynb
│   ├── 2_data_processing.ipynb
│   ├── 3_feature_engineering.ipynb
│   └── 4_modeling.ipynb
├── report/
│   ├── figures/           # Generated plots, charts, and figures for the report.
│   └── manuscript/        # Final report (LaTeX or Markdown files).
├── src/                   # Project source code, structured as an installable package.
│   └── tio4550_housing_energy/
│       ├── __init__.py    # Makes `tio4550_housing_energy` a package.
│       ├── data_processing/         # Code for cleaning and preparing data.
│       ├── exploratory_data_analysis/ # Code for initial data exploration.
│       ├── feature_engineering/     # Code for creating new features.
│       ├── modeling/                # Code for training and evaluating models.
│       └── utils/                   # Helper functions used across the project.
├── pyproject.toml         # Project metadata and dependencies for `uv`.
├── README.md              # The project front page.
└── uv.lock                # Pins exact versions of all dependencies for reproducibility.
```

## The `src` Folder: Our Project's Python Package

The `src` folder is the heart of our project's reusable code. It's not just a collection of scripts; it's a proper Python package named `tio4550_housing_energy`.

### Why a Package?

1.  **Clean Notebooks**: Instead of having huge cells of complex functions in our notebooks, we can define them once in the `src` package and import them. This keeps the notebooks focused on the narrative of our analysis.
2.  **Reusability**: Functions for cleaning data, creating features, or training models can be easily reused across different notebooks or scripts.
3.  **Easy Imports**: After setting up the project with `uv pip install -e .` (as described in `dev_setup.md`), we can import our code from anywhere in the project, just like we would import `pandas` or `numpy`.

### How to Use It

The `tio4550_housing_energy` package is organized into sub-packages for different tasks:

*   `exploratory_data_analysis`: Functions for performing EDA.
*   `data_processing`: Functions for cleaning and preparing raw data.
*   `feature_engineering`: Functions for creating new features.
*   `modeling`: Classes and functions for training and evaluating models.
*   `utils`: Common helper functions.

To use a function in a notebook, you simply import it. For example, to use the test function from the `utils` module, you would write:

```python
import tio4550_housing_energy.utils as u

# This will now work!
u.a_test_function()
```

Similarly, if you write a data cleaning function in `/src/tio4550_housing_energy/data_processing/data_processing.py` and import it in `/src/tio4550_housing_energy/data_processing/__init__.py`, you can use it in your notebook like this:

```python
import tio4550_housing_energy.data_processing as dp

# Assuming you have a function called 'clean_my_data'
cleaned_df = dp.clean_my_data(raw_df)
```

This structure helps us write modular, testable, and clean code.