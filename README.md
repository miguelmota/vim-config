# .vim

> My `~/.vim` and `~/.vimrc` configuration.

## Install

(Adjust accordingly)

```bash
# Create dotfiles directory
mkdir ~/.dotfiles

# Clone repo
git clone https://github.com/miguelmota/vim-config.git ~/.dotfiles/.vim

# Create backup directory
mkdir -p ~/.vim/backup

# Create symlinks
ln -s ~/.dotfiles/.vim ~/.vim
ln -s ~/.dotfiles/.vim/.vimrc ~/.vimrc

# Install Vundle bundle manager
git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle

# Install bundles (ignore errors about uninstalled bundles)
vim +BundleInstall +qall
```

Vundle commands

```bash
# Install bundles
vim +BundleInstall +qall

# Remove bundles
vim +BundleClean

# Update bundles
vim +BundleUpdate
```

## Required dependencies

lua

```bash
# mac
brew install vim --with-lua
```

For installing vim with lua on Ubuntu see this gist [gist](https://gist.github.com/techgaun/2fe3dd3d004d7320a68d)

[ctags](http://ctags.sourceforge.net/) for [ctrlp](https://github.com/kien/ctrlp.vim) and [tagbar](https://github.com/majutsushi/tagbar) plugins

```bash
# Mac OSX
brew install ctags

# Ubuntu
sudo apt-get install exuberant-ctags

# fedora
sudo dnf install ctags
```

[Tern](https://github.com/marijnh/tern) for [tern](https://github.com/marijnh/tern_for_vim) plugin

Make sure to have [Node.js](http://nodejs.org/) and [npm](https://www.npmjs.org/) installed first. You can use [nvm](https://github.com/nvm-sh/nvm).

```bash
cd ~/.vim/bundle/tern_for_vim

npm install
```

YouCompleteMe completers

```bash
# ubuntu requirements
sudo apt-get install python-dev python3-dev

# fedora
sudo dnf install cmake gcc-c++ python-devel python3-devel

# arch

```

```bash
cd ~/.vim/bundle/YouCompleteMe

git submodule update --init --recursive

# tern is deprecated
rm ~/.vim/bundle/YouCompleteMe/third_party/ycmd/third_party/tern_runtime/node_modules

./install.py --clang-completer --go-completer --ts-completer --js-completer --racer-completer

# alternatively, compile with everything enabled
./install.py --all
```

Getting Go v1.11 auto completer to work

```bash
cd ~/.vim/bundle/YouCompleteMe/third_party/ycmd/third_party/
rm -rf gocode
git clone git@github.com:mdempsky/gocode.git
cd gocode
go mod init
go build .
```

vim-completor

javascript autocompleter

```bash
cd ~/.vim/bundle/completor.vim/
# make sure to install tern first before this
make js
```

Rust autocompleter

```bash
# requires nightly rust
rustup toolchain add nightly
cargo +nightly install racer
```

Python autocompleter

```bash
pip install jedi
```

NOTE: if YouComplete server crashes, try running install script (shown above) again:

Powerline

[Powerline Installation instructions](http://powerline.readthedocs.org/en/latest/installation/osx.html)

vim-go

```bash
go get -u gopkg.in/alecthomas/gometalinter.v2
gometalinter --install
```

[the_silver_searcher](https://github.com/ggreer/the_silver_searcher) for content searching (used with [FZF](https://github.com/junegunn/fzf.vim))

```bash
brew install the_silver_searcher
```

All done.

## Installing bundles

Run `BundleInstall` after adding a [Vundle](https://github.com/gmarik/Vundle.vim) bundle in `.vimrc`

## Updating

```bash
wget https://raw.github.com/miguelmota/vim-config/master/update.sh -O - | bash
```

## Reference

Below are references for shortcuts and key bindings (to help me remember).

toggle comment

```
<leader>c<space>
```

uncomment comment

```
<leader>cu
```

comment out using asterisks

```
<leader>cs
```

ctrlp Search/open files:

`Ctrl+p`

```
horizonal split
<c-x>

vertical split
<c-v>
```

Toggle fullscreen for a window (like in tmux)

```
<C-w> z
```

ctrlp shortcuts

[source](https://github.com/kien/ctrlp.vim)

Turn off search highlight

```
:noh
```

```bash
Press <F5> to purge the cache for the current directory to get new files.
Press <c-f> and <c-b> to cycle between modes.
Press <c-d> to switch to filename only search instead of full path.
Press <c-r> to switch to regexp mode.
Use <c-j>, <c-k> or the arrow keys to navigate the result list.
Use <c-t> or <c-v>, <c-x> to open the selected entry in a new tab or in a new split.
Use <c-n>, <c-p> to select the next/previous string in the prompt's history.
Use <c-y> to create a new file and its parent directories.
Use <c-z> to mark/unmark multiple files and <c-o> to open them.
```

Toggle NERDTree:

`\ n`

Comment toggle:

Hightlight text in visual mode then type `\ cc`

`\ cl|cb` - aligned to left
`\ cm` - multiline
`\ cs` - sexily

Close tag:

`Ctr + Shift + _`

Window switching:

`Ctr + <movement key>`

Paste mode toggle:

`F9`

List mode toggle:

`F10`

Strip whitespace:

`\ ss`

Tabs to whitespace:

\ ts`
Reload vimrc:

`\ rv`

dit #delete everything in tag
vit
cit # change insidej tag
yit

Eady Motion:

`\ \ w`

Buffer shortcuts

```
:ls - list buffers
:buffer <num>
:bn
:bp
```

Buffergator toggle panel:

`\ b`

Buffergator shortcuts:

```bash
<C-V> Open in vertical split
<C-S> Open in horizontal split
<C-T> Open in tab
Use `[b` (or <M-b>) and `]b` (or <M-S-b>) to flip through the most-recently
Use `<Leader><LEFT>`, `<Leader><UP>`, `<Leader><RIGHT>`, `<Leader><DOWN>` to
```

Mini Buffer Explorer

toggle panel

`\ e`

Switch to buffer

```bash
 number<C-^>
 ```

Recording

```
q<letter> Start recording
q Stop recording
@<letter> Replay recording
```

vim-node open required module file

`gf` on `require('.')` to open ./index.js`

ConqueTerm

run iteractive prompt

```
:ConqueTerm bash
```

Git

Common commands

```
:Gstatus
:Gdiff :0
:Gdiff [revision]
:Gdiff ~3
:Gblame
:Glog
:Gcommit -m "message"
:Gremove
```

Vim over (substitution preview)

```
:OverCommandLine

" shortcut"
\ fr
```

Vim obsession

```
:mksession
:source Session.vim
```

Vimux

```
\ x # prompt command
\ nt # npm test
```

Tmux complete

```
C-x C-u  # autcomplete
```

Multiple Cursors

```
C-n in Normal Mode
C-n again to select next occurance
v to go into Visual Mode after selections

C-p in Visual Mode go back to previous cursor location
C-x skip current location

:'<,'>MultipleCursorsFind <regex>
```

Number toggle

```
<ctrl-n>
```

Syntastic

```
# toggle lint error list
:lopen
:lclose
```

##### Indentation

Vim defaults ([source](http://stackoverflow.com/questions/235839/how-do-i-indent-multiple-lines-quickly-in-vi))

```bash
>>   Indent line by shiftwidth spaces
<<   De-indent line by shiftwidth spaces
5>>  Indent 5 lines
5==  Re-indent 5 lines

>%   Increase indent of a braced or bracketed block (place cursor on brace first)
=%   Reindent a braced or bracketed block (cursor on brace)
<%   Decrease indent of a braced or bracketed block (cursor on brace)
]p   Paste text, aligning indentation with surroundings

=i{  Re-indent the "inner block", i.e. the contents of the block
=a{  Re-indent "a block", i.e. block and containing braces
=2a{ Re-indent "2 blocks", i.e. this block and containing block

>i{  Increase inner block indent
<i{  Decrease inner block indent
```

Ack

```bash
:Ack -i 'util' -H 'app/'
```

##### Tern commands

[source](https://github.com/marijnh/tern_for_vim)

```bash
TernDef: Jump to the definition of the thing under the cursor.
TernDoc: Look up the documentation of something.
TernType: Find the type of the thing under the cursor.
TernRefs: Show all references to the variable or property under the cursor.
TernRename: Rename the variable under the cursor.

<Leader> td	:TernDoc	Documentation under cursor
<Leader> tb	:TernDocBrowse	Browse documentation
<Leader> tt	:TernType	Type hints
<Leader> td	:TernDef	Jump to definition (yes, 'td' is duplicated)
<Leader> tpd	:TernDefPreview	Jump to definition inside preview
<Leader> tsd	:TernDefSplit	Definition in new split
<Leader> ttd	:TernDefTab	Definition in new tab
<Leader> tr	:TernRefs	All references under cursor
<Leader> tR	:TernRename	Rename variable
```

##### Vim fugitive commands

```
:help fugitive
:Gblame
:GBrowse
```

##### Lisp Swank server

```
# start server
:call SlimvConnectSwank()

# in source file, white over text do the following to:
,d to eval defun
,e to eval current expression
,h hyperspec
,s to describe symbol
,g set package
,W wrap in pair of parens
,O split
,J join
,> move paren right
,< move paren left
,o some perf stuff
,I remove line but
,D compile defun
,F compile file
,L compile and load
```

## License

MIT