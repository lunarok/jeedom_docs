# Gestion de Stock

## Présentation

Ce plugin permet de s'interfacer avec un gestionnaire de stock Grocy et ainsi pouvoir ineragir avec vos différents stocks depuis Jeedom.

Grocy est un logiciel complet de gestion de vos stocks frigo, placards etc. Il peut être utilisé également pour vos cuves de fioul, stock de bois, citerne d'eau ...

## Installation de Grocy

Pour installer Grocy, plusieurs méthodes sont disponibles :

https://github.com/grocy/grocy#how-to-install

## Configuration

Il faut remplir les éléments de configuration pour accéder à Grocy :

- Adresse IP

- Port d'écoute

- Token API

## Equipements

Les équipements sont automatiquement créés lors du scan de Grocy par Jeedom. Chaque produit est créé comme un équipement Jeedom avec les commandes ci-dessous disponible :

- Etat du stock

- Prochaine date d'expiration

- Ajout unitaire

- Ajout par quantité libre

- Réduction unitaire

- Réduction par quantité libre

- Définir la quantité en stock

Il y a 2 paramètres accessible sur chaque équipement, avec une valeur par défaut si non remplie (ils servent en cas d'ajout de stock) :

- Prix (par défaut 0)

- Date d'expiration (par défaut 2199-12-31)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de Grocy. Sur réseau local si votre instance est locale.

## Changelog

[Voir la page dédiée](changelog.md).
