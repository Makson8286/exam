# grafana-prometeus_docker-cluster
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Hello, in this thread I will show you and tell you how to create a Grafana monitoring system on ubuntu 23.04 LTS in the "Docker cluster" together with "Prometheus, SNMP-Exporter, Alert Manager, CatVisor, Node-Exporter". all the commands that you need to write I will duplicate for you. 
ATTENTION in docker-compose, I create and use my cluster network because I have a network bug and then I can't access my containers.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

apt update && apt upgrade -y

sudo apt install apt-transport-https -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update -y

sudo apt install docker-ce -y

sudo usermod -aG docker $USER

apt install docker-compose -y

git clone https://github.com/Makson8286/grafana.git

cd grafana

docker-compose up -d

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Now that we have everything up and running, we need to add our users to Prometheus whom we will monitor, to do this, follow the path: /var/lib/docker/volumes/grafana_prom-configs/_data/prometheus.yml

An example of what it looks like for me is in the file "example.yml"

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Next, set up Grafana:
IN THE BROWTHER-------> http://your-ip:3000

Login: admin

Password: admin

----> Data sources and click Create new and select Prometheus

In the "Prometheus server URL" row write: http://prometheus:9090

And click "Save&test" when the green window appears, we can exit from there.

Next, go to "Dashboards" click "New" --> "Import" and add our graphs 

P.S. You need to write the ID in the list below they will be indicated first 

Here are the ones we will use today: 
1. "11939" Docker Swarm Dashboard
2. "15798" Docker container monitoring
3. "14857" SNMP monitoring (Mikrotik, SNMP, SNMP V3, SNMP Exporter)
4. "14694" Windows monitoring
5. "1860" Linux monitoring

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Setup alerts in telegram

Go to telegram and find the bot "TelepushBot" and run it. He will send you your token. 

Insert the token that the bot sent you in the file "Alertmanager.yml"

In the "docker-compose.yml" file, in the line with the path to the "alertmanager.yml" and "alert.rules.yml" file, change to your path.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

In order for grafana to see your client, follow these steps.

apt update && apt upgrade -y

sudo apt install apt-transport-https -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update -y

sudo apt install docker-ce -y

sudo usermod -aG docker $USER

docker run -d --name node-exporter -p 9100:9100 bitnami/node-exporter:latest

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
