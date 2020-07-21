# DarkSky, météo complète

## Présentation

Ce plugin permet d'obtenir la météo depuis le site DarkSKy.net qui dispose de données "temps réel"

Une présentation est disponible sur cet article : [Article de présentation](https://lunarok-domotique.com/plugins-jeedom/dark-sky-meteo-panel/)

Le plugin dispose de différentes fréquences de rafraichissement :

  - toutes les 5 mns : les informations temps réel

  - toutes les heures : les prévisions à l'heure

  - journalier : les prévisions au jour (météo mais aussi lever et coucher du soleil)

Si un redémarrage de Jeedom se produit, toutes les infos sont récupérées.


## Configuration

Le plugin ne comporte pas de configuration générale.

Il faut ajouter un équipement et configurer les 2 paramètres :

  - quel équipement de localisation (configuration de Jeedom ou geotrav) servira pour les coordonnées de la météo à récupérer

  - la clef API de Dark Sky (https://darksky.net/dev/)


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le plugin récupère les valeurs de Dark Sky

>Est-ce que le plugin s'appuie sur des plugins tiers ?

Oui, il utilise un équipement du plugin geotrav (Localisation et Trajet).

>Comment utiliser les informations de lever/coucher du soleil ?

Il faut utiliser un scénario avec pour déclencheur le lever ou coucher du soleil. Puis utiliser des blocs à condition 'A'

## Troubleshooting

> Je n'ai pas d'informations qui remontent

Il faut bien créer un équipement et remplir les informations du lieu pour lequel on souhaite avoir la météo.

## Changelog

[Voir la page dédiée](changelog.md).
