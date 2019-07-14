---
layout: post
title: Vim Shortcuts to Make Life Easier
---

This is a follow up post to this amazing [post](https://dev.to/jsmanifest/21-vscode-shortcuts-to-make-coding-faster-and-more-fun-3b4m) on vscode shortcuts. I thought it would be fun to try and make the same or similar shortcuts on vim for comparison. Now mind you I am a relative new vimmer, more like a casual vimmer lol. Staying within the home row does provide faster work flow, like a painter bonding with the canvas. For my everyday use I mostly use Intellij/Android Studio, and vscode. I have vim mode turned on and I do turn it off when I feel is getting in the way.

I'll be using this repo for the examples
[coreutils](https://github.com/wertarbyte/coreutils) just clone it to your git directory.

# 1. Search Text Through All Files At Once
Probably one of the best fzf utilities for terminal is [fzf](https://github.com/junegunn/fzf), if you've ever used ```everything``` on windows then you know what I am talking about. fzf as the name implies is a fuzzy finder. fzf is supercharged with a bunch of nice commands. To use it on vim you need to have it installed first.

```
brew install fzf
```

Then you add it to your Plug vimrc, I use [vim-plug](https://github.com/junegunn/vim-plug) by the same author.

```
Plug '/usr/local/opt/fzf'
Plug 'junegunn/fzf.vim'
 ```
![fzf_lines]({{ site.baseurl }}/images/vim-shortcuts/fzf_lines.gif)