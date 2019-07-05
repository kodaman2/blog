---
layout: post
title: Part 2 A Basic Package
---
In the previous article we've talked about what packages are, and while that was a nice intro. I'd rather show you how to build one, we won't get to crazy with it, just enough to show you the basics.

## Barebones structure

In order to create a package we need a folder structure, for a single .py project a package is technically not needed [py-modules doc](https://packaging.python.org/guides/distributing-packages-using-setuptools/#py-modules). However most folks will probably have several packages in their project to keep things organized. (Note: In a later article I will talk about cookiecutter and templates)

```
├── README.md
├── awesome_package
│   ├── __init__.py
│   └── hello_world.py
└── setup.py
```

Here's the link for the above package structure 

- [Barebones-01](https://github.com/kodaman2/A_Basic_Package/tree/Barebones-01)

## Setup
The /setup.py file is the most important file for the package. It contains all the information your package needs. We will discuss this in more detail in a later article. For now the below will suffice to get us up and running.

```python
from setuptools import setup, find_packages

setup(
    name='my_tool',
    version='0.0.1',
    packages=find_packages(exclude=['contrib', 'docs', 'tests*']),
)
```
- [Setup.py-02](https://github.com/kodaman2/A_Basic_Package/tree/Setup.py-02)

## Let's add some python code
We won't get crazy we will add one function to our hello_world file

```python
def say_hello(name):
    print("hello %s" % (name))
```

## Adding our function to init

```
from .hello_world import *
```

We are importing all functions found in hello_world, in our case is only one. Ok, we are ready to test our package.

## Install as development package
A few things to take note. Installing a package with the development argument allows us to make changes, without having to keep installing or updating through a ```pip --upgrade``` command. Which could get tedius if you are working on something that takes days or weeks, or longer.

Another thing worth mentioning is that if you make changes and you've already launched python in the terminal, you'll have to exit(), and re-launch python. Don't ask me how I know this. 

Inside the package, install it by running the below command.
```
python3 setup.py develop
```
Check to make sure the package installed.

```
pip list
...
my-tool                  0.0.1       /Users/terminalX/git/A_Basic_Package
...
```

## Test our package

Launch python in terminal, and test our package as shown below. Too easy, mate. As the aussies say.

```
>>> from awesome_package import *
>>> say_hello("fer")
hello fer
```

- [Test-03](https://github.com/kodaman2/A_Basic_Package/tree/Test-03)

# Install Package from Github

Now that we have a fully working package, we can uninstall the development install, and install straight from Github

```
pip3 uninstall my_tool
pip3 install git+https://github.com/kodaman2/A_Basic_Package.git
```

Ensure you can still use the ```say_hello()``` function.

**Tip: If you want to know which methods are available in a module:**

```
>>> dir(hello_world)
['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'say_hello']
```

## Next Article

Make sure you play around with the package, add more functions, more packages, and see what happens. Remember if you decide to play around some more with this package uninstall it, and install as explained in the development section.

In the next article we will create a more advanced example, while learning how to efficiently create the package with the help of other python tools. Thanks for reading.