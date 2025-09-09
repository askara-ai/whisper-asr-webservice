# Installation procedure

Install upgrades if any :

```
sudo yum update
sudo yum upgrade
```

Install git, htop, docker : 

```
sudo yum install git htop docker
sudo service docker start
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```

Install docker compose (https://stackoverflow.com/questions/63708035/installing-docker-compose-on-amazon-ec2-linux-2-9kb-docker-compose-file) : 

```
sudo curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-$(uname -m) -o /usr/libexec/docker/cli-plugins/docker-compose
sudo chmod +x /usr/libexec/docker/cli-plugins/docker-compose
docker compose version
```

Install zsh & ohMyZsh : 

```
sudo yum -y install zsh util-linux-user
sudo chsh -s "$(which zsh)"
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

Activate the OhMyZsh theme Powerlevel10k.
Edit the file and add `ZSH_THEME="powerlevel10k/powerlevel10k"`

```
nano $HOME/.zshrc
source $HOME/.zshrc
```

Copy the content of the `.p10k.zsh` file into `$HOME/.p10k.zsh`
Replace `askara-NAME ENV` with the name of the server and the env.


Add some custom aliases in `$HOME/.zshrc` :

```
# @see https://stackoverflow.com/a/79601412/1756667
alias dcu="docker compose up -d"
alias dcs="docker compose stop"
alias dcex="docker compose exec"
alias dcl="docker compose logs --tail=10 -f"
```