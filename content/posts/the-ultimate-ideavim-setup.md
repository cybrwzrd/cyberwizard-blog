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

***

Look, don't get me wrong, I _love_ using Vim in the terminal. I've gone down the pure Vim route, the fully tweaked NeoVim route, and everything in between. While terminal Vim is pure, fast, and -let's face it- great for looking like a hipster in front of your colleagues, it's just not sufficient for day-to-day professional software development work.

I've tried, believe me I've tried, to leave the warm confines of my IDE for the neon beauty of the terminal, but I cannot abandon my debugger, test runner, and JetBrain's unbelievably good suite of refactorings.

The best part of using IdeaVim is I can create custom key bindings that map to JetBrains IDE actions, such as extracting variables, adjusting type signatures, or activating zen display mode.

IdeaVim allows me to find the ideal balance between the full power of the IDE, and the sleek, responsive, zen-ness of the terminal. Additionally, if you find yourself sharing your machine or pair programming, you don't have to victimise your unwitting colleague with a crash course in Vim.

_Disclaimer: I code primarily in C# in my professional capacity.  If you're coding in a toy language like Javascript, you may find terminal Vim is more than sufficient for you._

## The config

***

In each of the below sections, we'll take an in-depth look at each part of the IdeaVim config, explaining what the configuration does, and why we might desire it.  At the end of the post, you can find the full `.ideavimrc` file in its entirety, ripe for copy-pasting.

### Basic configuration

***

In this section, we'll look at some of the baseline tweaks and settings to give us a nice starting point for editor behaviour.

#### General settings

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

#### Search improvements

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

#### Leader key assignment

```vimrc
let mapleader = " "
```

The `mapleader` command defines which key we want to use as our `leader` key. This is a unique prefix key that we can use to define a bunch of custom commands a little bit later.

The spacebar is actually a great candidate for our leader key as it is not used by any existing commands, has no use in Vim's normal mode, and is accessible by both hands.

The reason we define the leader key now rather than later, is certain plugins depend on the leader key being defined prior to the plugins being configured.

### Third party plugins

***

In this section, we'll take a look at the best third-party plugins to maximise your IdeaVim experience.

#### Surround

```vimrc
set surround
```

Surround is already bundled with native IdeaVim, you simply need to enable it.  Surround lets you change the 'surrounds' of a block of text. For example, you can change double quote characters to single quotes with the following command:

    cs"'

This would result in `"Foo bar"` becoming `'Foo bar'`. This can be very handy in languages like Javascript where you may want to change a quoted string to use back-ticks so you can use string templating.

#### Highlighted Yank

```vimrc
set highlightedyank
```

Highlighted yank is also already bundled as part of IdeaVim.  The premise of this one is simple, but very useful. When you yank a character, word, or line, it briefly highlights the content you've just yanked.

#### Sneak

```vimrc
set sneak
```

[IdeaVim Sneak](https://plugins.jetbrains.com/plugin/15348-ideavim-sneak) is a port of the Vim-Sneak plugin to IdeaVim. It acts as a drop in overhaul and replacement for Vim's search in line functionality. This one isn't bundled with IdeaVim so you'll need to install the plugin from the link above.

Vim uses `f` and `F` to search forwards and backwards for an instance of a single character in the current line. Sneak uses `s` and `S` to search forwards and backwards _across multiple lines_, and searches for _2 characters_ instead, allowing for much more targeted searching.

You can use `;` and `,` to move to the next and previous search result, respectively.

#### NerdTree

```vimrc
set nerdtree
```

NerdTree is bundled with IdeaVim, and allows for Vim-like control over the file explorer. You can use the `hjkl` keys to navigate the tree structure, open and close directories, and view files in the editor, all without having to use the mouse. We'll set some keybindings for NerdTree shortly.

#### EasyMotion

```vimrc
set easymotion
set notimeout
```

[IdeaVim-EasyMotion](https://plugins.jetbrains.com/plugin/13360-ideavim-easymotion) is perhaps the single most useful plugin in this section. It completely revolutionises how you move around in Vim.  When you activate easymotion and start typing, it will highlight all instances of the sequence you type, and provide shortcodes which (once typed) will transport the cursor to that particular location. Easymotion isn't bundled with IdeaVim so you'll need to install the plugin using the above link, as well as [AceJump](https://plugins.jetbrains.com/plugin/7086-acejump) which is a peer dependency.

![Easymotion in action](/uploads/easymotion.png)

In the above image, I have activated easymotion and typed `set`. Without having to press `enter`, all the instances have been highlighted, and I can jump to any of thim with a couple of keypresses. So typing `jj` will transport the cursor to the start of line 7. Nifty right!

Handy feature - if you type the shortcode _in caps_ it will transport the cursor in _visual mode_, highlighting everything in between.

#### Which-Key

```vimrc
set which-key
```

[Which-Key](https://plugins.jetbrains.com/plugin/15976-which-key) is _awesome_. After you press the `leader` key, it will pop-up a modal at the bottom of your screen showing the possible key combinations you can press, and what each of those combinations will do. It even has support for groups!

![Which-key](/uploads/which-key.png)

In the above image, the options in pink are groups, and the options in cyan are single actions. If you press the key for any of the groups, the modal content will change to show the next key option for the group you selected. Very cool.

By default, which-key will detect your keybindings and populate the modal content automatically. However, if you'd like to have friendly and more helpful descriptions for each command (I do), you can customise this behaviour.

```vimrc
let g:WhichKeyDesc_display = "<leader>d Display options"

let g:WhichKeyDesc_zen_mode = "<leader>dz Toggle Zen mode"
let g:WhichKeyDesc_df_mode = "<leader>dd Toggle Distraction-Free mode"
let g:WhichKeyDesc_fullscreen = "<leader>df Toggle full screen"
```

The first line above sets the help text for the group, and the subsequent lines set the help text for each option in the group. When creating custom key descriptions like this, the syntax is as follows:

```vimrc
let g:WhichKeyDesc_<identifier> = "<keybinding> <helptext>"
```

The identifier can be anything you like, it doesn't get displayed anywhere. You'll see more examples in the full `.ideavimrc` file at the end of this blog, but I reccomend checking out the [Which-key documentation](https://github.com/TheBlob42/idea-which-key) for more information about customising the behavoiur.

### Key mappings

***

I actually keep my custom keymaps pretty lean; I prefer use to leader commands instead. Additionally, it can be tricky to find custom keymaps that don't clash with Vim's existing maps. Vim's default behaviour is pretty darn good, so I do advocating using the defaults where possible.

```vimrc
inoremap jk <Esc>
```

This one's a must have. Map the `jk` sequence to send an `escape` character. Some people like `jj` instead, but I find `jk` slightly faster.

```vimrc
" Tab navigation
nnoremap <A-n> :tabnext<CR>
nnoremap <A-p> :tabprev<CR>\
```

```vimrc
" Pane navigation
nnoremap <A-h> <C-w>h
nnoremap <A-l> <C-w>l
nnoremap <A-k> <C-w>k
nnoremap <A-j> <C-w>j
```

```vimrc
" Jump between methods
nnoremap [[ <Action>(MethodUp)
nnoremap ]] <Action>(MethodDown)
```

```vimrc
" Easy visual indentation
vnoremap < <gv
vnoremap > >gv
```

```vimrc
" Easy visual indentation
vnoremap < <gv
vnoremap > >gv
```

```vimrc
" Popup navigation
inoremap <C-j> <Action>(PopupMenu-selectNext)
inoremap <C-k> <Action>(PopupMenu-selectPrev)
```

### Leader commands

***

In this section we'll take a look at some of the custom leader commands you can create. This is where the true power of IdeaVim really shines, as you can map keyboard shortcuts to the powerful editor actions of JetBrains IDEs. For each of the leader commands defined below, I have also created friendly helptext for these using which-key; you can see all of these in the full `.ideavimrc` file at the end of this post.

You'll recall we set our `leader` key to be the spacebar, at the top of this post.

```vimrc
" Comment lines
map <leader>c <action>(CommentByLineComment)
```

Comment out an individual line.

```vimrc
" Jump around with easymotion
map <leader>j <Plug>(easymotion-s)
```

Activate easymotion as described above, so we can jump around our file easily.

```vimrc
" Open NERDTree (use q to exit)
map <leader>x :NERDTreeToggle<CR>
```

Open the file explorer without having to use the mouse. 

```vimrc
" Folding
map <leader>zc :action CollapseAllRegions<CR>
map <leader>zo :action ExpandAllRegions<CR>
```

Set shortcuts to globally fold and unfold the current file.

```vimrc
" Window splits
map <leader>wv <Action>(SplitVertically)
map <leader>ws <Action>(SplitHorizontally)
map <leader>wu <Action>(Unsplit)
map <leader>wm <Action>(MoveEditorToOppositeTabGroup)
```

Set shortcuts for window split operations, and group them under the `<leader>w` group.

```vimrc
" Display options
map <leader>dd <action>(ToggleDistractionFreeMode)
map <leader>dz <action>(ToggleZenMode)
map <leader>df <action>(ToggleFullScreen)
```

Toggle display modes, and nest under the `<leader>d` group.

```vimrc
" Actions
map <leader>am <action>(ShowIntentionActions)
map <leader>as <action>(SearchEverywhere)
```

Show the context menu, and the global search box using the `<leader>a` group.

```vimrc
" File navigation
map <leader>ff <action>(GotoFile)
map <leader>fr <action>(RecentFiles)
map <leader>fc <action>(FindInPath)
map <leader><leader> <Action>(RecentFiles)
map <leader>fl <action>(RecentLocations)
map <leader>fs <action>(NewScratchFile)
```

Set shortcuts for file related actions, grouping under the `<leader>f` group.

```vimrc
" Close active tab
map <leader>q <action>(CloseContent)
```

Close the active tab.

```vimrc
" Refactoring
map <leader>rn <Action>(RenameElement)
map <leader>rm <Action>(ExtractMethod)
map <leader>rv <Action>(IntroduceVariable)
map <leader>rf <Action>(IntroduceField)
map <leader>rs <Action>(ChangeSignature)
map <leader>rr <Action>(Refactorings.QuickListPopupAction)
```

Map the IDE refactoring actions to keyboard shortcuts, and nest them under the `<leader>r` group.

```vimrc
" Go to code
nmap <leader>gd <Action>(GotoDeclaration)
nmap <leader>gy <Action>(GotoTypeDeclaration)
nmap <leader>gi <Action>(GotoImplementation)
nmap <leader>gu <Action>(ShowUsages)
nmap <leader>gt <Action>(GotoTest)
nmap <leader>gf <Action>(Back)
nmap <leader>gb <Action>(Forward)
```

Map code navigation actions to keyboard shortcuts, and nest them under the `<leader>g` group.

```vimrc
" Git windows
map <leader>gc <Action>(CheckinProject)
map <leader>gs <Action>(ActivateVersionControlToolWindow)
map <leader>gb <Action>(Git.Branches)
```x

Map git actions to keyboard shortcuts, and nest them under the `<leader>g` group.

```vimrc
" Errors
map <leader>en <Action>(ReSharperGotoNextErrorInSolution)
map <leader>ep <Action>(ReSharperGotoPrevErrorInSolution)
```

Navigate errors using keyboard shortcuts.

## The entire .ideavimrc

Here is the entire `.ideavimrc` file, ripe for copy-pasting. Hope you enjoyed this post!

```vimrc
"" .ideavimrc - Matt Chapman


"" Base Settings
"" ========================================================

set scrolloff=10
set linenumber
set showmode
set showcmd

set smartcase
set incsearch
set hlsearch

set visualbell

" Use system clipboard
set clipboard+=unnamed   

let mapleader = " "


"" Plugin Settings
"" ========================================================

set surround
set highlightedyank
set sneak
set nerdtree

" Easymotion settings
set easymotion
set notimeout

" Which-key settings
set which-key
let g:WhichKey_FontSize = 16
let g:WhichKey_CommandColor = "#41ead4"
let g:WhichKey_PrefixColor = "#f335b2"
let g:WhichKey_SortOrder = "by_key_prefix_first"

let g:WhichKeyDesc_leader = "<leader> Leader key"

let g:WhichKeyDesc_leader = "<leader>x Open file explorer"

let g:WhichKeyDesc_easymotion = "<leader>j Jump with Easymotion"
let g:WhichKeyDesc_easymotion_prefix = "<leader><leader>"

let g:WhichKeyDesc_comment = "<leader>c Comment line"

let g:WhichKeyDesc_fold = "<leader>z Folding"
let g:WhichKeyDesc_fold_all = "<leader>zc Fold all regions"
let g:WhichKeyDesc_unfold_all = "<leader>zo Unfold all regions"

let g:WhichKeyDesc_window = "<leader>w Window splits"
let g:WhichKeyDesc_window_split_vertically = "<leader>wv Split vertically"
let g:WhichKeyDesc_window_split_horizontally = "<leader>wh Split horizontally"
let g:WhichKeyDesc_window_split_unsplit = "<leader>wu Unsplit"
let g:WhichKeyDesc_window_split_move_editor = "<leader>wm Move editor to opposite tab group"


let g:WhichKeyDesc_display = "<leader>d Display options"
let g:WhichKeyDesc_zen_mode = "<leader>dz Toggle Zen mode"
let g:WhichKeyDesc_df_mode = "<leader>dd Toggle Distraction-Free mode"
let g:WhichKeyDesc_fullscreen = "<leader>df Toggle full screen"

let g:WhichKeyDesc_action= "<leader>a Actions"
let g:WhichKeyDesc_action_context_menu = "<leader>am Open context menu"
let g:WhichKeyDesc_action_search = "<leader>as Open command modal"

let g:WhichKeyDesc_file_quickLook = "<leader><leader> Recent files"

let g:WhichKeyDesc_file_nav = "<leader>f File navigation"
let g:WhichKeyDesc_file_nav_goto_file = "<leader>ff Go to file"
let g:WhichKeyDesc_file_nav_goto_content = "<leader>fc Search for file content"
let g:WhichKeyDesc_file_nav_show_recent_files = "<leader>fr Show recent files"
let g:WhichKeyDesc_file_nav_show_recent_locations = "<leader>fl Show recent locations"

let g:WhichKeyDesc_close_tab = "<leader>q Close active tab"

let g:WhichKeyDesc_refactoring = "<leader>r Refactoring menu"
let g:WhichKeyDesc_refactoring_rename = "<leader>rn Rename element"
let g:WhichKeyDesc_refactoring_method = "<leader>rm Extract method"
let g:WhichKeyDesc_refactoring_variable = "<leader>rv Introduce variable"
let g:WhichKeyDesc_refactoring_field = "<leader>rf Introduce field"
let g:WhichKeyDesc_refactoring_signature = "<leader>rs Change signature"
let g:WhichKeyDesc_refactoring_all = "<leader>rr Open refactorings list"

let g:WhichKeyDesc_goto = "<leader>g Go to X"
let g:WhichKeyDesc_goto_declaration = "<leader>gd Go to Definition"
let g:WhichKeyDesc_goto_type_declaration = "<leader>gy Go to Type Definition"
let g:WhichKeyDesc_goto_implementation = "<leader>gi Go to Implementation"
let g:WhichKeyDesc_goto_usages = "<leader>gu Go to Usages"
let g:WhichKeyDesc_goto_test = "<leader>gt Go to Test"
let g:WhichKeyDesc_goto_back = "<leader>gb Go Back"
let g:WhichKeyDesc_goto_forward = "<leader>gf Go Forward"

let g:WhichKeyDesc_git = "<leader>g Git operations"
let g:WhichKeyDesc_git_commit = "<leader>gc Open Git commit dialog"
let g:WhichKeyDesc_git_status = "<leader>gs Open Git status dialog"
let g:WhichKeyDesc_git_branches = "<leader>gb Open Git branches list"

let g:WhichKeyDesc_errors = "<leader>e Error navigation"
let g:WhichKeyDesc_errors_next = "<leader>en Go to next error in solution"
let g:WhichKeyDesc_errors_prev = "<leader>ep Go to previous error in solution"


"" Key mappings
"" ========================================================

inoremap jk <Esc>

" Tab navigation
nnoremap <A-n> :tabnext<CR>
nnoremap <A-p> :tabprev<CR>

" Pane navigation
nnoremap <A-h> <C-w>h
nnoremap <A-l> <C-w>l
nnoremap <A-k> <C-w>k
nnoremap <A-j> <C-w>j

" Jump between methods
nnoremap [[ <Action>(MethodUp)
nnoremap ]] <Action>(MethodDown)

" Easy visual indentation
vnoremap < <gv
vnoremap > >gv

" Execute macro saved in 'q' register
nnoremap qj @q

" Popup navigation
inoremap <C-j> <Action>(PopupMenu-selectNext)
inoremap <C-k> <Action>(PopupMenu-selectPrev)


"" Leader commands
"" ========================================================

" Comment lines
map <leader>c <action>(CommentByLineComment)

" Jump around with easymotion
map <leader>j <Plug>(easymotion-s)

" Open NERDTree (use q to exit)
map <leader>x :NERDTreeToggle<CR>

" Folding
map <leader>zc :action CollapseAllRegions<CR>
map <leader>zo :action ExpandAllRegions<CR>

" Window splits
map <leader>wv <Action>(SplitVertically)
map <leader>ws <Action>(SplitHorizontally)
map <leader>wu <Action>(Unsplit)
map <leader>wm <Action>(MoveEditorToOppositeTabGroup)

" Display options
map <leader>dd <action>(ToggleDistractionFreeMode)
map <leader>dz <action>(ToggleZenMode)
map <leader>df <action>(ToggleFullScreen)

" Actions
map <leader>am <action>(ShowIntentionActions)
map <leader>as <action>(SearchEverywhere)

" File navigation
map <leader>ff <action>(GotoFile)
map <leader>fr <action>(RecentFiles)
map <leader>fc <action>(FindInPath)
map <leader><leader> <Action>(RecentFiles)
map <leader>fl <action>(RecentLocations)
map <leader>fs <action>(NewScratchFile)

" Close active tab
map <leader>q <action>(CloseContent)

" Refactoring
map <leader>rn <Action>(RenameElement)
map <leader>rm <Action>(ExtractMethod)
map <leader>rv <Action>(IntroduceVariable)
map <leader>rf <Action>(IntroduceField)
map <leader>rs <Action>(ChangeSignature)
map <leader>rr <Action>(Refactorings.QuickListPopupAction)

" Go to code
nmap <leader>gd <Action>(GotoDeclaration)
nmap <leader>gy <Action>(GotoTypeDeclaration)
nmap <leader>gi <Action>(GotoImplementation)
nmap <leader>gu <Action>(ShowUsages)
nmap <leader>gt <Action>(GotoTest)
nmap <leader>gf <Action>(Back)
nmap <leader>gb <Action>(Forward)

" Git windows
map <leader>gc <Action>(CheckinProject)
map <leader>gs <Action>(ActivateVersionControlToolWindow)
map <leader>gb <Action>(Git.Branches)

" Errors
map <leader>en <Action>(ReSharperGotoNextErrorInSolution)
map <leader>ep <Action>(ReSharperGotoPrevErrorInSolution)

```