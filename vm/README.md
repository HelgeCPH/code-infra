Setup the Machine
=================

  * Install Vagrant, see https://www.vagrantup.com/docs/installation/
  * Clone this repository to your machine `git clone https://github.com/HelgeCPH/code-infra.git`
  * Navigate to the `vm` folder
  * Run `vagrant up`


Origins
=======


The Vagrant file is based on the following resources

  * https://github.com/praqma-training/code-infra
  * https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart
  * https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04


On a fresh 'real' Ubuntu Xenial (16.04) machine one would do the following to setup Praqma's infrastructure code.

```
root@ubuntu-xenial:~# 
root@ubuntu-xenial:~# adduser infra
root@ubuntu-xenial:~# usermod -aG sudo infra
root@ubuntu-xenial:~# su - infra

infra@ubuntu-xenial:~# sudo apt-get update
infra@ubuntu-xenial:~# sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
infra@ubuntu-xenial:~# echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list
infra@ubuntu-xenial:~# sudo apt-get update
infra@ubuntu-xenial:~# apt-cache policy docker-engine
infra@ubuntu-xenial:~# sudo apt-get install -y docker-engine
infra@ubuntu-xenial:~# sudo systemctl status docker
infra@ubuntu-xenial:~# sudo usermod -aG docker $(whoami)
infra@ubuntu-xenial:~# sudo apt-get install -y docker-compose
infra@ubuntu-xenial:~# mkdir dvl
infra@ubuntu-xenial:~# cd dvl
infra@ubuntu-xenial:~# git clone https://github.com/praqma-training/code-infra.git
infra@ubuntu-xenial:~# cd code-infra/containers/
infra@ubuntu-xenial:~# sudo ./create-homes.sh
infra@ubuntu-xenial:~# nano docker-compose.yml
infra@ubuntu-xenial:~# sudo systemctl status docker
infra@ubuntu-xenial:~# sudo docker-compose up -d
infra@ubuntu-xenial:~# sudo docker-compose stop

```

In the docker-compose.yml the first two lines have to be commented out. Otherwise it won't work with `docker-compose` (v. )



