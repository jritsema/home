### dotfiles

```sh
git clone --bare git@github.com:jritsema/dotfiles.git $HOME/.cfg
function config {
   /usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME $@
}
mkdir -p .config-backup
config checkout
if [ $? = 0 ]; then
  echo "Checked out config.";
  else
    echo "Backing up pre-existing dot files.";
    config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
fi;
config checkout
config config status.showUntrackedFiles no
```

vim plugins

```sh
git clone https://github.com/preservim/nerdtree.git $HOME/.vim/pack/plugins/start/nerdtree
git clone https://github.com/frazrepo/vim-rainbow.git $HOME/.vim/pack/plugins/start/vim-rainbow
git clone https://github.com/fatih/vim-go.git $HOME/.vim/pack/plugins/start/vim-go
git clone https://github.com/airblade/vim-gitgutter.git $HOME/.vim/pack/plugins/start/vim-gitgutter
git clone https://github.com/prettier/vim-prettier.git $HOME/.vim/pack/plugins/start/vim-prettier
git clone https://github.com/pangloss/vim-javascript.git $HOME/.vim/pack/plugins/start/vim-javascript
git clone https://github.com/MaxMEllon/vim-jsx-pretty.git $HOME/.vim/pack/plugins/start/vim-jsx-pretty
```
