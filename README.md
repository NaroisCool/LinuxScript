# This a script from Benoit . https://github.com/benoitlavorata

## Tutorial for fresh server installation 

### Install deps
```
sudo apt-get update
apt-get upgrade -y
sudo apt-get install tmux vim wget curl jq git build-essential -y
```
### add firewall
```
apt-get install ufw -y
ufw default allow outgoing
ufw default deny incoming
ufw allow ssh
ufw allow 80/tcp
ufw allow 443/tcp
ufw enable
ufw reload
ufw status
```
### dct
```
mkdir ~/bin
curl -o ~/bin/dct.sh https://raw.githubusercontent.com/NaroisCool/LinuxScript/master/dct.sh
chmod +x ~/bin/dct.sh 
```

```
echo "" >> $HOME/.bashrc && echo 'alias dct="bash ~/bin/dct.sh"' >> $HOME/.bashrc && source $HOME/.bashrc
```

### zsh and oh-my-zsh
```
sudo apt-get install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
ZSH
I usually add the theme af-magic + auto tmux

Edit the conf file
```
cd ~
nano .zshrc
```
Add this at top of file (without the comments)
```
ZSH_TMUX_AUTOSTART=true
ZSH_TMUX_AUTOCONNECT=true
ZSH_TMUX_AUTOQUIT=true
Modify the theme:

ZSH_THEME="af-magic"
Add plugins:

plugins=(
git
tmux 
)
```
Reload:
```
source .zshrc
```
### Tmux
```
cd ~/
touch ~/.tmux.conf
echo "" >> ~/.tmux.conf
echo "set -g status-fg white" >> ~/.tmux.conf
echo "" >> ~/.tmux.conf
echo "set -g status-bg red" >> ~/.tmux.conf
```
### Install docker + docker-compose
```
curl -sSL https://get.docker.com/ | sh
sudo usermod -aG docker falinwa
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
### Set up apps with dct / git
Make default dirs
```
cd ~/
mkdir apps
mkdir dev
mkdir backup
```
Install apps
```
cd apps
dct nginx
dct ide
dct portainer
dct relay
ls -all
```
