---
sidebar_position: 2
---

# Intune

Intune sera l'application utiliser afin de gérer nos appareils mobiles.

C'est une application créer et mise en place par Microsoft et permet son utilisation cloud.
Notre test sera réaliser avec la version gratuite de 30 jours. 

Dans notre cas on voudra proposer les applications de l'entreprise qui se téléchargeront automatiquement tout en veillant a désactiver certains fonctionnalités et rajouter plus de terme de sécurité.

## Pré-requis : 

Intune prend en charge les appareils **Android version 8.0 ou plus** mais possède plus de contrôle sur tout les **android 10 ou plus**

Il faudra avoir créer un compte microsoft dans l'entreprise qui permettra de rejoindre le portail Intune que ce soit pour l'administrateur ou les utilisateurs.

Chaque appareil mobile a controller il faudra : 

- Installer le portail d'entreprise Intune depuis le Play Store.

- Se connecter avec le compte Microsoft Professionnel.

- Autoriser les droits d'administration

- Enroler les appareils pour qu'ils soient reconnus par le controleur Intune.


## Sécuriter

Pour sécuriser l'utilisation de Intune, nous avons mis en place l'authentification MFA (multifacteur) avec l'application Microsoft Authentificator.

![](/img/MFA.png)

L'interface de Intune se présente ainsi, on peut voir les Utilisateurs qui ont été crées ainsi que leur adresse mail sur laquelle ils devront se connecter dans le **portail entreprise**

![](/img/microsoft.png)

Afin de permettre aux utilisateurs d’accéder au portail d’entreprise et d’être gérés via Microsoft Intune, nous leur
avons attribué une licence Intune. Cela permet d’enrôler leurs appareils, d’appliquer les stratégies de sécurité, de
déployer des applications et d'assurer le suivi depuis le centre d'administration.

![](/img/licence.png)
