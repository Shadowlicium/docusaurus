---
sidebar_position: 2
---


Notre infrastructure sera soutenu sur AWS, le service proposer par Amazon afin de répondre a la demande du client

#### explication de l'infrastructure

![](/img/Project.png)

Le serveur SAMBA qui gère l'ADDS ainsi que NFS seront dans le cloud de AWS relié par un vpn jusqu'au routeur du client, permettant ainsi la communication grâce au pont effectuer.

Prometheus et grafana se partageront aussi un serveur dans la solution cloud de AWS, les données seront visionné par les machines internes du client.