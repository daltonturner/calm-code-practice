# Lesson Notes

## Intro
If you are working on multiple projects, you should concern yourself with dependencies. 

> A virtual environment is a Python environment such that the Python interpreter, libraries and scripts installed into it are isolated from those installed in other virtual environments, and (by default) any libraries installed in a “system” Python, i.e., one which is installed as part of your operating system.[^1]

[^1]: [Creation of virtual environments](https://docs.python.org/3/library/venv.html)


## Multiple Pythons
You can find out where a python executable is running from by executing one of the following commands in a Terminal window on Mac:
> `which python`

> `which python3.x`

## Installation
You can install virtualenv for a given python version by running the following command:
> `python3.x -m pip install virtualenv`

You can create a new virtual environment named `file_name` by running:
> `python3.x -m virtualenv file_name`

## Virtualenv
To use a newly created virtual environment, run the following command:
> `source file_name/bin/activate`

The `source` command above references the `activate` bash script, which ensures that when you run the `python` command in an active virtual environment, you automatically reference the virtual environment's version of python, not your system installation. 

To deactivate a virtual environment, run the following command:
> `deactivate`

## Pip
To install a python package in an *active* virtual environment, run the following command after selecting a package version, or omit the version option altogether:
> `python -m pip install package_name==0.00.0`

It is important that the virtual environment be active in the step listed above to be sure the python command references the intended version of Python.

You can run the following command to check all of the dependencies and their versions within a virtual environment:
> `python -m pip freeze`

This command has the option to add `| grep package_name` to only display the package and version you're interested in. 

You can also install a list of requirements from a file by running:
> `python -m pip install -r requirements.txt`

The line above necessitates having a `requirements.txt` file in the current file path.

## Common Mistakes
By not assuming a certain python version and omitting the `python -m` portion of a command in a virtual environment, you can be sure you aren't referencing a package that is installed outside of your virtual environment (in another virtual environment, or at the system level).

Deactivating a virtual environment after installing a dependency ensures that when you re-source and activate the virtual environment you will properly reference the virtual environment's new dependency list. 



