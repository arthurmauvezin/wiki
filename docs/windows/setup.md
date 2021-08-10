# Setup Windows

Here is a little reminder to setup windows for power users (aka. with Linux on it :smile: )

## Install Windows Subsystem for Linux (WSL 2)
Follow [this article](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to install Ubuntu within your windows

* Install Docker on your desktop natively (without emulation). Follow [this article](https://docs.docker.com/docker-for-windows/wsl/)

## Install Windows terminal
If you want to use a great terminal, [install new Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started)

## Install Visual Studio Code and setup it
* [Install VS Code](https://code.visualstudio.com/docs/?dv=win)
* [Install wsl code extension and learn to use it](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode)
* [Setup VS Code to use Docker remote container](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers)


## Setup Ubuntu
### Git
Setup Git with [this link](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-git)

#### To create ssh key
```bash
ssh-keygen -t rsa -C arthur.mauvezin@gmail.com
```

#### Setup .gitconfig

`~/.gitconfigs/perso.gitconfig`
```ini
[user]
        email = arthur.mauvezin@gmail.com
        name = Arthur MAUVEZIN
```

`~/.gitconfigs/company.gitconfig`
```ini
[user]
        email = arthur.mauvezin@company.com
        name = Arthur MAUVEZIN
```

`~/.giconfig`
```ini
[includeIf "gitdir:~/company/"]
  path = .gitconfigs/company.gitconfig
[includeIf "gitdir:~/perso/"]
  path = .gitconfigs/perso.gitconfig

[push]
	default = simple
	recurseSubmodules = on-demand
[core]
	editor = vim
[alias]
	clo = clone
	co = checkout
	st = status
	pur = pull
	ci = commit
	rc = rebase
	lg = log -M --decorate --graph
	tree = log --oneline --decorate --graph
	lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
	br = branch
	sth = stash
[credential]
	helper = cache --timeout=604800
[init]
	templatedir = ~/.git_template
[diff]
	submodule = log
[status]
	submodulesummary = 1
```

### Python
```bash
sudo apt install python3 python3-pip python-is-python3
```

### oh-my-zsh
```bash
sudo apt install zsh
chsh -s $(which zsh)
```

#### Follow [official instructions](https://ohmyz.sh/#install)
In `~/.zshrc`, modify:

* theme to `bira`
* add plugins: git docker gitignore



