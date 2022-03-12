+++
ShowReadingTime = true
date = 2022-03-12T00:24:05Z
disableShare = false
title = "The ultimate IdeaVim setup"
[cover]
alt = "Image of a computer keyboard"
caption = "Keyboard specialists rejoice!"
hidden = false
image = "/uploads/paul-esch-laurent-8ssnfn4vplg-unsplash.jpg"
relative = true

+++
I've been an avid 'Vimmer' for over 5 years now, using a combination of Vim, NeoVim, and IdeaVim in a professional context.  Like most of you, I have been on the perpetual quest to discover the 'perfect' Vim config (and workflow). While I don't think it's posisble to truly define a 'perfect' setup, after much trial and error I have settled on what I believe to be the 'ultimate' Vim config, containing the optimal balance of functionality and efficiency.

What I believe to be the 'ultimate' setup actually uses IdeaVim ( the Vim emulation plugin built into JetBrains IDEs), so this post focuses on the customisation of the `.ideavimrc`, as opposed to the traditional `.vimrc`.

## Why IdeaVim

Look, don't get me wrong, I _love_ using Vim in the terminal. I've gone down the pure Vim route, the fully tweaked NeoVim route, and everything in between. While terminal Vim is pure, fast, and -let's face it- great for looking like a hipster in front of your colleagues, it's just not sufficient for day-to-day professional software development work.

I've tried, believe me I've tried, to leave the warm confines of my IDE for the neon beauty of the terminal, but I cannot abandon my debugger, test runner, and JetBrain's unbelievably good suite of refactorings.

IdeaVim allows me to find the ideal balance between the full power of the IDE, and the sleek, responsive, zen-ness of the terminal. Additionally, if you find yourself sharing your machine or pair programming, you don't have to victimise your unwitting colleague with a crash course in Vim.

_Disclaimer: I code primarily in C# in my professional capacity.  If you're coding in a toy language like Javascript, you may find terminal Vim is more than sufficient for you._

## The config

In each of the below sections, we'll take an in-depth look at each part of the IdeaVim config, explaining what the configuration does, and why we might desire it.  At the end of the post, you can find the full `.ideavimrc` file in its entirety, ripe for copy-pasting.

### Basic configuration

In this section, we'll look at some of the baseline tweaks and settings to give us a nice starting point for editor behaviour.

```vimrc
set scrolloff=10
set linenumber
set showmode
set showcmd
set visualbell
set clipboard+=unnamed
```

`scrolloff` defines the number of lines to leave on the screen before scrolling. That is, if the value is set to `10`, when moving the cursor down the page, once only 10 lines remain, the page will start to scroll.

`linenumber` ensures the editor displays the line numbers to the left of the document. A popular alternative is `relativenumber`, which shows line numbers relative to the current line (above and below). This can be handy if you tend to jump betweeen lines a lot.

`showmode` and `showcmd` simply ensure that the Vim mode (normal, insert etc) and any commands you execute are displayed at the bottom of the screen.

`visualbell` causes the annoying audible bell sound to stop being emitted whenever you enter an invalid input.

`clipboard+=unnamed` ensures that IdeaVim shares its clipboard with the system clipboard.

```vimrc
set ignorecase
set smartcase
set incsearch
set hlsearch
```

`ignorecase` tells Vim to use case-insensitive search by default.

`smartcase` tells Vim that if _any_ of the search characters are uppercase, treat the search as case-sensitive.

`setincsearch` tells Vim to start searching as you type, rather than waiting for you to submit the complete search string first.

`hlsearch` ensures all of the search results are highlighted.

```vimrc
let mapleader = " "
```

The `mapleader` command defines which key we want to use as our `leader` key. This is a unique prefix key that we can use to define a bunch of custom commands a little bit later.

The spacebar is actually a great candidate for our leader key as it is not used by any existing commands, has no use in Vim's normal mode, and is accessible by both hands.

The reason we define the leader key now rather than later, is certain plugins depend on the leader key being defined prior to the plugins being configured.

### Third party plugins

### Key mappings

### Leader commands

## TL;DR

***

## The entire .ideavimrc