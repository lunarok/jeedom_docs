# Hikvision

## Présentation

Le plugin a pour but de gérer vos caméras Hikvision dans Jeedom en autonomie (sans besoin d'autres plugins)

On peut donc :

- obtenir un widget pour les dashboards avec un apercu de la caméra

- avoir un panel Jeedom avec toutes vos caméras

- recevoir les notifications de vos caméras (suivant les modèles : détection de mouvement, franchissement de ligne ...)

- récupérer les url de snapshots, videos ... (pour les utiliser avec d'autres commanndes, par exemple pour envoyer la vidéo vers un Google Home)

- gérer les commandes infrarouge, PTZ

- envoyer des notifications avec screenshot (via Telegram, Mail ...)

- ajouter les cameras Hikvision dans les interactions Jeedom


Attention, toutes les commandes ne sont pas disponibles sur toutes les caméras, cela dépend des caractéristiques de votre caméra/NVR.

Le protocole existe dans certaines caméras "clone" Hikvision sans garantie.

Pour être sûr de bien recevoir les notifications, pensez à vérifier vos configurations Hikvision et que les différentes détections sont bien actives pour votre modèle.

Deux commandes permettent de connaitre l'URL Snapshot et RTSP utilisées.

Une dernière commande sert à envoyer un snapshot pour les scénarios.

Le plugin est également compatible avec certains portiers comme le DS-KD8003 (réception alors des codes clavier, sonnerie, possibilité d'ouvrir la porte ...)

## Configuration

#### Configuration général du plugin

Le plugin propose plusieurs paramètres sur la page de configuration générale :

- rafraichissement d'affichage (qui servent à modifier la valeur par défaut de 2s pour toutes les caméras, sauf si le paramètre est défini sur l'équipement de facon spécifique)

- une taille générique pour les widgets qui s'appliquera alors à toutes les caméras

- l'expression qui servira à répondre aux interactions

#### Configuration des équipements

Il faut configurer l'adresse, l'utilisateur et le mot de passe de la caméra Hikvision dans l'équipement.Il faut aussi indiquer si c'est une caméra, un portier ou un NVR (et dans ce cas cas, indiqué le channel)

Note importante : les portiers ne sont supportés pour les alarmes que sur une plateforme Intel/AMD

Des paramètres sont disponibles pour chaque caméra (les mêmes que sur la configuration générale, ils prévalent) :

- rafraichissement d'affichage (2 secondes par défaut)

- widget standard (n'affichera alors pas la vue mais les informations de mouvement ...)

- activer le PTZ (qui ajoutera les commandes PTZ)

- activer l'infrarouge (qui activera les commandes du mode infrarouge)

- désactiver l'écoute des évnènements pour cette caméra (dans ce cas Jeedom ne recevra pas les notifications)


#### Configuration des caméras/NVR

Suivant les modèles, il faut bien activer les notifications vers "Centre de surveillance" sur 3 zones :

- Système : Sécurité doit être sur digest/basic et vous devez créer un utilisateur avec au moins les droits Centre de Surveillance

- Réseau, Avancé : l'onglet Protocole d'intégration doit être en digest/basic aussi avec l'utilisateur présent

- Evènement : chaque type d'évènement de la caméra, il faut bien configurer qu'il est actif et notifier vers le Centre de Surveillance

## Commandes

Pour les caméras, on aura dans Jeedom ces commandes :

- URL Snapshot, RTSP, MPEG

- Message avec snapshot (à utiliser conjointement avec un plugin de messagerie)

- Enregistrement (démarrage et arrêt) à utiliser avec précaution, Jeedom ne remplace pas un NVR hardware ou software

- Infrarouge (arrêt et démarrage) si la configuration est cochée

- Commandes PTZ, si la configuration est cochée


### Commandes de notification Caméra

Les commandes de notification sont créées à la sauvegarde de l'équipement. Elles vont dépendre de ce que la caméra est en capacité de faire ET qui a été configuré pour remonter au centre de notification. Ainsi, une caméra capable de détection de franchissement de ligne, pour que ca remonte, il faut bien activer cette détection sur la caméra avec commme notification le centre de notification.

On trouve par exemple LineCrossing, Motion, TamperDetection, FieldDetection, IllegalAccess ...

Toutes ces commandes sont de type binaire

### Commandes de notification Portier

Pour un portier on retrouvera les commandes suivantes :

- unlocked, dismiss, dooropen, motion, ring, tamper

Motion est un capteur de mouvement, Ring permet de récupérer quand on sonne. Unlocked remonte les codes d'ouverture. Vous pourrez identifier celui envoyer par l'ouverture depuis un visiophone/application mais aussi les cartes RFID, code de clavier

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin écoute les trames émises par les caméras sur le réseau local (celles qui servent au Centre de Surveillance Hikvision)

> Est-ce que le plugin permet d'enregistrer les vidéos ?

Non, le plugin ne remplace pas un NVR que ce soit via une appliance physique ou un logiciel tiers de gestion de CCTV (Zoneminder, Shinobi, Moonfire ...)

> Quelles caméras sont compatibles ?

Les caméras Hikvision qui peuvent émettre des détections vers le centre de surveillance, c'est à peu près la seule définition sans liste exacte.

Toutes les caméras Hikvision ne proposent pas tous les types de détection (comme le franchissement de ligne)

Des clones Hikvision implémentent aussi ce protocole (ceux qui ont pour but de s'intégrer complètement dans une solution de surveillance full Hikvision)

> Quelles portiers sont compatibles ?

La liste exacte n'est pas connue. Le plugin utilise le SDK officiel d'Hikvision, donc ca devrait en couvrir une majorité.

En revanche, ce même SDK pose une contrainte majeure : il ne fonctionne que sur plateforme Intel/AMD et donc pas sur les plateformes ARM. Rendant la détection des alarmes de portier indisponible sur ARM.

## Changelog

[Voir la page dédiée](changelog.md).
