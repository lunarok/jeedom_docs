# Shinobi CCTV

## Présentation

Ce plugin permet de récupérer les informations des caméras existantes dans Shinobi et leurs évènements.

## Configuration

### Configuration générale

Le plugin nécessite de saisir la configuration pour se connecter à Shinobi.

- Adresse : sous la forme http://shinobi:8080

- API Key : que vous retrouvez dans le menu "API" dans Shinobi

- Group Key : que vous retrouvez dans le menu Settings

Et également deux configurations générale : pour les interactions avec le plugin et le temps de rafraichissement par défaut des widgets

### Configuration d'un équipement

Il n'y a pas d'ajout, les équipements sont créés sur synchronisation avec Shinobi

Elle se fait en sauvegardant la conf et toutes les 30mn

#### Paramètres

Les paramètres de la caméra dans Shinobi sont visible sur la page équipement (IP, path, port, résolution ...)

En plus il est possible de définir un temps de rafraichissement du widget ou bien de ne pas utiliser le widget de capture vidéo et afficher les informations

#### Configuration dans Shinobi

Vous devez ajouter un webhook sur votre caméra dans Shinobi. L'adresse à y mettre est fournit par la commande "URL Jeedom - EVent"

### Commandes disponibles

Pour chaque caméra, des commandes actions et informations sont créées.

En informations, on retrouve le statut et mode en cours. Mais aussi les différentes informations relatives à un Event se produisant sur la caméra et pour lequel Shinobi trigger le webhook.

En commande, on retrouve la gestion des modes de la caméra (off, active, enregistrement), les commandes PTZ et la possibilité d'envoyer un event à Shinobi

Pour la commande envoi d'un event, le message devra être constitué ainsi : plug=camera1=name=stairs,reason=motion,confidence=197.4755859375

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Le plugin utilise les API Shinobi pour récupérer ses informations et le piloter.


## Changelog

[Voir la page dédiée](changelog.md).
