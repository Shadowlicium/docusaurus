---
sidebar_position: 6
---

Le serveur NFS partagera les mêmes ressources que le serveur samba-adds


## 1. Installer les paquets NFS


Sur le **serveur** :
```
sudo apt update
sudo apt install nfs-kernel-server
```

sur le **client**

```
sudo apt install nfs-common
```

## 2. Configurer le serveur NFSv4

#### -Créer le point d'export principal (root NFS)

NFSv4 utilise un point d'ancrage hnique. Créez un dossier dédié :
```
sudo mkdir -p /srv/nfs/share
```

Définir les permissions : 
```
sudo chown -R nobody:nogroup /srv/nfs
sudo chmod 755 /srv/nfs
sudo chmod 777 /srv/nfs/share
```

#### -Configurer les exports NFS

Ouvrir le fichier de configuration :
```
sudo nano /etc/exports
```
Ajouter cette ligne pour un partage sécurisé :
```
/srv/nfs4 192.168.1.0/24(ro,fsid=0,no_subtree_check,async)
/srv/nfs4/share 192.168.1.0/24(rw,no_subtree_check,async)
```

## 3. Appliquer les changements et activer NFSv4

Activer NFSv4 en ajustant le fichier de configuration :
```
sudo nano /etc/default/nfs-kernel-server
```
Ajouter
```
RPCNFSDOPTS="--nfs-version 4"
```

Recharger les exports et redémarrez le service :
```
sudo exportfs -rav
sudo systemctl restart nfs-server
sudo systemctl enable nfs-server
```

## 4. Configurer le pare-feu (si activé)

Autoriser le trafic NFS : 

```
sudo ufw allow from x.x.x.x/24 to any port nfs
sudo ufw reload
```

## 5. Monter le partage NFSv4 sur le client

Créer un dossier local pour monter le partage :
```
sudo mkdir -p /mnt/nfs_share
```

Monter le partage sur votre client:
```
sudo mount -t nfs -o vers=4 x.x.x.x:/share /mnt/nfs4_share
```
(remplacer x.x.x.x par l'ip de votre serveur NFS)

Pour un montage automatique au démarrage, ajouter cette ligne dans **/etc/fstab** :
```
x.x.x.x:/share /mnt/nfs4_share nfs4 defaults 0 0
```

## 6. Sécuriser davantage NFSv4

- Limiter les accès en restreignant les IPs autorisées dans /etc/exports.
- Activer Kerberos afin d'autoriser l'authentificiation obligatoire en utilisant NFSv4
- Verrouiller les permission avec chmod et chown afin de restreindre l'accès de certain document/fichier a des utilisateur/groupe.

## Vérification

Sur le serveur : 
```
sudo exportfs -v
```
Sur le client :
```
mount | grep nfs
```
