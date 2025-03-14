---
sidebar_position: 4
---

Pour commencer ce projet, nous avons décide chaqu'un de configurer une partie que l'on rassemblerait par la suite qui est :

la documentation avec les schéma de la structure.
la mise en place du serveur Samba adds/nfs avec authentification.
la mise en pratique de aws afin d'importer le serveur Samba par la suite.

Nous avons donc chaqu'un commencer avec un sujet en tête.

- AWS étant nouveau, une personne s'est chargé d'en apprendre un peu plus afin de se familiarisé avec l'environnement.

- la création du serveur SAMBA ADDS + nfs, la mise en place de la demande du client afin de parfaire les attentes du clients.

- la création du schéma de l'infrastructure ainsi que la documentation a fournir afin de guidé l'utilisateur sur notre avancer et des commandes.

Avant d'importer ensuite les machines sur AWS, nous avons fait les tests en interne afin de s'assurer de la fonctionnalité de celle-ci.

Notre premier panneau STOP a été lors de la création du vpn, nous avions tout d'abord tenter de relié un wireguard entre le routeur de test que nous avions (qui simulerais l'entreprise) avec le serveur SAMBA se trouvant sur AWS.

Après concertation, nous avons déduis que le vpn doit être créer dans les configurations disponibles de AWS notamment le VPC, mais par faute de temps et de connaissance, la solution n'aura pas pu être aboutit.

Nous avons fini par la mise en place d'une solution de supervision avec Grafana et Prometheus afin de pouvoir monitorer les services Samba et recevoir des retours lorsque celui-ci ne répond plus.