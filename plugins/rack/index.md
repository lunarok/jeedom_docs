# Rack Informatique

## Présentation

La plugin permet de faciliter la gestion de certains équipements présents dans un rack informatique. Le but est de centraliser sur un seul plugin différents matériels pour ne pas démultiplier les plugins gérant un seul équipement.

Les équipements pris en charge :

- Smart PDU Intellinet

- Onduleurs (via NUT)

- Switch Netgear JGS524PE

Pour les onduleurs, le plugin n'utilise pas de dépendances python mais directement la commande NUT qui doit être présente.

## Configuration

Il n'y a pas de configuration générale.

Pour chaque équipement, il faut préciser :

- le type (Onduleur NUT, Smart PDU Intellinet, Switch Netgear JGS524PE)

- l'adresse IP

- si c'est un onduleur, le nom de l'onduleur tel que déclaré dans NUT

- si c'est un switch Netgear, le mot de passe de l'interface

- si c'est un Smart PDU Intellinet en version 1.0.4 il faut remplir user et password (en dessous il faut laisser les champs vides)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, celles des équipements. C'est une connexion sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
