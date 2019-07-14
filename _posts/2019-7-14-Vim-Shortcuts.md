---
layout: post
title: Vim Shortcuts to Make Life Easier
---

This is a follow up post to this amazing [post](https://dev.to/jsmanifest/21-vscode-shortcuts-to-make-coding-faster-and-more-fun-3b4m) on vscode shortcuts. I thought it would be fun to try and make the same or similar shortcuts on vim for comparison. Now mind you I am a relative new vimmer, more like a casual vimmer lol. Staying within the home row does provide faster work flow, like a painter bonding with the canvas. For my everyday use I mostly use Intellij/Android Studio, and vscode. I have vim mode turned on and I do turn it off when I feel is getting in the way.

I'll be using this repo for the examples
[coreutils](https://github.com/wertarbyte/coreutils) just clone it to your git directory.

## 1 Search Text Through All Files At Once
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

## 2 Select lines inside brackets

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

## 5 Launch terminal

This is just personal preference, because when you are in vim you are in the terminal, if you use iTerm2 then you can switch between tabs relatively easy.

If you want to have a terminal tab within vim I use [split-term](https://github.com/vimlab/split-term.vim) plugin. Keep in mind I use neovim, let me know if you also use this or some other plugin in vim.

There are far too many configurations to talk about to make sure to visit the repo.

- :Term Opens a new terminal buffer using :new (splits horizontally)
- :VTerm Opens a new terminal buffer using :vnew (splits vertically)
- :TTerm Opens a new terminal buffer using :tabnew (new tab)

![terminal]({{ site.baseurl }}/images/vim-shortcuts/terminal.png)

## 6 Delete Everything to the Left/Right

This is far too easy with vim. Move your cursor to where you want it with motions or hjkl, if you want to delete everything to the left ```d0```, if you want to do to the right ```d$```.

![delete_left_right]({{ site.baseurl }}/images/vim-shortcuts/delete_left_right.gif)

Another good one is the ```t``` (until). So if you want to delete until a bracket you would do ```dt)```.

![delete_until]({{ site.baseurl }}/images/vim-shortcuts/delete_until.gif)

## 7 Delete Previous Word

If you are writing some text and you make a mistake, exit insert mode, and do ```daw``` (delete a word).

For more tips on this do ```:help diw``` in vim.

![daw]({{ site.baseurl }}/images/vim-shortcuts/daw.gif)

## 8 Select Words

Visual mode in vim is just another world in itself, it has line, block, and columns modes. To select words make sure you are in visual mode by hitting lower ```v```. Then press ```w``` to select next word. Let's say you selected a word you don't want, hit ```b``` for back, most vim commands have some sort of pnemonic. There is also ```e``` for end of word.

![word_select]({{ site.baseurl }}/images/vim-shortcuts/word_select.gif)

## 9 Selecting Lines

Visual Lines mode, let's you select lines easily.
Enter lines mode with upper case ```V```.

![lines_select]({{ site.baseurl }}/images/vim-shortcuts/lines_select.gif)

## 10 Duplicate a Line

Simply yank the line with ```yy```, the paste with ```p```.

![duplicate_line]({{ site.baseurl }}/images/vim-shortcuts/duplicate_line.gif)

## 11 Move to Beginning/End of File

Moving in vim is such of breeze. Top of the file with ```gg```, and ```G``` to the end of the file.

![start_end]({{ site.baseurl }}/images/vim-shortcuts/start_end.gif)

## 12 Move Up/Down a File

You can move up and down a file with ```CTRL+U``` and ```CTRL+D```, also you can use ```SHIFT+ {``` and ```SHIFT+}```.

## 13 Search Words in a File

Searching for words in a file with vim is pretty cool, but not as cool as fzf. To search for a word you do ```/``` then type the word to find. To go to next word you hit ```n```, and to go to previous word ```N```. In addition you can search backwards with ```?```.

## 14 Replace Words in a File

Search and replace can take various forms.

```
:%s/search/replace/gc
```

- % indicates search in the whole file
- g for global, meaning all occurrences
- c is for confirmation

When you run this command you'll get a confirmation where you can hit yes or no for each instance or simply hit ```a``` to replace all instances.

![replace]({{ site.baseurl }}/images/vim-shortcuts/replace.gif)

## 15 Move Line Up/Down

Vim provides a move command for moving lines around.

```
:move+1
:move-2
```

## 16 Delete a Line

If you want to delete the whole line, you can do ```dd```.

## 17 Add Cursor Multiple Lines

- Move the cursor to the position on first line.
- Enter visual block mode (ctrlv).
- Press j three times (or 3j).
- Press I (Uppercase i).
- Type in whatever.
Press esc.

Seems like a lot but once you get used it is quick.

![multiline]({{ site.baseurl }}/images/vim-shortcuts/multiline.gif)

## 18 EasyMotion in Vim

EasyMotion is a cool plugin that helps with traversing thorugh text really quick, it also works within vscode if you are interested in trying vim in vscode, thought the shortcomings of using vim in vscode is that you can't bring in any plugins other than the ones provided by the vscodevim plugin.

Make sure to check out [github](https://github.com/easymotion/vim-easymotion) for full description of the plugin.

![easymotion]({{ site.baseurl }}/images/vim-shortcuts/easymotion.gif)

## 19 NerdTree

Another cool plugin for looking in directories is [NerdTree](https://github.com/scrooloose/nerdtree). 

![tree]({{ site.baseurl }}/images/vim-shortcuts/tree.gif)

For more plugins visit https://vimawesome.com/

## 20 Bookmarking aka Marks

I am not sure if vscode has this feature, but nevertheless is pretty cool in vim. You just put your cursor in a line, and hit ```m``` and a letter or number.

If you do ```ma``` then your mark will be ```a```

To see your current marks, you can do (Marks to use with fzf plugin):

```
:marks
:Marks
```

![marks]({{ site.baseurl }}/images/vim-shortcuts/marks.png)

You can also delete marks:

```
:delmarks a
```
Delete all lowercase marks:

```
:delmarks!
```

If you ever got too many marks you can delete ```~/.viminfo``` which contains history and marks.

## Conclusion

Lots of cool stuff you can do with Vim, I particularly which I could do vim with all the plugins but in a vscode environment, and I think that's what Oni is trying to accomplish. Let me know what you think or what cool tricks or plugins you use in vim. Hasta la vimsta baby!