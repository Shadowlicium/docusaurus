---
sidebar_position: 5
---

# Portail Entreprise

![](/img/portail.png) 

Une fois l’application lancée, l’utilisateur se connectera avec le mail et le mot de passe qu’on lui aura fourni et
l’appareil remontera automatiquement. 
Attention ! L'authentification à deux facteurs est nécessaire pour enrôler
l’appareil.

À gauche, l’interface de l’application “Portail d’entreprise” permet à l’utilisateur de gérer son profil professionnel,
de synchroniser les stratégies de l’organisation, ou de déclencher un support. Cette application est essentielle pour
l’enrôlement et la gestion continue de l’appareil mobile.
À droite, l’application “Microsoft Authenticator” affiche le code à usage unique (OTP) généré pour
l’authentification multifacteur. Elle permet également de valider des connexions via notifications push, ce qui
renforce la sécurité d’accès aux ressources de l’entreprise.

![](/img/tel.png)

Une fois l’enrôlement de l’appareil terminé par l’utilisateur via le portail d’entreprise, nous pouvons constater que celui-ci remonte
correctement dans l’interface Microsoft Intune. L’appareil apparaît dans la section “Appareils” du profil utilisateur
avec ses informations techniques, son état de conformité, ainsi que la date et l’heure du dernier enregistrement. Cela
confirme que la gestion MDM est bien active et fonctionnelle.

![](/img/tenant.png)

Une fois l’utilisateur créé dans Entra ID (Azure AD), nous l’avons ajouté à un groupe de sécurité précédemment configuré dans Intune. Cela permet d’automatiser l’attribution des stratégies, des configurations et des applications liées à ce groupe. Dans notre cas, nous avons choisi le groupe “MDM”, ce qui déclenche automatiquement l’enrôlement de l’appareil mobile, ainsi que l’installation d’Outlook, Microsoft Authenticator, et des autres applications professionnelles nécessaires.

![](/img/app.png)

Nous pouvons désormais constater que le téléphone de l’utilisateur affiche une section “Work” (Espace professionnel).
Cette séparation entre les données personnelles et professionnelles est automatiquement créée par Intune lors de l’enrôlement de l’appareil Android en mode “profil professionnel”. 
Toutes les applications professionnelles assignées — telles que Outlook, Microsoft Authenticator, Company Portal, ou Skype — sont installées dans cet espace sécurisé, identifiable par l’icône de valise de travail bleu. 
Cela permet de garantir une isolation complète des données d’entreprise tout en respectant la vie privée de l’utilisateur.

![](/img/captel.png)

Une fois l'appareil inscrit et remonté dans Intune, nous
avons accès à une vue détaillée de ses caractéristiques
techniques dans la section "Matériel". Cette interface
permet de consulter plusieurs informations essentielles
telles que :

- Le modèle et le système d’exploitation de l’appareil, ici un terminal Android de type sdk_gphone64_x86_64.
- L’état de conformité, qui est marqué comme “Conforme”, indiquant que toutes les stratégies de sécurité et de configuration sont bien appliquées.
- L’opérateur mobile, la connectivité (Wi-Fi / GSM), et les adresses MAC, permettant de tracer ou d’analyser l’usage réseau.
- Les informations liées à l’activation EAS (Exchange ActiveSync) pour le lien avec les services de messagerie.
- Le statut de sécurité, avec la confirmation que l’appareil n’est pas rooté, n’est pas jailbreaké, et n’est pas supervisé.

Cette visibilité complète sur le matériel permet à l’administrateur de suivre précisément chaque appareil géré, de
vérifier sa conformité, et d’intervenir rapidement en cas de problème ou de perte.

![](/img/conftel.png)
