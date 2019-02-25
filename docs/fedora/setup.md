# Setup Fedora

## Tools
```bash
sudo dnf -y install vim
sudo dnf -y install htop
```

## Chrome (change with fedo28)
```bash
sudo bash -c "cat >> /etc/yum.repos.d/google-chrome.repo" << EOF
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/x86_64
enabled=1
gpgcheck=1
gpgkey=https://dl.google.com/linux/linux_signing_key.pub
EOF
sudo dnf install google-chrome-stable
```

## Franz 5.0
```bash
mkdir -p ~/software/franz && cd ~/software/franz
wget https://github.com/meetfranz/franz/releases/download/v5.0.0-beta.18/franz-5.0.0-beta.18-x86_64.AppImage
chmod +x franz-5.0.0-beta.18-x86_64.AppImage
./franz-5.0.0-beta.18-x86_64.AppImage
```

## Generate SSH Key
```bash
ssh-keygen -t rsa -C <mail_address>
```

## Sublime text
```bash
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
sudo dnf install sublime-text
```

## Forticlient SSL VPN
```bash
sudo dnf install NetworkManager-fortisslvpn-gnome
```

### Start VPN
```bash
sudo openfortivpn <host>:<port> -u <login> -p <password> --trusted-cert <cert>
sudo openfortivpn
```
#### Default arguments
```bash
# IN /etc/openfortivpn/config
host = vpn.mycompany.com
port = 443
username = <username>
password = <password>
trusted-cert = <trusted_cert>
```

## oh-my-zsh
```bash
sudo dnf install zsh util-linux-user git
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
chsh -s $(which zsh)
```

## Docker
```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce
sudo usermod -aG docker $USER
sudo systemctl start docker
sudo systemctl enable docker
# To check
mkdir -p ~/.oh-my-zsh/plugins/docker/\ncurl -fLo ~/.oh-my-zsh/plugins/docker/_docker https://raw.github.com/felixr/docker-zsh-completion/master/_docker
```

## Docker-compose
```bash
sudo curl -L https://github.com/docker/compose/releases/download/1.21.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose\n
sudo chmod +x /usr/local/bin/docker-compose
mkdir -p ~/.zsh/completion
curl -L https://raw.githubusercontent.com/docker/compose/1.21.0/contrib/completion/zsh/_docker-compose > ~/.zsh/completion/_docker-compose
# To check
compinit
```

## Postman
```bash
```

## Software - Must be installed
* chrome
* Franz
* sublimetext
* postman
* docker
* docker-compose
* forticlient
* firefox

## Software - Could be installed
* minikube
* arduino
* calibre
* oh-my-zsh
* cerebro
* ditaa
* rancher-compose
* rancher-cli

## bluetooth software (not sure if I should keep it)
```bash
sudo dnf install bluez-hid2hci
```

## gnome themes and tweak tools
```bash
sudo dnf install gnome-tweak-tool.noarch
```
From here setup :
* Dark theme
* Caps lock as CTRL

## Go
```bash
mkdir -p ~/go/bin
wget https://dl.google.com/go/go1.10.2.linux-amd64.tar.gz -O - | sudo tar -xzC test
```

```bash
# Add in .zshenv
typeset -U path
path=(/usr/local/go/bin ~/go/bin $path[@])
```

## Google Play Music Desktop Player
See this link : [Install GPMDP](https://www.googleplaymusicdesktopplayer.com/#!)
### Add dark theme
Add this repo to .local directory and configure gpmdp to point on it
```bash
git clone https://github.com/ronilaukkarinen/gpmdp-dark-theme.git
```

## Set vim command line shortcut
### For bash
```bash
bash -c "cat >> ~/.inputrc" << EOF
set editing-mode vi
set keymap vi-command
EOF
```
## For zsh
```bash
echo "bindkey -v" >> .zshrc
```
