---
layout: post
title: Another Package with Cookiecutter 
---

In the previous post we've setup a basic package by manually creating the structure. In this post we will leverage a very cool package [Cookiecutter](https://github.com/cookiecutter/cookiecutter). Cookiecutter can clone the directory of another repo or even a local directory, and then it prompts for things like name, version, license, etc. You'll have a python package ready for you to code in no time. There is a huge database of already made templates too, not just for python.

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
`Note: Make sure to say n for cli`
![prompts](https://kodaman2.github.io/blog/images/python-package-series/cookiecutter-prompts.png)

All set and done:

![contents](https://kodaman2.github.io/blog/images/python-package-series/package-contents.png)

In less than a minute a whole project was created with all necessary files for a python package.

## Adding a Function to Test the Package

I use vscode, so inside the main package directory run, to bring up the project in vscode:

```
code .
```

We'll reuse our hello_world function to make sure things work before getting ahead of ourselves, delete the main module comment:

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

## Adding a py module to init

Open \__init__\.py inside the package folder, and right below the version insert the below line `(note the dot before the module name)`:

```
from .another_package import *
```

Here we tell init to import all our functions.

## Test 2

```
>>> from another_package import *
>>> say_hello("fer")
hello fer
```

Just as seen in the previous post we've built a package, but much faster and will avoid mistakes like adding a readme file or license. 

## A word on cookiecutter

If you have a project that needs certain structure you can do another template. I usually just do python utilities and use the python template. If you need a specific template that doesn't exist already, make sure to read the docs.

## Next Article

We have a working package, but it doesn't have any functionality at the moment. In the next post we'll add some functionality to run like a script from bash or cmd prompt. We will also learn how to use arguments with the argparse module. More fun to come, stay tuned!

For example:

```
say_hello -n "fer" -l "balandran"
output: hello fer balandran
```