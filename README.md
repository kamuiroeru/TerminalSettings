## めっちゃ雑ですが、cloneしたら、その場で `source dotfiles/README.md` を打ってください。
### Requirements
- zsh
- nvim
- screen

#### インストール処理（ `source dotfiles/README.md` により、以下が実行されます。）
```
mv dotfiles ~
cd ~
ln -s dotfiles/.zshenv .
ln -s dotfiles/.zsh .

# vimはやめた
# ln -s dotfiles/.vimrc .
# ln -s dotfiles/.vim .
ln -s dotfiles/.gitconfig .

# nvim
echo "Install neovim settings?(y/N): "
if read -q; then
    if [ ! -d "$~/.config" ]; then
	mkdir ~/.config
    fi
    ln -s ../dotfiles/.config/nvim .config
else
    echo "Skip!"
fi

# screen
echo "Install screen settings?(y/N): "
if read -q; then
    ln -s dotfiles/.screenrc .
else
    echo "Skip!"
fi

# git alias
git config --global alias.s status
git config --global alias.co checkout
git config --global alias.b branch
git config --global alias.c commit
git config --global alias.d diff
git config --global alias.g grep

# myScript
ln -s dotfiles/.myscript .

echo "Finish!!!"

cp dotfiles/localfiles/zshrc.local ./zsh/zshrc.local
cp dotfiles/localfiles/.gitconfig.local .
echo "$HOME/.gitconfig.localと$HOME/.zsh/zshrc.localを編集してください"
```
