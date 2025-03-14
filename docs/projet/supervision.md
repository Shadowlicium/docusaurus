---
sidebar_popsition: 8
---
 
Grafana ainsi que prometheus seront installés sur un debian 12 dans AWS avec la composition suivante :

CPU : 1\
RAM : 1 Go\
disk : 20 Go

Grafana permettra de monitorer le serveur samba sur AWS
### Installation grafana

```
sudo apt install -y apt-transport-https software-properties-common
sudo wget -q -O /usr/share/keyrings/grafana.key https://packages.grafana.com/gpg.key
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt update
apt install grafana -y
```
Activer grafana
```
systemctl enable grafana-server
systemctl start grafana-server
```

### Installation prometheus
```
wget https://github.com/prometheus/prometheus/releases/download/v2.51.2/prometheus-2.51.2.linux-amd64.tar.gz
```

Extraction du tar.gr

```
tar xvf prometheus-2.51.2.linux-amd64.tar.gz
```

Déplacer les dossiers au bonnes endroits

```
cd prometheus-2.51.2.linux-amd64
mv prometheus promtool /usr/local/bin/
mv consoles/ console_libraries/ /etc/prometheus/
mv prometheus.yml /etc/prometheus/
```

Créer le service systemd
```
nano /etc/systemd/system/prometheus.service
```
![](/img/prom-serv.png)


Installation du node de prometheus

```
wget https://github.com/prometheus/node_exporter/releases/download/v1.7.0/node_exporter-1.7.0.linux-amd64.tar.gz
tar xvf node_exporter-1.7.0.linux-amd64.tar.gz
mv node_exporter-1.7.0.linux-amd64/node_exporter /usr/local/bin/
```
Créer le service 
```
nano /etc/systemd/system/node_exporter.service
```
![](/img/prom-node.png)


Initialisation
```
sudo systemctl daemon-reload
sudo systemctl enable prometheus node_exporter
sudo systemctl start prometheus node_exporter
```