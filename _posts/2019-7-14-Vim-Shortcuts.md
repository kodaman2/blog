---
layout: post
title: Vim Shortcuts to Make Life Easier
---

This is a follow up post to this amazing [post](https://dev.to/jsmanifest/21-vscode-shortcuts-to-make-coding-faster-and-more-fun-3b4m) on vscode shortcuts. I thought it would be fun to try and make the same or similar shortcuts on vim for comparison. Now mind you I am a relative new vimmer, more like a casual vimmer lol. Staying within the home row does provide faster work flow, like a painter bonding with the canvas. For my everyday use I mostly use Intellij/Android Studio, and vscode. I have vim mode turned on and I do turn it off when I feel is getting in the way.

I'll be using this repo for the examples
[coreutils](https://github.com/wertarbyte/coreutils) just clone it to your git directory.

## 1. Search Text Through All Files At Once
Probably one of the best utilities for terminal is [fzf](https://github.com/junegunn/fzf), if you've ever used ```everything``` on windows then you know what I am talking about. fzf as the name implies is a fuzzy finder. fzf is supercharged with a bunch of nice commands. To use it on vim you need to have it installed first.

```
brew install fzf
```

Then you add it to your Plug vimrc, I use [vim-plug](https://github.com/junegunn/vim-plug) by the same author.

```
Plug '/usr/local/opt/fzf'
Plug 'junegunn/fzf.vim'
```

For this next example, simply do ```:Lines``` then type whatever you're looking for. Fzf will look in the opened buffers, if you are looking just in one buffer then do ```:BLines```. A cool thing about fzf is well that it finds anything even if missing a few letters here and there. Also if you don't want fuzzy finding you can start the fzf commands with a single quote ```'```.

![fzf_lines]({{ site.baseurl }}/images/vim-shortcuts/fzf_lines.gif)

Fzf is amazingly fast, no kidding try it on a big project.

## 2. Select lines inside brackets

There are quite a few ways to select text in vim, in fact you don't even need visual mode to do it.

Place cursor in a bracket or inside the brackets.

```
ya(
ya{
```

![yanking_bracketts]({{ site.baseurl }}/images/vim-shortcuts/yanking_brackets.gif)

If you'd like to do it visually, place cursor in a bracket, then you can do yank(y), or cut(d).

```
v%
```

![select_visual]({{ site.baseurl }}/images/vim-shortcuts/select_visual.gif)

## 3 Open a file in the buffer with fzf

If you ever need help on fzf utility you can do ```:help fzf``` within vim. You can see the help file, and all the commands it does. Buffers command show you all the buffers opened at the moment. Then if you start typing you can do fzf finding if you have lots of buffers opened.

```
:Buffers
```

![open_buffers]({{ site.baseurl }}/images/vim-shortcuts/open_buffers.png)

## 4 Find a file in the project with fzf

Same as with the buffers command, but with all files within the directory you are working with.

```
:Files
```

![files_01]({{ site.baseurl }}/images/vim-shortcuts/files_01.png)

Note how fzf picks up strnumcmp.c when searching for num. If you start the search with ```'``` it will look for whole words.

![files_02]({{ site.baseurl }}/images/vim-shortcuts/files_02.png)