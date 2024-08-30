# AFlux RSS, créer vos flux avec Jeedom

## Présentation

Flux RSS est un plugin permettant de générer des flux RSS. Vous pourrez alors les ajouter dans votre lecteur RSS préféré.


## Configuration

Il n'y a pas de configuration du plugin

### Configuration de l'équipement

Chaque équipement à 4 paramètres à remplir :

  * Titre du Flux

  * Lien du Flux

  * Description du Flux

  * Nombre d'items du Flux (1,10,15,20,25,30,50)


Après sauvegarde, on aura accès à l'URL du flux RSS

Chaque équipement contient une seule commande message :

  * Titre : deviendra le titre de l'item du flux

  * Message : le contenu de l'item


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non le plugin génère le RSS en local et vous donne l'adresse à laquelle il est dispo (sur Jeedom)

## Changelog

[Voir la page dédiée](changelog.md).
