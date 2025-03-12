---
sidebar_position: 3
---
# Cahier des charges

L’entreprise nous demande de mettre en place une infrastructure afin de centraliser l’authentification de ses utilisateurs, il demande la mise en place d’un contrôleur de domaine Linux Samba AD DS avec le système de partage de fichiers sécurisé sous NFS.

### Il doit donc y avoir : 

- Le déploiement d’un serveur Samba afin d’intégrer des clients Windows et Linux.
- La mise en place d’un serveur NFS pour partage de fichier et gestion des permissions.
- sécurisation du réseau et des accès avec des règles de pare-feu/authentification
- Intégration d’un système de monitoring et de gestion des logs.


### Pour les solution apporté, notre équipe a décidé d’utiliser les applications suivante : 

- **AWS** (infrastructure cloud)
- **Samba** (serveur debian12) il possèdera le dns interne ainsi que la gestion des fichiers de partage (Utilisation de **NFSv4** utilisé) et des utilisateurs 
- **Monitoring** (Grafana + prometheus)
- **Logs** (ELK Stack)

### En matière de sécurité, il y aura : 

- Des groupes sur le cloud
- Le pare-feu : ouverture des ports nécessaire
- droits d’accès utilisateurs pour Samba et NFS
- Chiffrements des connexion ainsi que une authentification forte.

