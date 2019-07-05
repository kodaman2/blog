---
layout: post
title: Part 1 Introduction to Python Packages
---

This will be the first article in the series, where I intent to show you everything about Python Packaging. Well maybe not everything, but everything you need to know about creating a self contained module that you can deploy to the Python Packing Index aka [PyPi](https://pypi.org/), and Github for the world to consume.

## Why should you ever need a package?
If you are a programmer, and chances are 99% certain since you are reading this article. There comes a time where a lightbulb goes off in your head. You have an idea for a wonderful python project. Even better you think it would benefit the community or certain group. It can be a tool, helper functions, even a small script. Whatever the idea might be, publishing a package can make sure your work is available for others to use, or even future you should something happen to your computer. (Yeah I know that's the monitor lol)

![alt text](https://media.giphy.com/media/S7u66urzxc2J2/giphy.gif)

## Benefits of using a package manager
Package Installer for Python (pip) is not the only package manager out there. There are other managers which you've probably used, homebrew, apt-get, rpm, and the list goes on and on. 

We will concentrate in pip, since it is built around python and is cross platform, and well documented. In addition you can easily install other pip packages, and dependencies for your project. You can create multi-platform package. You can easily install/update via simple commands.

## What does a package manager actually do?
Package managers attempt to solve one problem, and that is to make it easy and accessible for users to download modules, while at the same time assisting programmers to build packages in a sane way by providing the tools required for deployment. Imagine if each time someone needed to print a statement, they had to go the internet to download some awesome print module, then copy and paste in a designated folder. What happens if that print module got a new version, now you have to rinse and repeat.

![](https://media.giphy.com/media/3nFKBN97bDwli/giphy.gif)

One does not think much of what it takes to maintain a package until you have to maintain a package. Update repo, version, contributors list, distributables, etc.

The basic premise of pip is that it is a full cmd utility.
- pip install some_package
- pip search some_package
- pip install some_package --upgrade
- pip uninstall some_package
- pip install git+https://github.com/some_repo/a_repo.git
- pip freeze > requirements.txt (Sends a list of installed packages to a text file)
- pip install -r requirements.txt (Where requirements is one package per line, awesome when building a new virtualenv)

## Next article
Ok, lots of good information in this article. In the next one we will setup our development environment, and create a basic package. Thanks for reading!
