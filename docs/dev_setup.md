# HowTo use this repo

## Uv
[Uv](https://docs.astral.sh/uv/) is a tool for managing the python version and the packages you use. It completely relpaces pip. **Never use pip**, that will break the project.

The reason it is genious is that normally, each person working on a project may have different versions of python and therefore experience different bugs or functionality. Having the same python version removes this problem.

In the same vein, having differring package verisons also introduces bugs for large projects. Uv handles all of this.

### Setup

1. Begin by installing uv following [this](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer) guide. On Windows 11, you need to run this command: 
    ```
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    ```

2. After installing uv, open the project folder in VS Code and press ```Ctrl + J``` to start a terminal thats already navigated to the working folder. This command is very nice to use by default every time you need a terminal.

3. Enter ```uv sync``` in the terminal. This will automatically download the specific python version and packages.

4. Enter ```uv venv``` in the terminal. This will create a .venv folder that only exists for you on your PC. It contains the virtual environment for this specific python project on your PC.

5. Set the python interpreter used by VS Code to be the same as the one used by the virtual environment that should have been created. The path should be something like ```tio4550-housing-energy``` and have ```.venv``` in the name. This ensures that you use the python setup used only by this project.

### Commands you should know

- **```uv sync```** reads the uv config files in the repo and automatically installs what you need to be up to date. Use this if you know that other project members have added or removed packages that the code now relies on.
- **```uv add [package]```** installs a package. For example ```uv add scikit-learn pandas``` has already been been used to install the two packages pandas and scikit-learn. This command replaces the old ```pip install [package]``` way of doing things. From now on, never use pip. Instead rely on uv add.
- **```uv remove [package]```** is used to uninstall packages.

## Ruff
[Ruff](https://docs.astral.sh/ruff/#testimonials) re-formats code to use the same style and automatically fixes common errors. This ensures both that easily overseen errors are corrected immediately and that everyone can read your the entire codebase. Ruff should be run each time you are done editing a file.

I have set it to automatically run for all files whenever you use git commit. The result should be shown in the terminal. It should also be installed automatically when you run ```uv sync```, but i advise you to also install the VS Code extension for it that can be found [here](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff).

If you want to run it manually, use any of these:
```
# Lint files in `path/to/code`. #
ruff check [path/to/code/]
# Eg. ruff check main.py

# Lint files in the current directory. #
ruff check

# Lint files in the current directory and fix any fixable errors. #
ruff check --fix

# Lint files in the current directory and re-lint on change. #
ruff check --watch
```

I don't have any experience using this, so it may bring problems in the beginning. Still, try to research how to fix the problem before giving up on the tool, it is very powerful.

## Ty
[Ty](https://docs.astral.sh/ty/) is a bleeding edge type checker. Meaning that is so new that it is still in alpha, and that it supposed to catch runtime errors before running the code. Ty should be used each time you are done editing a file.

Remember using Java how it would complain if it saw that inputs to the code weren't compatible further along the code? It basicly implements this in python.

Begin by installing [this](https://marketplace.visualstudio.com/items?itemName=astral-sh.ty) extension in VS Code. It is also installed automatically when you run ```uv sync```, but my impression is that the extension works best.

Since Ty is so new, Chat can't help explain how to use it. Instead, resort to [this](https://docs.astral.sh/ty/reference/cli/#ty-help) list of commands. Most commonly, you will want to run ```ty ckeck [path/to/code/]``` in order check the specific file you are working on.