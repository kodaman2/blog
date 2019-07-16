---
layout: post
title: Another Package with Cookiecutter 
---

In the previous post we've setup a basic package by manually creating the structure. In this post we will leverage a very cool package [Cookiecutter](https://github.com/cookiecutter/cookiecutter). Cookiecutter can clone the directory of another repo or even a local directory. You'll have a python package ready in no time. There is a large database of templates too, not just for python.

## Installing Cookiecutter

You can install cookiecutter with a pip command(Note: I am using pip3 because I also have py2 installed):

```
pip3 install cookiecutter
```

## Create Package

On my git directory I can then run:

```
cookiecutter https://github.com/audreyr/cookiecutter-pypackage
```

Since github is the defacto for repositories you can also run:

```
cookiecutter gh:audreyr/cookiecutter-pypackage
```
`Note: Make sure to say 2 for cli`
![prompts](https://kodaman2.github.io/blog/images/python-package-series/cookiecutter-prompts.png)

All set and done:

![contents](https://kodaman2.github.io/blog/images/python-package-series/package-contents.png)

In less than a minute a whole project was created with all necessary files for a python package.

## Adding a Function to Test the Package

I use vscode, so inside the main package directory run, to bring up the project in vscode:

```
code .
```

We'll reuse our `hello_world` function to make sure the project works as expected:

```python
# -*- coding: utf-8 -*-

"""Main module."""
def say_hello(name):
    print("hello %s" % (name))
```

## Installing the Package

Installing with dev argument same as before:

```
python3 setup.py develop
```

## Testing say_hello function

At this point we can test our function. Launch python3 in the terminal or launch idle.

```
>>> from another_package import *
>>> say_hello("fer")
```

Won't run huh? We forgot to do one thing, and that is to add our python module to the init file. The reason it fails is that it doesn't know what functions to include in the package.

```
>>> from another_package import *
>>> say_hello("fer")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'say_hello' is not defined
```

## Adding a py module to init

Open \__init__\.py inside the package folder, and below the version insert the following: `(note the dot before the module name)`:

```
from .another_package import *
```

Here we tell init to import all our functions.

## Test 2

Exit python, and relaunch to reload another_package.

```
>>> from another_package import *
>>> say_hello("fer")
hello fer
```

With this process in place you won't be forgetting adding a readme file or a license ever again.

## A word on cookiecutter

If you have a project that needs certain structure you can do another template. I usually just do python utilities and use the python template. If you need a specific template that doesn't exist already, make sure to read the docs on how to create a template.

## Next Article

We have a working package, but it doesn't have any functionality at the moment. In the next post we'll add some functionality to run like a script from bash or cmd prompt. We will also learn how to use arguments with the argparse module. More fun to come, stay tuned!

For example:

```
say_hello -n "fer" -l "balandran"
output: hello fer balandran
```