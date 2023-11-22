---
layout: default
title: linux
parent: Cheatsheet
nav_order: 2
---

# Linux

## [Oh my ZSH with zsh-autosuggestions zsh-syntax-highlighting zsh-fast-syntax-highlighting and zsh-autocomplete](https://gist.github.com/n1snt/454b879b8f0b7995740ae04c5fb5b7df)

```bash
sudo apt install zsh-autosuggestions zsh-syntax-highlighting zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/fast-syntax-highlighting
git clone https://github.com/marlonrichert/zsh-autocomplete.git ~/.oh-my-zsh/custom/plugins/zsh-autocomplete

# ~/.zshrc
# plugins=(git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-autocomplete)
```

## [Install NVM](https://github.com/nvm-sh/nvm#installing-and-updating)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```

## [Install RVM](https://github.com/rvm/rvm#installing-rvm)

```bash
gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://get.rvm.io | bash -s stable
```

## [Install Pyenv](https://github.com/pyenv/pyenv#installation)

```bash
curl https://pyenv.run | bash
```

## [color emoji not showing up at all in Chrome, only partially in Firefox](https://askubuntu.com/questions/1029661/18-04-color-emoji-not-showing-up-at-all-in-chrome-only-partially-in-firefox)

```bash
nano ~/.config/fontconfig/conf.d/01-emoji.conf
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>serif</family>
    <prefer>
      <family>Noto Color Emoji</family>
    </prefer>
  </alias>
  <alias>
    <family>sans-serif</family>
    <prefer>
      <family>Noto Color Emoji</family>
    </prefer>
  </alias>
  <alias>
    <family>monospace</family>
    <prefer>
      <family>Noto Color Emoji</family>
    </prefer>
  </alias>
</fontconfig>
```

```bash
fc-cache -f -v
```