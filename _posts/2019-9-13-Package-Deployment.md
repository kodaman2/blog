---
layout: post
title: Package Deployment
---

We are almost finished with our python package series. In this post we'll discuss deployment.

- Github repo
- PyInstaller
- Releases
- PyPi

## Github

There isn't much to do in terms of github or any other git server. Just push your changes and you are done. I would recommend using tags, for example for indicating a version, i.e. v2.0.1. And update your README file.

## PyInstaller

Depending on how complex your package is, and if it can run as an exe or dmg, you can package your application with [PyInstaller](https://www.pyinstaller.org/).

First install pyinstaller:

```
pip install pyinstaller
```

Then run:

```
pyinstaller your_file.py
```

> This will generate the bundle in a subdirectory called dist.

One File:

```
pyinstaller your_file.py --onefile
```

Debugging:

```
pyinstaller your_file.py --onefile --log-level LEVEL
```

> Amount of detail in build-time console messages. LEVEL may be one of TRACE, DEBUG, INFO, WARN, ERROR, CRITICAL (default: INFO).

For full usage visit the [docs](https://pyinstaller.readthedocs.io/en/stable/usage.html)

## Add it to Release

Once you have a dmg, or exe, you can add it to the releases on github, and this is nice for end users that don't know how to pip, or compile code. This is well [documented](https://help.github.com/en/articles/creating-releases).

## PyPi

Sign up for an account https://pypi.org/

[Docs](https://packaging.python.org/tutorials/packaging-projects/)

### Build

Let's build the package first, ensuring you have all the tools installed.

```
python -m pip install --user --upgrade setuptools wheel
```

Now run this command from the same directory where setup.py is located:

```
python3 setup.py sdist bdist_wheel
```

This command should output a lot of text and once completed should generate two files in the dist directory:

```
dist/
  example_pkg_your_username-0.0.1-py3-none-any.whl
  example_pkg_your_username-0.0.1.tar.gz
```

### Twine upload to PyPi

```
python -m pip install --user --upgrade twine
```

You can add a configuration file in your home directory, for easy uploads:

`.pypirc`

```
[distutils]
index-servers=pypi

[pypi]
repository = https://upload.pypi.org/legacy/
username = your_username
password = your_password
```

With `.pypirc` in place you can upload with following command:

```
twine upload dist/*
```

Lastly secure `.pypirc` file so only current user can read it:

```
chmod 600 ~/.pypirc
```

> A couple of things to note:
> I couldn't test with the test site for pypi. So I ended up just doing it to the real site.
> Ensure your version number in the setup.py is correct, and all the information there. Once you upload a version, you cannot reupload again unless you change the version number.

## Installing your package

After a few seconds check your package in your PyPi account, if is there. Install it via pip on your local machine. And you have finally completed your first deployment.

## Recap

Every release:

- Update git repo
- Upload git release (option)
- Compile with setup tools
- Upload with twine to PyPi

Congratulations for making it to the end! Any feedback is welcomed! Remember do not deploy on Fridays. :)
