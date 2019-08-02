---
layout: post
title: Argparse and Script Entry Points
---

We are ready to call our utility from the cmd line, problem is we haven't setup an entry point. We want to do something like this 'my_cli args' from the cmd line.

Once we have done that we will proceed to setup argparse which is one of the modules that eases the pain when dealing with input arguments. There are other modules like click, and optparse. Argparse happens the one I use the most in my cmd utilities.

Arguments modules abstract some things to make it easier to handle arguments, it also adds a quick help command based on the arguments setup. You don't have to worry about calling a wrong argument, argparse will handle that nicely.

## Setup Script Entry Point

[Documentation](https://packaging.python.org/specifications/entry-points/) for entry points. You can have multiple entry points, but we will only use one.

On 'setup.py' at the very end:

```
...
version='0.0.1',
    zip_safe=False,
```
Add the following:
```
entry_points={
        'console_scripts': [
            # command = package.module:function
            'my_cli = another_package.another_package:say_hello',
        ],
    },
```

## Quick Test
At this point we can unistall our current utility since we've modified the setup.py.

```
pip3 uninstall another-package
cd git/another-package
python3 setup.py develop
```

If install is sucessfull, go into terminal or cmd prompt and type 'my_cli', you'll get the error below. 'say_hello' needs an argument for the string, and so we get a traceback as we should. And with this we know that our entry point is working as it should, even though we can't call 'say_hello' without providing an argument. Note below even when I tried to provide my name, the utility doesn't know how to handle that arg, fear not argparse to the rescue.

```
Fernandos-MacBook-Air:another_package terminalX$ my_cli "fer"
Traceback (most recent call last):
  File "/Library/Frameworks/Python.framework/Versions/3.7/bin/my_cli", line 11, in <module>
    load_entry_point('another-package', 'console_scripts', 'my_cli')()
TypeError: say_hello() missing 1 required positional argument: 'name'
```

## Argparse Setup

Modify 'another_package.py', I don't think '__ main __' is necessary since we will be caling 'main' from our entry point but that's how I always setup my utilities. This way you can also call python another_package.py args*.

```python
# -*- coding: utf-8 -*-

import argparse

"""Main module."""
def say_hello(name):
    print("hello %s" % (name))

def main():
        parser = argparse.ArgumentParser()
        parser.add_argument('-n', '--name', action="store", help='Provides name')
        args = parser.parse_args()

        say_hello(args.name)
 
 
if __name__ == '__main__':
          main()

```

Modify 'setup.py':

```
'my_cli = another_package.another_package:main',
```

Ok we are ready to make yet another test, unistall, and reinstall as mentioned in the Quick Test section.

## Second Test
Once utility is installed run the following commands:

```
my_cli
my_cli -h
my_cli -n yourname
```

If everything went ok, you should see your name output properly.
If you'd like to know more about argparse check out the [documentation](https://docs.python.org/3/library/argparse.html?highlight=argparse#).

```
Fernandos-MacBook-Air:another_package terminalX$ my_cli -n fer
hello fer
```

## Next Article

In the next post we will publish our package to github or any git repo for that matter. Remember having a package in github alone is great since you can install with pip. Thanks for reading, hope you enjoyed, and until the next one.