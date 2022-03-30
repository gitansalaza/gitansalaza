# Docker Installation

# Task Summary
1. Update the repositories.
2. Install the essential packages.
3. Set up the gpg docker certificates.
4. Add thte docker repository.
5. Refresh the repositories one more time.
6. Install docker-ce packages and its dependencies.
7. Verify docker is installed and running.
8. Create docker group and assign it to the current $USER

# Installing Docker in Linux Mint
```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=$(dpkg --print-architecture)] https://download.docker.com/linux/ubuntu $(. /etc/os-release; echo "$UBUNTU_CODENAME") stable"
sudo apt-get update
sudo apt-get install -y docker-ce
sudo systemctl status docker
sudo usermod -aG docker $USER
su - $USER
newgrp docker
id $USER
```

# Installing Docker in Ubuntu
```
sudo apt-get update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
apt-cache policy docker-ce
sudo apt install docker-ce
sudo systemctl status docker
sudo usermod -aG docker ${USER}
su - ${USER}
```

# Verify docker details and/or is running
Client version
```
docker --version
```

Client and server version
```
docker vesion
docker info
```

Service status
```
sudo systemctl status docker
```

All of them
```
docker --version
docker vesion
docker info
sudo systemctl status docker
```

# References
- [https://docs.docker.com/engine/install](https://docs.docker.com/engine/install)
- [https://linuxhint.com/install_configure_docker_ubuntu](https://linuxhint.com/install_configure_docker_ubuntu)