---
sidebar_position: 3
---

### Risque de sécurité de Samba

- maintenir a jour
- droit d'utilisateur trop permissif
- partage de fichier mal configurer
- partage samba ADDS exposé de manière publique

### Mesure de sécurité a mettre en place

- mettre a jour avec les derniers patch de sécurité
- restreindre l'accés de partage aux utilisateurs
- authentification kerberos forte

Mettre en place du monitoring + logs afin de voir les intrusions

### Risque de sécurité NFS

- maintenir a jour
- mauvaise gestion du partage
- attaque par usurpation

### Risque de sécurité internet

- perte internet
- chute de AWS 
- routeur qui tombe

### Mesure de sécurité

- Prévoir un deuxième FAI (voir pour une troisième solution, comme la 5G si possible)
- Prévoir des backup des machines au cas ou + souscrire a une assurance qui prévoit ce risque
- prévoir au moins deux routeurs mis en redondance