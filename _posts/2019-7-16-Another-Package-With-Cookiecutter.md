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

![prompts](https://kodaman2.github.io/blog/images/python-package-series/cookiecutter-prompts.png)

All set and done:

![contents](https://kodaman2.github.io/blog/images/python-package-series/package-contents.png)