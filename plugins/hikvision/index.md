# Hikvision

## Présentation

Ce plugin permet de lire les trames émises par les caméras Hikvision en cas d'évènement. Mais aussi de visualiser les caméras depuis Jeedom et envoyer les snapshot en notifications.

Il permet de récupérer :

- la détection de mouvement

- la détection de ligne

- la perte de vidéo

- la vidéo aveugle

- l'alarme locale

- la détection de mouvement PIR

- la détection de zone

Attention, toutes les commandes ne sont pas disponibles sur toutes les caméras, cela dépend des caractéristiques de votre caméra/NVR.

Le protocole existe dans certaines caméras "clone" Hikvision sans garantie.

Pour être sûr de bien recevoir les notifications, pensez à vérifier vos configurations Hikvision et que les différentes détections sont bien actives pour votre modèle.

Deux commandes permettent de connaitre l'URL Snapshot et RTSP utilisées.

Une dernière commande sert à envoyer un snapshot pour les scénarios.

## Configuration

#### Configuration général du plugin

Le plugin propose plusieurs paramètres sur la page de configuration générale :

- rafraichissement d'affichage (qui servent à modifier la valeur par défaut de 2s pour toutes les caméras, sauf si le paramètre est défini sur l'équipement de facon spécifique)

- nombre de jours de rétention (par défaut 2)

- l'expression qui servira à répondre aux interactions

#### Configuration des équipements

Il faut configurer l'adresse, l'utilisateur et le mot de passe de la caméra Hikvision dans l'équipement.Il faut aussi indiquer si c'est une caméra ou un NVR (et dans ce cas cas, indiqué le channel)

Des paramètres sont disponibles pour chaque caméra (les mêmes que sur la configuration générale, ils prévalent) :

- rafraichissement d'affichage (2 secondes par défaut)

- nombre de jours de rétention (par défaut 2)

#### Configuration des caméras

Suivant les modèles, il faut bien activer les notifications vers "Centre de surveillance" sur 3 zones :

- Système : Sécurité doit être sur digest/basic et vous devez créer un utilisateur avec au moins les droits Centre de Surveillance

- Réseau, Avancé : l'onglet Protocole d'intégration doit être en digest/basic aussi avec l'utilisateur présent

- Evènement : chaque type d'évènement de la caméra, il faut bien configurer qu'il est actif et notifier vers le Centre de Surveillance

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin écoute les trames émises par les caméras sur le réseau local (celles qui servent au Centre de Surveillance Hikvision)

> Est-ce que le plugin permet d'enregistrer les vidéos ?

Non, le plugin ne remplace pas un NVR que ce soit via une appliance physique ou un logiciel tiers de gestion de CCTV (Zoneminder, Shinobi, Moonfire ...)

> Quelles caméras sont compatibles ?

Les caméras Hikvision qui peuvent émettre des détections vers le centre de surveillance, c'est à peu près la seule définition sans liste exacte.

Toutes les caméras Hikvision ne proposent pas tous les types de détection (comme le franchissement de ligne)

Des clones Hikvision implémentent aussi ce protocole (ceux qui ont pour but de s'intégrer complètement dans une solution de surveillance full Hikvision)

## Changelog

[Voir la page dédiée](changelog.md).
