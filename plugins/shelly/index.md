# Shelly

## Présentation

Ce plugin permet d'interconnecter Jeedom avec des modules Shelly.

Il permet de commander les relais ou fonctions des différents modules Shelly. Ainsi que récupérer les informations (statut, consommation, couleur ...)

Shelly sont une série de produits fonctionnant en Wifi, ils proposent une application mobile pour leur configuration ainsi qu'un Cloud pour leur utilisation à distance.

Le plugin Jeedom utilise une API locale au module directement, pas besoin du cloud.

https://shelly.cloud/

## Configuration

Le plugin ne comporte pas de configuration générale.

Sur chaque équipement, il faut configurer :

  - l'adresse IP

  - le type
  
Si un user et password sont existants, il est possible de les saisir.

En plus de la configuration locale, il est possible d'utiliser les API du Cloud Shelly. Cela permettra par exemple d'accéder à des Shelly qui ne sont pas sur le réseau de Jeedom (résidence secondaire, etc)

Dans le cas du Shelly Cloud, pour l'adresse il faut mettre celle du Shelly Cloud. Il faut saisir en plus l'auth_key et l'ID du module Shelly. Attention, le fonctionnement en cloud n'est pas fonctionnel pour tous les modules.

Les commandes sont créées automatiquement à la sauvegarde. Pour chaque type, les commandes infos et actions disponibles seront disponibles.

Pour les relais, sur sauvegarde de l'équipement, Jeedom va aller configurer chaque "push url" du Shelly pour recevoir en temps réel les changements d'état.

Dans le cas du Shelly 1, si le bouton est configuré en "Detached type", alors Jeedom en plus pendant la sauvegarde équipement va créer une commande représentant le bouton et qui sera liée au "push url" du bouton. Permettant ainsi son utilisation en plus du relais comme bouton poussoir dans Jeedom.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le plugin utilise l'API locale des modules Shelly, pas besoin du Cloud ou autre.


## Changelog

[Voir la page dédiée](changelog.md).
