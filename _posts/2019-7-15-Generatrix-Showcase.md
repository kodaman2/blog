---
layout: post
title: Showcase Generatrix Utility for Git Branches/Tags Markdown
---

I wrote this utility last week which I call [Generatrix](https://github.com/kodaman2/generatrix_py). It generates markdown for a repo branches/tags. I don't know how much of a problem this is for other people, but I figured to share it anyways. If you are doing a tutorial, and need to provide code to your users, and you split the code in branches or tags as you progress throughout the tutorial or lesson, you can too use generatrix. And then copy and paste the output in your readme.

## Backstory

I actually started doing a static site on [https://kodaman2.github.io/generatrix/](https://kodaman2.github.io/generatrix/), [repository](https://github.com/kodaman2/generatrix) but I sorta failed miserably because I suck at JS, well not really, I just suck at async code. I've never done any JS and I got frustated, I did asked for help which some folks provided awesome help and I still have to work on it. Site works but branches are spit out not in date order, sometimes, which is a problem. I am sure my JS code is a mess lol.

Out of order mkdown
![static_gtrix](https://kodaman2.github.io/blog/images/gtrix/gtrix_site.png)

## Python Version
I spent a few days on the static site, and then went and did the python version in a couple of hours.

![gtrix_cmd](https://kodaman2.github.io/blog/images/gtrix/gtrix.gif)

It works in all platforms since is piping git commands.

```
pip install Generatrix
```

Inside a git repo:
```
gtrix
  or
gtrix --help
  or
gtrix --tags
```

Optional, if you don't have .gitconfig configured:
```
gtrix --user "username"
```

All arguments have short version too, help documentation is on the repo posted in the beginning. Let me know if you've ever had to generate this manually for a readme file. I welcome feedback as well. :)