# NERD Commenter

Comment functions so powerful—no comment necessary.

## Installation

### Via Plugin Manager (Recommended)

#### [Vim-Plug](https://github.com/junegunn/vim-plug)

1. Add `Plug 'orientlu/nerdcommenter'` to your vimrc file.
2. Reload your vimrc or restart
3. Run `:PlugInstall`

#### [Vundle](https://github.com/VundleVim/Vundle.vim) or similar

1. Add `Plugin 'orientlu/nerdcommenter'` to your vimrc file.
2. Reload your vimrc or restart
3. Run `:BundleInstall`

#### [NeoBundle](https://github.com/Shougo/neobundle.vim)

1. Add `NeoBundle 'orientlu/nerdcommenter'` to your vimrc file.
2. Reload your vimrc or restart
3. Run `:NeoUpdate`

#### [Pathogen](https://github.com/tpope/vim-pathogen)

```sh
cd ~/.vim/bundle
git clone https://github.com/orientlu/nerdcommenter.git
```

### Manual Installation

#### Unix

(For Neovim, change `~/.vim/` to `~/.config/nvim/`.)

```sh
curl -fLo ~/.vim/plugin/NERD_Commenter.vim --create-dirs \
  https://raw.githubusercontent.com/orientlu/nerdcommenter/master/plugin/NERD_commenter.vim
curl -fLo ~/.vim/doc/NERD_Commenter.txt --create-dirs \
  https://raw.githubusercontent.com/orientlu/nerdcommenter/master/doc/NERD_commenter.txt
```

#### Windows (PowerShell)

```powershell
md ~\vimfiles\plugin
md ~\vimfiles\doc
$pluguri = 'https://raw.githubusercontent.com/orientlu/nerdcommenter/master/plugin/NERD_commenter.vim'
$docsuri = 'https://raw.githubusercontent.com/orientlu/nerdcommenter/master/doc/NERD_commenter.txt'
(New-Object Net.WebClient).DownloadFile($pluguri, $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath("~\vimfiles\plugin\NERD_commenter.vim"))
(New-Object Net.WebClient).DownloadFile($docsuri, $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath("~\vimfiles\doc\NERD_commenter.txt"))
```

### Post Installation

Make sure that you have filetype plugins enabled, as the plugin makes use of **|commentstring|** where possible (which is usually set in a filetype plugin). See **|filetype-plugin-on|** for details, but the short version is make sure this line appears in your vimrc:

```sh
filetype plugin on
```

## Usage

### Documentation

Please see the vim help system for full documentation of all options: `:help nerdcommenter`

### Settings

Several settings can be added to your vimrc to change the default behavior. Some examples:

```vim
" Add spaces after comment delimiters by default
let g:NERDSpaceDelims = 1

" Use compact syntax for prettified multi-line comments
let g:NERDCompactSexyComs = 1

" Align line-wise comment delimiters flush left instead of following code indentation
let g:NERDDefaultAlign = 'left'

" Set a language to use its alternate delimiters by default
let g:NERDAltDelims_java = 1

" Add your own custom formats or override the defaults
let g:NERDCustomDelimiters = { 'c': { 'left': '/**','right': '*/' } }

" Allow commenting and inverting empty lines (useful when commenting a region)
let g:NERDCommentEmptyLines = 1

" Enable trimming of trailing whitespace when uncommenting
let g:NERDTrimTrailingWhitespace = 1

" Enable NERDCommenterToggle to check all selected lines is commented or not 
let g:NERDToggleCheckAllLines = 1
```

### Default mappings

The following key mappings are provided by default (there is also a menu provided that contains menu items corresponding to all the below mappings):

Most of the following mappings are for normal/visual mode only. The **|NERDCommenterInsert|** mapping is for insert mode only.

  * `[count]<space>cc` **|NERDCommenterComment|**

    Comment out the current line or text selected in visual mode.

  * `[count]<space>cn` **|NERDCommenterNested|**

    Same as <space>cc but forces nesting.

  * `[count]<space>c<space>` **|NERDCommenterToggle|**

    Toggles the comment state of the selected line(s). If the topmost selected line is commented, all selected lines are uncommented and vice versa.

  * `[count]<space>cm` **|NERDCommenterMinimal|**

    Comments the given lines using only one set of multipart delimiters.

  * `[count]<space>ci` **|NERDCommenterInvert|**

    Toggles the comment state of the selected line(s) individually.

  * `[count]<space>cs` **|NERDCommenterSexy|**

    Comments out the selected lines with a pretty block formatted layout.

  * `[count]<space>cy` **|NERDCommenterYank|**

    Same as <space>cc except that the commented line(s) are yanked first.

  * `<space>c$` **|NERDCommenterToEOL|**

    Comments the current line from the cursor to the end of line.

  * `<space>cA` **|NERDCommenterAppend|**

    Adds comment delimiters to the end of line and goes into insert mode between them.

  * **|NERDCommenterInsert|**

    Adds comment delimiters at the current cursor position and inserts between. Disabled by default.

  * `<space>ca` **|NERDCommenterAltDelims|**

    Switches to the alternative set of delimiters.

  * `[count]<space>cl` **|NERDCommenterAlignLeft**
    `[count]<space>cb` **|NERDCommenterAlignBoth**

    Same as **|NERDCommenterComment|** except that the delimiters are aligned down the left side (`<space>cl`) or both sides (`<space>cb`).

  * `[count]<space>cu` **|NERDCommenterUncomment|**

    Uncomments the selected line(s).
