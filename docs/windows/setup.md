# Setup Windows

Here is a little reminder to setup windows for power users (aka. with Linux on it :smile: )

## [Optional] Rename your laptop
If you want to have a clean/cool prompt, you should change your laptop default name (most of the time something like: DESKTOP-458DF)  to a new one (a short name of your choice).

* Go to `Start > Settings > System > About`
* Click on `Rename this PC`
* Restart your computer

## [Optional] Rename your user folder
As the last step, if you want to have a clean/cool prompt, you should change your windows user folder if it is truncated (that was the case for me. eg. `arthu` instead of wanted username `arthy`).

To do so, follow [this article](https://www.minitool.com/news/change-user-folder-name-windows-10.html)

## Install Windows Subsystem for Linux (WSL 2)
Follow [this article](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to install Ubuntu within your windows

* Install Docker on your desktop natively (without emulation). Follow [this article](https://docs.docker.com/docker-for-windows/wsl/)

## Install Windows terminal
If you want to use a great terminal, [install new Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started)

You may want to change some settings:

* Update `Default profile` to Ubuntu to start it when you open Windows terminal
* In `Ubuntu` profile, go to `Appearance` to `change cursor shape` to `filled box` - this helps on vim prompt
* If listenings windows bells sound is not your hobby, I suggest you to change it to flash. To do so, in `Ubuntu` profile, go to `Advanced` to change `Bell notification style` to `Flash window`
* Do not forget to save your changes in `Settings` page

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

Add the content of the public key (`~/.ssh/id_rsa.pub`) to [your Github account keys](https://github.com/settings/keys)

#### Setup .gitconfig

`~/.gitconfigs/company.gitconfig`
```ini
[user]
        email = arthur.mauvezin@company.com
        name = Arthur MAUVEZIN
```

`~/.gitconfig`
```ini
[user]
        email = arthur.mauvezin@gmail.com
        name = Arthur MAUVEZIN

# Use includeIf to commit with different accounts depending on the parent folder
[includeIf "gitdir:~/company/"]
  path = .gitconfigs/company.gitconfig

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

Test the installation with the following command:
```bash
python -V
```

!!! information
    If the last command prompts something like `Python 3.8.10`, then it's good :smile: !

### oh-my-zsh
```bash
sudo apt install zsh
chsh -s $(which zsh)
```

#### Follow [official instructions](https://ohmyz.sh/#install)
In `~/.zshrc`, modify:

* theme to `bira`
* add plugins: git docker gitignore

#### Setup useful scripts
Create folder
```bash
mkdir .oh-my-zsh/functions
```

Add following line to `~/.zshrc`
```bash
autoload -Uz $ZSH/functions/*(.:t)
```

Source `~/.zshrc` file
```bash
source ~/.zshrc
```

Now, all files put in `~/.oh-my-zsh/functions` folder will be available as commands

See [this kind of file](https://gist.github.com/arthurmauvezin/694d1b9ee1cbb3d82b40d0f05f0238a4) for example




