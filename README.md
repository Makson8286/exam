# grafana-prometteus_docker-swarm

Hello, in this thread I will show you and tell you how to create a Grafana monitoring system on ubuntu 23.04 LTS in the "Docker cluster" together with "Prometheus, SNMP-Exporter, Alert Manager, CatVisor, Node-Exporter". all the commands that you need to write I will duplicate for you. 
ATTENTION in docker-compose, I create and use my cluster network because I have a network bug and then I can't access my containers.

apt update && apt upgrade -y

sudo apt install apt-transport-https -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update -y

sudo apt install docker-ce -y

sudo usermod -aG docker $USER

apt install docker-compose -y

git clone

