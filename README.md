# P&O3 Python and image processing guidelines

This repository is intended to provide basic introduction and guidelines to the students of the P&O3 project at KU Leuven. These guidelines are meant to help you get going with Python and image processing.

## Prerequisites

- Have Python >= 3.6.5 installed.
- Clone the repository on your local machine.
- Install `virtualenv` by running `pip install virtualenv`. A [good video](https://www.youtube.com/watch?v=N5vscPTWKOk&feature=youtu.be&t=112) about what virtual environments are and `virtualenv` in particular. Make sure to go through the video before proceeding.
- Create a new virtual environment for this project by running `virtualenv p_and_o_3`.
- To activate the virtual environment run `source p_and_o_3/bin/activate`. Now, you are inside your new Python virtual environment. 
- To install all the required packages run `pip install -r requirements.txt`. If you did everything successfully up to this point you have an identical virtual environment as I have on my local machine.
- In case you want to exit the virtual environment run `deactivate`.
- Finally, if you want to see an alternative practice (The one I use to deal with my Python dependencies and virtual environments) go to section [virtual environments](#Virtual-environments).

## Notebooks

The Jupyter notebook `python_image_processing.ipynb` in the `notebooks/` directory gives you a brief overview of Python and image processing. To run the notebook, from inside your virtual environment run `jupyter notebook`. This will open `jupyter` in your browser and from there you can navigate to the `notebooks/` directory and open the `python_image_processing.ipynb` notebook.

## Final remarks

For any questions or clarifications feel free to reach out to me on
[gorjan.radevski@esat.kuleuven.be](mailto:gorjan.radevski@esat.kuleuven.be). If you have any suggestion that you think might be usefull for other students as well and you think it needs to be added to the repository feel free to create an Github issue (sending me an email will suffice as well but and issue is preferred). For those interested, the sections below go through some Python practices that I try to stick to when working on my projects.

### Folder structure

Python files that reside at the top-most level in the sources directory `src/` are treated as scripts (should implement a `__main__` method) and can be executed (e.g `python script.py`). All other Python files that are further down in the sources directory should be packed as packages and imported as modules. An example is presented below.

```
data/
notebooks/
src/
 |
  -- script1.py
  -- script2.py
  -- package1/
        |
         -- module1.py
         -- module2.py
  -- package2/
        |
         -- module3.py
```

### Docstrings and static typing

Improved readability of the code is achieved if you use Docstrings. On the other hand, static typing helps more than just improving readability and provides useful warning messages if something seems off. One option is to use the Google docstring format and the typing library included by default in Python. An example is presented below.

```
from typing import List, Dict

def function(arg1: List[int], arg2: str) -> Dict[str, int]:
    """Summary line of the function.

    Extended description of the function if needed.

    Args:
        arg1: Description of the first input argument.
        arg2: Description of the second input argument.

    Returns:
        What the function returns

    """
    start_of_code += 1
    return_dict = {"some_var": start_of_code}

    return return_dict
```

Furthermore the `typing` library supports all kind of types such as ```Dict```, ```Tuple```, ```Set```, ```Union``` and so on.

### Logging vs printing

The only scenario where ```print("Something")``` should be done is in the Python scripts. Otherwise, logging should be used. The logging is included in the default
Python library. The logging package has a lot of useful features:

 - Easy to see where and when (even what line no.) a logging call is being made from.
 - You can log to files, sockets, pretty much anything, all at the same time.
 - You can differentiate your logging based on severity.
 - Print doesn't have any of these.

[Stackoverlow source](https://stackoverflow.com/questions/6918493/in-python-why-use-logging-instead-of-print) about printing vs logging.

### Formatting and linting

I would suggest that you all install [Black](https://github.com/psf/black) and [Flake8](https://github.com/pycqa/flake8/). Black will format your code for you while Flake8 will check your code against coding style (PEP8), check for programming errors (like “library imported but unused” etc. This is important since you are working in a team, i.e., you want to have your code be identically formated across team members and properly stylized. Black and Flake8 will do this for you.

### Virtual environments

In the future I would suggest that you install [Poetry](https://poetry.eustace.io/). Poetry helps you manage your virtual environments in Python and serves as a dependency resolver. In case you decide to use Poetry for this project, let me know and I will push the necessary files for you to replicate the virtual environment with Poetry. Assuming that you installed `poetry` for this project and I pushed the files, navigate to the cloned directory and run `poetry install`. Then, `poetry` will set up an identical virtual environment as the one I have for this project. Several commands to keep in mind about `poetry`:

- `poetry add package_name` to install a package.
- `poetry remove package_name` to remove a package.
- `poetry init` to create a new project (this will set up a `pyproject.toml` file for you where all dependencies will be listed).
- `poetry lock` it will resolve all your dependencies and create a `poetry.lock` file that you SHOULD keep in version control.
- `poetry run python script1.py` to execute a Python script using Python from inside the virtual environment.

### Code edittor

I personally use VS Code, and I suggest that you should use it as well. You can download and follow the instructions for installing VS Code from [here](https://code.visualstudio.com/Download). After installing VS Code, these are some nice extensions that will help you maintain a nice user experience.

- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python); if you use VS Code for Python development than you must have it.
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance); a language server for Python in VS Code. [Here](https://devblogs.microsoft.com/python/announcing-pylance-fast-feature-rich-language-support-for-python-in-visual-studio-code/) you can read about the features it provides.
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens); basically improved Git features for VS Code.
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) or [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint); for writting and editting markdown files e.g., READMEs.
- [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow); clearer indentation.
- Any others?
