# Personnal Weather Station

## Présentation

Ce plugin permet d'utiliser des stations météos avec Jeedom en mode local. Les stations météo utilisant l'application WS View ou WS Tools sont compatibles.

On trouve plusieurs modèles sur Amazon à partir de 100€.

### Exemple de stations fonctionnelles

Les stations météo qui utilisent WS View se trouvent sous plusieurs noms de marques différentes, plusieurs variantes mais restent le même modèle. Voici une liste qui devrait fonctionner.

[Waldbeck Halley Station météo Multifonction](https://amzn.to/3924BKr)

[Waldbeck Halley Station météo Multifonction avec écran](https://amzn.to/392592X)

[Ventus W830](https://amzn.to/2wacIWU)

[Froggit](https://www.amazon.fr/Froggit-DP1500-Station-syst%C3%A8me-Centre/dp/B07YDG97XF/ref=sr_1_35?)

## Configuration

### Configuration générale

Le plugin ne comporte pas de configuration générale.

### Configuration d'un équipement

Il faut utiliser WS View pour configurer votre station météo via le type "Customized"

Les paramètres à saisir :

* Protocole : Wunderground

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

## Station Froggit

Il existe plusieurs déclinaisons de la station Froggit dont un modèle avec une tablette

[Froggit avec tablette](https://www.amazon.fr/Froggit-HP1000SE-Internet-Station-Serveur/dp/B07ZJK8644/ref=sr_1_2?)

La station Froggit permet de rajouter des capteurs supplémentaires, dont :

### Capteur intérieur de température et d'humidité 

[Un capteur de température et d'humidité](https://www.amazon.fr/Froggit-DP50-Thermo-hygrom%C3%A8tre-Plusieurs-canaux/dp/B0844K28MJ/ref=sr_1_7?)

Les informations fournies sont : 

* Humidité Intérieure

* Température Intérieure

* Pile Faible : binaire à 0 quand il n'y a pas d'alerte

La configuration consiste à indiquer, via des micro-switchs, un numéro de capteur et l'unité de température choisie (°C ou °F)

### Capteur d'humidité de sol

[Un capteur d'humidité de sol](https://www.amazon.fr/Froggit-DP100-Capteur-Radio-multicanal/dp/B0844KS4B2/ref=sr_1_14?)

Les informations fournies sont : 

* Humidité du sol 

* Voltage de la pile 

Le capteur peut être installé soit en intérieur (bac à fleurs) ou soit en extérieur (jardin, pelouse, massif de fleurs, haie, ...)

Un capteur d'humidité de sol permet de gérer un arrosage automatique de façon plus optimum car celui-ci ne se déclenchera que lorsque le sol en a réellement besoin.

### Configuration d'une station dans le cas d'utilisation de capteurs additionnels

![Illustration](images/Config_Ecowitt.png?raw=true "Illustration")

Il faut utiliser WS View pour configurer votre station météo via le menu "Weather Services" / "Customized"

Les paramètres à saisir :

* Protocole : Ecowitt

* Server IP : IP de Jeedom

* Path : le path de l'API pws du plugin, /{jeedom}/plugins/pws/core/api/ecowitt.php

* Port : le port de Jeedom (80 pour du http standard)

* Période de rafraichissement : 16 secondes (minimum)
