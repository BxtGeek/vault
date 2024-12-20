```
""" Basic .vimrc configuration for YAML and Bash scripting

" Enable syntax highlighting
syntax on

" Set line numbering
set number

" Enable relative line numbering
set relativenumber

" Highlight search results
set hlsearch

" Incremental search
set incsearch

" Auto-indent settings
set autoindent
set smartindent

" Tabs and spaces settings
set tabstop=2
set shiftwidth=2
set expandtab

" Enable file type detection
filetype on
filetype plugin on
filetype indent on

" Specific settings for YAML files
augroup yaml
  autocmd!
  autocmd FileType yaml setlocal ts=2 sw=2 expandtab
augroup END

" Specific settings for Bash scripting files
augroup bash
  autocmd!
  autocmd FileType sh setlocal ts=4 sw=4 expandtab
  autocmd FileType sh setlocal noet
augroup END

" Highlight trailing spaces
match ErrorMsg '\s\+$'

" Enable mouse support
set mouse=a

" Enable clipboard support
set clipboard=unnamedplus

" Status line
set laststatus=2
set showmode

" Colorscheme (you can choose your preferred one)
colorscheme desert

" Plugin support (optional: Uncomment if using a plugin manager like vim-plug)
" call plug#begin('~/.vim/plugged')
" Plug 'dense-analysis/ale'   " For linting
" call plug#end()

" ALE configuration for YAML and Bash (if ale plugin is used)
" let g:ale_linters = {
" \   'yaml': ['yamllint'],
" \   'sh': ['shellcheck'],
" \}
" let g:ale_fixers = {
" \   'yaml': ['prettier'],
" \   'sh': ['shfmt'],
" \}
" let g:ale_fix_on_save = 1

```
