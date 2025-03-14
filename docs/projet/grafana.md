---
sidebar_popsition: 8
---
 
Grafana ainsi que prometheus seront installés sur un debian 12 dans AWS avec la composition suivante :

CPU : 1\
RAM : 1 Go\
disk : 20 Go

### Installation grafana

```
apt install grafana -y
```

activer grafana
```
systemctl enable grafana-server
systemctl start grafana-server
```

### Installation prometheus
```
wget https://github.com/prometheus/prometheus/releases/download/v2.51.2/prometheus-2.51.2.linux-amd64.tar.gz
```

extraction du tar.gr

```
tar xvf prometheus-2.51.2.linux-amd64.tar.gz
```

déplacer les dossiers au bonnes endroits

```
cd prometheus-2.51.2.linux-amd64
mv prometheus promtool /usr/local/bin/
mv consoles/ console_libraries/ /etc/prometheus/
mv prometheus.yml /etc/prometheus/
```