# P&O3 Python and image processing guidelines
The purpose of this project/tutorial is to help you get going with Python and image processing done in Python.

## Prerequisites

- Have Python >= 3.6.5 installed.
- Clone the repository on your local machine.
- Install `virtualenv` by running `pip install virtualenv`. A [good video](https://www.youtube.com/watch?v=N5vscPTWKOk&feature=youtu.be&t=112) about what virtual environments are and `virtualenv` in particular. Make sure to go through the video before proceeding.
- Create a new virtual environments for this project by running `virtualenv p_and_o_3`.
- To activate the virtual environments run `source p_and_o_3/bin/activate`. Now, you are inside your new Python virtual environment. 
- To install all the required packages run `pip install -r requirements.txt`. If you did everything successfully up to this point you have an identical virtual environment as I have on my local machine.
- In case you want to exit the virtual environment run `deactivate`.
- Finally, if you want to see an alternative practice (The one I use to deal with my Python dependencies and virtual environments go to section [virtual environments](#ve)).

## Notebooks

The Jupyter notebooks `tutorial_python.ipynb` and `tutorial_image_processing.ipynb` give you a brief overview of Python and image processing done in Python accordingly. 


For any questions, or if you have things that you think are missing, feel free to reach out to me on
[gorjan.radevski@esat.kuleuven.be](mailto:gorjan.radevski@esat.kuleuven.be). For those interested, the sections below go through some Python practices that I try to stick to when working on my projects.


## Folder structure
Python files that are in the top most level in the sources directory are treated as scripts (should implement a `__main__` method) and can be run (using `python script1.py`). All other python files that are further down in the sources directory should be packed as packages and imported in the scripts as modules. An example is presented below.

```
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

## Docstrings and static typing
Improved readability of the code will be achieved if you use Docscrings. On the other hand, static typing helps more than just improving readability and provides usefull warning messages if something seems off. One option to use is the Google docstring format and the typing library included by default in Python. An example is presented below.

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

## Logging vs printing

The only scenario where ```print("Something")``` should be done is in the top level python files. Otherwise, logging should be used. The logging is included in the default
Python library. The logging package has a lot of useful features:

 - Easy to see where and when (even what line no.) a logging call is being made from.
 - You can log to files, sockets, pretty much anything, all at the same time.
 - You can differentiate your logging based on severity.
 - Print doesn't have any of these.

[Stackoverlow source](https://stackoverflow.com/questions/6918493/in-python-why-use-logging-instead-of-print) about printing vs logging.

## Virual environments {#ve}

- In the future I would suggest that you install [Poetry](https://poetry.eustace.io/). Poetry helps you manage your virtual enviroments in Python and serves as a dependency resolver. Assuming that you installed `poetry` for this project, navigate to the cloned directory and run `poetry install`. Then, `poetry` will set up an identical virtual environment for you as the one I have for this project. Several commands to keep in mind about `poetry`:

- `poetry add package_name` to install a package.
- `poetry remove package_name` to remove a package.
- `poetry init` to create a new project (this will set up a `pyproject.toml` file for you where all dependencies will be listed).
- `poetry lock` it will resolve all your dependencies and create a a `poetry.lock` file that you SHOULD keep in version control.
- `poetry run python script1.py` to execute a Python script using Python from inside the virtual environment.


	
