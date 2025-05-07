---
sidebar_position: 6
---

# VPN

Nous avons mis en place une solution **VPN sécurisée** avec **Microsoft Tunnel** pour permettre aux utilisateurs mobiles (Android/iOS) d’accéder aux ressources internes de l’entreprise.  
Ce déploiement repose sur :

* une **segmentation des accès** en fonction des rôles métier ;

* l’utilisation de **balises d’étendue** pour une gestion déléguée dans Intune. 

**1\. Mise en place du tunnel VPN**

Un tunnel VPN nommé **Tunnel\_Entreprise** a été déployé pour assurer la connexion sécurisée des appareils.

###  **Détails de configuration :**

| Élément | Valeur |
| ----- | ----- |
| **Nom** | Tunnel\_Entreprise |
| **Adresse IP publique / FQDN** | projetmdm.local |
| **Configuration de serveur** | Entreprise MDM |
| **Mise à jour automatique** | Oui |
| **Limite de mise à jour** | Non |
| **Balises d’étendue affectées** | Par défaut, vpn\_commerciaux, vpn\_rh, vpn\_tech |

![](/img/des.png)


## **2\. Création des profils VPN**

Nous avons défini **trois profils de configuration VPN**, chacun lié à un groupe d’utilisateurs et à une balise d’étendue spécifique.  
Ces profils appliquent des restrictions d’accès en fonction des besoins métiers.

### **Exemple de configuration dans Intune :**

* **Profil\_Tunnel\_Commerciaux** → accès web

* **Profil\_Tunnel\_Tech** → accès aux applis internes (GLPI, Jira…)

* **Profil\_Tunnel\_RH** → accès à l’intranet RH

![](/img/VPN1.png)

## **3\. Attribution des groupes et balises**

Chaque utilisateur est placé dans un groupe Azure AD correspondant à son métier.  
Les profils VPN sont déployés automatiquement en fonction de l’appartenance au groupe, via les **balises d’étendue** associées.

Il faudra mettre les utilisateurs correspondants dans leurs groupes respectifs au fur et à mesure de leurs arrivées dans l’entreprise afin de leurs données accès avec des différentes restriction 

| Groupe Azure AD | Balise d'étendue | Accès VPN |
| ----- | ----- | ----- |
| Groupe\_Commerciaux | vpn\_commerciaux | Accès aux applications web professionnelles |
| Groupe\_Tech | vpn\_tech | Accès aux applications internes spécifiques |
| Groupe\_RH | vpn\_rh | Accès aux portails internes RH |

## **4\. Procédure de gestion des arrivées**

Lors de l’arrivée d’un nouvel utilisateur :

1. L’administrateur ajoute l’utilisateur dans le groupe Azure AD correspondant.

2. Intune attribue automatiquement :

   * l’application Microsoft Defender (client VPN intégré),

   * le bon profil VPN,

   * les droits d’accès liés à sa fonction.

![](/img/VPN1.png]
