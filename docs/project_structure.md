# An Explanation for the Project Folder Strucutre

## Tree View of the project

tio4550-housing-energy/
├── .gitignore
├── data/
│   ├── 1_raw/             # Original, immutable data. Do not edit.
│   ├── 2_interim/         # Intermediate data that has been transformed.
│   └── 3_processed/       # The final, clean data sets for analysis and modeling.
├── docs/                  # Project documentation for internal use.
├── notebooks/             # Jupyter notebooks for EDA, prototyping, and experiments.
├── reports/
│   ├── figures/           # Generated plots, charts, and figures.
│   └── manuscript/        # Your final report (LaTeX or Markdown files).
├── src/                   # The main project source code.
│   ├── __init__.py        # Makes src a Python package that can be imported into other files.
│   ├── data_processing.py # Scripts for downloading and cleaning data.
│   ├── feature_engineering.py # Scripts for creating features (e.g., LLM calls).
│   └── modeling.py        # Scripts for training and evaluating models.
├── pyproject.toml         
├── README.md              # The project front page.
└── uv.lock                


## What is the "src" Folder?

By existing in a directory, __init__.py tells Python: "Treat this folder as a package of code modules." src is just a common name for such folder full of reusable "source code."

You can now write code in other files (like your notebooks) that says from src.data_processing import clean_data_function, and Python will know where to find it.