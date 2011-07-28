set nocompatible	" Vim mode vs vi mode
set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
set showmatch		" Highlight closing ), >, }, ], etc...
set ruler			" Show row,col in cmd line
set hlsearch		" Keep previous search highlighted

set ignorecase		" Ignore case in searches
set smartcase		" Don't ignore case if search string contains uppercase letters
set number			" Display line numbers
set nobackup		" No backup files
syntax on
if !has("gui_running")
	colorscheme 256-jungle
endif

" The rest of these options are from mswin.vim to make Vim behave more like
" Windows.
set backspace=indent,eol,start whichwrap+=<,>,[,]
" backspace in Visual mode deletes selection
vnoremap <BS> d
" CTRL-X is Cut
vnoremap <C-X> "+x
" CTRL-C is Copy
vnoremap <C-C> "+y
" CTRL-V is Paste
map <C-V> "+gP
cmap <C-V>	<C-R>+

" Pasting blockwise and linewise selections is not possible in Insert and
" Visual mode without the +virtualedit feature.  They are pasted as if they
" were characterwise instead.
" Uses the paste.vim autoload script.

exe 'inoremap <script> <C-V>' paste#paste_cmd['i']
exe 'vnoremap <script> <C-V>' paste#paste_cmd['v']

" Use CTRL-Q to do what CTRL-V used to do
noremap <C-Q>		<C-V>

" Use CTRL-S for saving, also in Insert mode
noremap <C-S>		:update<CR>
vnoremap <C-S>		<C-C>:update<CR>
inoremap <C-S>		<C-O>:update<CR>

" CTRL-Z is Undo; not in cmdline though
noremap <C-Z> u
inoremap <C-Z> <C-O>u

" CTRL-Y is Redo (although not repeat); not in cmdline though
noremap <C-Y> <C-R>
inoremap <C-Y> <C-O><C-R>

" CTRL-A is Select all
noremap <C-A> gggH<C-O>G
inoremap <C-A> <C-O>gg<C-O>gH<C-O>G
cnoremap <C-A> <C-C>gggH<C-O>G
onoremap <C-A> <C-C>gggH<C-O>G
snoremap <C-A> <C-C>gggH<C-O>G
xnoremap <C-A> <C-C>ggVG

" CTRL-Tab is Next window
noremap <C-Tab> <C-W>w
inoremap <C-Tab> <C-O><C-W>w
cnoremap <C-Tab> <C-C><C-W>w
onoremap <C-Tab> <C-C><C-W>w
