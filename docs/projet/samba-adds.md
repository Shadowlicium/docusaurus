---
sidebar_position: 5
---
Samba sera installer sur un debian 12 en cloud sur AWS avec les composants suivant :

CPU : 1\
RAM : 1 Go\
disk : 20 Go\
Version SAMBA : 4.17.12-Debian

Il a tout d'abord été tester en interne dans une vm avant de le transferer sur AWS afin de s'assurer de la fonctionnalité de celui-ci.

Les test réaliser en interne a été :
- La création de l'active directory
- La réalisation d'un dossier de partage nfs
- La création d'utilisateur ainsi que la prise de contrôle d'un utilisateur de l'ad.

### Configuration :

Changer le nom de la machine si nécessaire

```
hostnamectl set-hostname nom_du_serveur
```

Il faudra ensuite modifier la résolution de noms
```
nano /etc/hosts

127.0.0.1		localhost
192.168.100.250	nom_machine.domaine.racine		nom_machine     domaine.racine
```

contenu a valider
```
nano /etc/nsswitch.conf
hosts: files dns
```

Installation des applications et services
```
apt update && apt upgrade -y
export DEBIAN_FRONTEND=noninteractive
apt install acl attr samba samba-dsdb-modules samba-vfs-modules winbind libpam-winbind -y
apt install libnss-winbind libpam-krb5 krb5-config krb5-user dnsutils smbclient ldb-tools -y
apt install ntp ntpdate -y
unset DEBIAN_FRONTEND
```

**Si l'installation ne se fait pas, n'oublier pas de modifier le resolv.conf afin de naviguer sur internet !**

Re-modifier le contenu du fichier\
/etc/resolv.conf
```
search domaine.racine
nameserver 127.0.0.1
```

Effacer le fichier de config samba (par défaut)
```
rm /etc/samba/smb.conf
```

Déployer le domaine ‘domaine.racine’
```
samba-tool domain provision --realm=domaine.racine --domain=domaine --server-role=dc
```

Copier le fichier krb5.conf dans le dossier **/etc**
```
cp /var/lib/samba/private/krb5.conf /etc/krb5.conf
```

Une fois terminé, vérifier que le fichier contient bien les directives suivantes :

```
[libdefaults]
default_realm = domaine.racine
dns_lookup_realm = false
dns_lookup_kdc = true
```

Mise en place du mot de passe de administrator (mdp fort exigé)
```
samba-tool user setpassword administrator
```

Activer les services Samba au démarrage de la machine
```
systemctl unmask samba-ad-dc
systemctl --now enable samba-ad-dc
systemctl disable nmbd smbd
systemctl mask nmbd smbd
```

redemarrer ensuite la machine puis on vérifie le fonctionnement des services **Kerberos** et **DNS**

```
kinit administrator
klist
dig @localhost nom_machine.domaine.racine
```

### Rejoindre le domaine

Pour rejoindre le domaine il suffira d'entrer sur une machine cliente

```
realm join nom.domaine.racine
```

### Annexe

exemple d'une config smb pour samba

![](/img/smb.png)

exemple d'une configuration krb5

![](/img/krb5.png)