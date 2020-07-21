# Weatherbit, météo complète

## Présentation

Ce plugin permet d'obtenir la météo depuis le site Weatherbit.io qui dispose de données "temps réel", projections futures mais aussi de données météos spécialisées pour l'agriculture ou l'énergie thermique. Il y a également des données de qualité d'air et de pollens.

Le plugin se rafraichit à l'heure

Si un redémarrage de Jeedom se produit, toutes les infos sont récupérées.


## Configuration

Le plugin ne comporte pas de configuration générale.

Il faut ajouter un équipement et configurer les 3 paramètres :

  - quel équipement de localisation (configuration de Jeedom ou geotrav) servira pour les coordonnées de la météo à récupérer

  - la clef API de Weatherbit (https://weatherbit.io/)
  
  - la température de référence utilisée pour le calcul des degrés de chauffe/refroidissement
  
## Commandes créées

Le plugin créé un grand nombre de commandes. Celles ci sont réparties par catégories : en cours, du jour, +1, +2j, +3j, +1h, +2h, ... jusqu'à +6h

Les commandes sont de nature :

  - conditions météo générales (nuages, description, humidité, température ...)
  
  - soleil et lune (lever, coucher, phase, élévation ...)
  
  - énergie (degrés de chauffe/refroidissement, heures d'ensoleillement)
  
  - air (qualité d'air, polluants, pollens)
  
  - agriculture (température et humidité au sol)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le plugin récupère les valeurs de Weatherbit

>Est-ce que le plugin s'appuie sur des plugins tiers ?

Oui, il peut utiliser un équipement du plugin geotrav (Localisation et Trajet).

>Comment utiliser les informations de lever/coucher du soleil ?

Il faut utiliser un scénario avec pour déclencheur le lever ou coucher du soleil. Puis utiliser des blocs à condition 'A'

## Troubleshooting

> Je n'ai pas d'informations qui remontent

Il faut bien créer un équipement et remplir les informations du lieu pour lequel on souhaite avoir la météo.

## Changelog

[Voir la page dédiée](changelog.md).
