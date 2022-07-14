# how to create requirements.txt python

:::section{.abstract}
In Python, a requirement.txt file is a type of file that usually stores information about all the libraries, modules, and packages in itself that are used while developing a particular project.
This article will guide us in creating the requirements.txt file and installing dependencies from the requirements.txt file. We would be looking into various ways to develop requirements.txt Python.
:::

# Need for Requirements.txt File

When working on any python project or data science project, it is essential to always work in an environment that makes your project reusable and repeatable without any issues for anyone who picks up your future project. One of the ways to solve this issue is to use a virtual environment. The reason is that there are two main types of packages and locations where your python libraries reside, and you do not need all of these packages when working on specific projects; hence it is required to know which one is needed per project to make it easier for the reproducibility. These include

* System Packages that form part of the Standard Python Library
* Site Packages (Third Party Packages) that your install using pip.

# PROBLEMS WITH THE TRADITIONAL requirements.txt FILES

Traditionally, we create a requirements.txt file by creating a virtual environment. After activating a virtual environment, we have to run the command as follows:

`pip freeze > requirements.txt`

It works fine, but the problem with this approach is that it includes all the packages that are installed via pip install <package_name> and the sub-dependency packages.
Let’s consider the following scenario:
We are working on Django based application, and the only package we have installed is Fastapi through the command :

`pip install fastapi`

However, when we tried to put all the installed packages into the requirements.txt file apart from Django, additional packages were installed internally by pip for Fastapi. To avoid this, we can use the grep command to filter for only required packages.
The command to pass the standard output from pip freeze to grep is as follows :

`pip freeze | grep -i fastapi >> requirements.txt`

> The | command is called a pipe. It is used to pipe, or transfer, the standard output from the command on its left into the standard input of the command on its right.

# what is a virtual environment?

In basic, a virtual environment is an isolated environment for python projects. It allows you to create an isolated environment for respective each python project. This makes it easier for us to manage packages and dependencies throughout projects, especially where they share the same dependencies. Various ways exist to create a virtual environment and make a requirements.txt file. Some of them are as follows :
* virtualenv
* pipenv
* Pipreqs
Once the virtual environment is created for our project, let’s see how we can use different packages to generate a requiremnets.txt file. Let’s first explore how to use the Virtualenv packages.

# Working with Virtualenv

Virtualenv is a library that allows us to execute a virtual environment. To install and work with it, you can install it through the following pip command:

`pip install virtualenv`

After installation and setting up the environment, we need to activate the environment using the source : 

`source name_of_env/bin/activate`

![](https://hackmd.io/_uploads/BJGzEhss5.png)


Once the virtual environment is activated, the name of your virtual environment will appear on the left side of the terminal. This will let you know that the virtual environment is currently active.

Now you can install dependencies related to the project in this virtual environment. For example, if you use Fastapi 0.77.1 for a project, you can install it like other packages.



## How to Get the Requirements.txt File: Using Virtualenv

To be able to get the requirements.txt file through Virtualenv, you can now use the pip freeze or pip3 freeze (python3) command as below

`pip3 freeze > requirements.txt`

![](https://hackmd.io/_uploads/Byjg4njo9.png)


# How to Get the Requirements.txt File: Using Pipenv

Pipenv is a Python packaging tool that solves common problems associated with the typical workflow using pip, virtualenv, and the good old requirements.txt. To get started with installation, we can follow the below-mentioned commands :

## Install

```python
pip install pipenv
```

![](https://hackmd.io/_uploads/S1j572soc.png)

## Install Your Packages for the project

Once we are done installing pipenv, we can effectively forget about pip since Pipenv essentially acts as a replacement in place of pip. It also introduces two new files, the Pipfile (meant to replace requirements.txt) and the Pipfile.lock (which enables deterministic builds). Pipenv uses pip and virtualenv under the hood but simplifies their usage with a single command line interface.

```bash
pipenv install package

```

## Activate Virtual Env
```bash
pipenv shell

```

## Run a script in the virtual env

`pipenv run python myscript.py`

Pipenv is a dependency manager for Python projects. It is similar to those tools if you’re familiar with Node.js’ npm or Ruby’s bundler. Pipenv is recommended as it simplifies dependency management for everyday use cases. Pipenv manages dependencies on a per-project basis.




![](https://hackmd.io/_uploads/ByapXhji9.png)

By default, it generates a Pipfile which contains packages with their mentioned versions. Whereas if we want, we can also generate a requirements.txt file following the below-mentioned command:

`pipenv -r lock >> requirements.txt`

# How to Get the Requirements.txt File: Without VirtualEnv using Pipreqs

Pipreqs is the other simple alternative that doesn’t require you to create a virtual environment first. This is quite useful and easy to operate. It generates a requirement.txt file based on the import statements of the project.
It automatically scans the python file or script for their mentioned imported libraries and then generates a requirements.txt file. This helps in not including extra installed libraries that are not being used.
Let us see how to work with it.

## Installation

`pip install pipreqs`

Once the pipreqs are installed, we can directly generate a requiremnets.txt file without creating a Virtual Environment. We have to point the path to our project folder or directory.


```bash
pipreqs /path/to/project
```


![](https://hackmd.io/_uploads/HJPD7nisc.png)

Pipreqs uses imports of projects to generate a requirements.txt file. So, it is essential to note that pipreqs will not include the external plugins required for specific projects. You need to add plugin information manually in a requirement.txt for such cases.


:::section{.summary}
-----
# Conclusion

* In Python, a requirement.txt file is a type of file that usually stores information about all the libraries, modules, and packages in itself that are used while developing a particular project.

* The most common way of creating a requirements.txt file is to run pip freeze > requirements.txt when all packages are already installed.
* In basic, a virtual environment is an isolated environment for python projects. It allows you to create a remote environment for respective each python project.

* Virtualenv is a library that allows us to execute a virtual environment.
* To get the requiremnets.txt file through Virtualenv we can pip freeze .
* Pipenv is a Python packaging tool that solves common problems associated with the typical workflow using pip, virtualenv, and the good old requirements.txt.
* Pipenv essentially acts as a replacement in place of pip. It also introduces two new files, the Pipfile (meant to replace requirements.txt) and the Pipfile.lock (which enables deterministic builds).

* Pipenv manages dependencies on a per-project basis.
* Pipreqs is the other simple alternative that doesn’t require you to create a virtual environment first. This is quite useful and easy to operate. It generates a requirement.txt file based on the import statements of the project.
* Pipreqs uses imports of projects to generate a requirements.txt file. So, it is essential to note that pipreqs will not include the external plugins required for specific projects.

:::