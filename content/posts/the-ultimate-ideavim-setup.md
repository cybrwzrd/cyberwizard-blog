+++
ShowReadingTime = true
date = 2022-03-12T00:24:05Z
disableShare = false
title = "The ultimate IdeaVim setup"
[cover]
alt = "Image of a computer keyboard"
caption = "Keyboard specialists rejoice!"
hidden = true
image = "/uploads/paul-esch-laurent-8ssnfn4vplg-unsplash.jpg"
relative = true

+++
I've been an avid 'Vimmer' for over 5 years now, using a combination of Vim, NeoVim, and IdeaVim in a professional context.  Like most of you, I have been on the perpetual quest to discover the 'perfect' Vim config (and workflow). While I don't think it's posisble to truly define a 'perfect' setup, after much trial and error I have settled on what I believe to be the 'ultimate' Vim config, containing the optimal balance of functionality and efficiency.

![My setup](/uploads/ideavim.png)

Believe it or not, the above screenshot is of JetBrains Rider - a fully fledged IDE, looking decidedly 'zen-like'

In this post, I'll show you how to configure your workflow like mine, so that you end up with a final result looking like the above image.

## Why IdeaVim

## The config

### Basic configuration

In this section, we'll look at some of the baseline tweaks and settings to give us a nice starting point for editor behaviour.

```vimrc
set scrolloff=10
set linenumber
set showmode
set showcmd
```
`scrolloff` defines the number of lines to leave on the screen before scrolling. That is, if the value is set to `10`, when moving the cursor down the page, once only 10 lines remain, the page will start to scroll.

`linenumber` ensures the editor displays the line numbers to the left of the document. A popular alternative is `relativenumber`, which shows line numbers relative to the current line (above and below). This can be handy if you tend to jump betweeen lines a lot.

`showmode` and `showcmd` simply ensure that the Vim mode (normal, insert etc) and any commands you execute are displayed at the bottom of the screen.

```vimrc
set smartcase
set incsearch
set hlsearch
```

These 3 lines all relate to Vim's searching functionality

### Third party plugins

### Key mappings

### Leader commands

## TL;DR