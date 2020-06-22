# Personnal Weather Station

## Présentation

Ce plugin permet d'utiliser des stations météos avec Jeedom en mode local. Les stations météo utilisant l'application WS View ou WS Tools sont compatibles.

On trouve plusieurs modèles sur Amazon à partir de 100€.

### Exemple de stations fonctionnelles

Les stations météo qui utilisent WS View se trouvent sous plusieurs noms de marques différentes, plusieurs variantes mais restent le même modèle. Voici une liste qui devrait fonctionner.

[Waldbeck Halley Station météo Multifonction](https://amzn.to/3924BKr)

[Waldbeck Halley Station météo Multifonction avec écran](https://amzn.to/392592X)

[Ventus W830](https://amzn.to/2wacIWU)

Les Froggit semblent aussi être une variante.

## Configuration

### Configuration générale

Le plugin ne comporte pas de configuration générale.

### Configuration d'un équipement

Il faut utiliser WS View pour configurer votre station météo via le type "Customized"

Les paramètres à saisir :

* Server IP : IP de Jeedom

* Path : le path de l'API pws du plugin, /{jeedom}/plugins/pws/core/api/pws.php?

* Station ID : ce que vous voulez, si vous voulez utilisez plusieurs stations, il faut bien que cet ID soit unique

* Station Key : la clef API du plugin pour Jeedom

* Port : le port de Jeedom (80 pour du http standard)

Un paramètre supplémentaire permet d'intégrer une station météo en protocole Ecowitt (toujours en customized). Celui-ci peut être utilisé pour une seule station, il permet de récupérer des valeurs de capteurs supplémentaires à la station (que l'on ne peut pas avoir avec le protocole Wunderground)

Dans le cas d'Ecowitt, un paramètre change :

* Path : le path de l'API pws du plugin, /{jeedom}/plugins/pws/core/api/ecowitt.php

## Informations fournies

Voici les informations disponibles :

* Humidité Extérieure

* Température Extérieure

* Confort Humidité Extérieure (par calcul)

* Humidex (par calcul, indice de confort chaleur)

* Point de Rosée

* Point de Givrage (par calcul)

* Température Ressentie

* Provenance du Vent

* Direction du Vent (par calcul)

* Vitesse du Vent

* Vitesse de Rafale

* Pluie

* Pluie 24h

* Radiation Solaire

* Eclairement (par calcul)

* UV Index

* UV Statut Alerte (par calcul)

* Température Intérieure

* Humidité Intérieure

* Confort Humidité Intérieure (par calcul)

* Pression Relative

* Pression Absolue (quand disponible)

* Tendance (par calcul basé sur la pression actuelle)

* Projection (par calcul basé sur les 4 dernières heures de pression)

* Pile Faible : binaire à 0 quand il n'y a pas d'alerte
