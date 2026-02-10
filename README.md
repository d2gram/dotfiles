# how-to-recover
```bash
alias dot='git --git-dir=$HOME/.dotfiles --work-tree=$HOME'

git clone --bare https://github.com/d2gram/dotfiles.git $HOME/.dotfiles

dot checkout
```

# conflict resolve
```bash
mkdir -p ~/.dotfiles-backup
dot checkout 2>&1 | grep "^\t" | awk '{print $1}' | xargs -I{} mv {} ~/.dotfiles-backup/{}

dot checkout

dot config --local status.showUntrackedFiles no
```

# install eza (in deb/ubt)
```bash
sudo apt install -y gpg 
sudo mkdir -p /etc/apt/keyrings
wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
sudo apt update
sudo apt install -y eza
```
(shell script from eza's official repository)
