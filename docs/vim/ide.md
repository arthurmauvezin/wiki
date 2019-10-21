# VIM - IDE

## Vimrc file
```
call plug#begin()
" Useful VIM IDE plugins
Plug 'davidhalter/jedi-vim'
Plug 'tmhedberg/SimpylFold'
Plug 'vim-scripts/indentpython.vim'
Plug 'nvie/vim-flake8'
call plug#end()

" VIM IDE settings
let mapleader=" "
set encoding=utf-8

" Split to right and down
set splitbelow
set splitright
" Split navigation
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>

" Enable folding
set foldmethod=indent
set foldlevel=99
" Enable folding with the spacebar
nnoremap <space><space> za

" Find bab whitespace
highlight BadWhitespace ctermbg=red guibg=darkred
au BufRead,BufNewFile *.py,*.pyw,*.c,*.h match BadWhitespace /\s\+$/
```

## Split
```
# Horizontally
:sp <filename>
# Vertically
:vs <filename>
```

## Move from pane to pane
```
Ctrl+J # Move to split below
Ctrl+K # Move to split above
Ctrl+L # Move to split right
Ctrl+H # Move to split left
```

## Open recent file (buffer)
```
# List buffers
:ls
# Open buffer
:b <buffer name>
```

## Fold Code
```
<space>
```

## Autocompletion
```
Ctrl+<space>
```

## Goto assignment
```
<space>+g
```

## Goto definitions
```
<space>+d
```

## Show Documatation/Pydoc
```
<shift>+k
```

## Rename
```
<space>+r
```

## Show usages
```
<space>+n
```

## Open module
```
:Pyimport <module>
# Example
:Pyimport os
```

