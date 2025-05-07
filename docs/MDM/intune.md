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


## Sécurité

Pour sécuriser l'utilisation de Intune, nous avons mis en place l'authentification MFA (multifacteur) avec l'application Microsoft Authentificator.

![](/img/MFA.png)

L'interface de Intune se présente ainsi, on peut voir les Utilisateurs qui ont été crées ainsi que leur adresse mail sur laquelle ils devront se connecter dans le **portail entreprise**

![](/img/microsoft.png)

Afin de permettre aux utilisateurs d’accéder au portail d’entreprise et d’être gérés via Microsoft Intune, nous leur
avons attribué une licence Intune. Cela permet d’enrôler leurs appareils, d’appliquer les stratégies de sécurité, de
déployer des applications et d'assurer le suivi depuis le centre d'administration.

![](/img/licence.png)

Nous avons ensuite mis en place une authentification multifacteur (MFA) obligatoire pour chaque utilisateur à l’aide
de l’application Microsoft Authenticator. Cette mesure renforce significativement la sécurité de l’environnement
Microsoft Intune, en protégeant l’accès au portail d’entreprise ainsi qu’à l’ensemble des données et ressources de
l’organisme.

![](/img/authentif.png)

## Après installation du portail entreprise

Une fois l'appareil inscrit et remonté dans Intune, nousavons accès à une vue détaillée de ses caractéristiques techniques dans la section "Matériel".\
Cette interface permet de consulter plusieurs informations essentielles telles que : 

- Le modèle et le système d’exploitation de l’appareil, ici un terminal Android de type sdk_gphone64_x86_64.
- L’état de conformité, qui est marqué comme “Conforme”, indiquant que toutes les stratégies de sécurité et de configuration sont bien appliquées.
- L’opérateur mobile, la connectivité (Wi-Fi / GSM), et les adresses MAC, permettant de tracer ou d’analyser l’usage réseau.
- Les informations liées à l’activation EAS (Exchange ActiveSync) pour le lien avec les services de messagerie.
- Le statut de sécurité, avec la confirmation que l’appareil n’est pas rooté, n’est pas jailbreaké, et n’est pas supervisé.

Cette visibilité complète sur le matériel permet à l’administrateur de suivre précisément chaque appareil géré, de vérifier sa conformité, et d’intervenir rapidement en cas de problème ou de perte.

![](/img/compo.png)

Depuis le portail d’administration Microsoft Intune, nous avons une vue centralisée sur l’ensemble des informations liées aux appareils gérés. 
Sur cette interface, il est possible de visualiser :
- Le nombre d’appareils par plateforme (Windows, Android, iOS, etc.),
- L’état de conformité de chaque appareil,
- Les éventuelles erreurs de stratégie ou de déploiement,
- Les actions à distance disponibles (effacement, verrouillage, synchronisation…).

Cette console offre une supervision complète et en temps réel de l’environnement mobile et permet aux administrateurs de réagir rapidement en cas de non-conformité, d'incident ou de vol d’appareil.

![](/img/console.png)

Dans le cadre du déploiement de l'application Outlook, nous avons configuré en amont les paramètres de messagerie afin de renforcer la sécurité et de simplifier l'expérience utilisateur.\
Grâce à la stratégie de configuration d'application déployée via Intune, plusieurs réglages ont été appliqués automatiquement, tels que :
- L’activation de l’authentification biométrique, pour sécuriser l’accès à l’application.
- Le blocage des images externes et des comptes personnels, afin de limiter les risques de fuite de données.
- La synchronisation automatique des calendriers et des e-mails, pour garantir la continuité de service.
- La désactivation de certaines fonctionnalités non essentielles comme Discover, afin de se concentrer sur les besoins professionnels.

En complément, nous avons également activé la prise en charge de S/MIME, avec chiffrement des e-mails et signature numérique, ce qui garantit la confidentialité et l’intégrité des communications.\
Cette stratégie est appliquée automatiquement aux utilisateurs des groupes MDM et Téléphone salarié, ce qui assure un déploiement homogène sur l’ensemble des appareils professionnels.

![](/img/outlook.png) ![](/img/outlook2.png)

En cas de perte ou de vol d’un appareil, Microsoft Intune permet de réagir rapidement pour sécuriser les données de l’entreprise.  
Depuis la console d’administration, l’administrateur peut sélectionner l’appareil concerné et exécuter des actions à distance telles que :

* Le verrouillage de l’appareil, empêchant toute utilisation non autorisée,

* La suppression sélective des données professionnelles, qui efface toutes les applications et données liées à l’entreprise sans impacter les données personnelles,

* Ou encore une réinitialisation complète de l’appareil, si nécessaire.

Dès que l’action est déclenchée, l’utilisateur perd immédiatement l’accès aux ressources de l’entreprise (Outlook, Teams, OneDrive, etc.), ce qui garantit que les informations sensibles ne puissent pas être compromises.

![](/img/vue.png)

Une fois l’effacement ou la suppression d’un appareil effectuée depuis Intune, il n’est plus possible de revenir en arrière.  
Si le téléphone est ensuite retrouvé, l’utilisateur devra :

1. Télécharger à nouveau l’application “Portail d’entreprise” depuis le Play Store,

2. Se reconnecter avec ses identifiants professionnels,

3. Et enfin suivre la procédure d’enrôlement habituelle.

Une fois ces étapes réalisées, toutes les applications professionnelles (Outlook, Authenticator, etc.) ainsi que les stratégies de sécurité et de configuration seront automatiquement réinstallées sur le téléphone.
