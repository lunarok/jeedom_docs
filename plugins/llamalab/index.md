# Automate de Llamalab

## Présentation

Le plugin permet de faciliter le lien entre Automate pour Android et Jeedom.

## Configuration

On créé un équipement par Android, une URL de connexion est alors affichée et on peut télécharger le flow Automate.
Ce flow une fois importé nécessite d'y ajouter l'URL envoyée, et c'est tout.

Le flux proposé permet d'envoyer toutes les données que vous trouvez en commandes infos depuis le téléphone.
Il vous faudra le scheduler par vos moyens (par exemple en utilisant un flow permettant de le jouer toutes les minutes)

Il est possile d'ajouter d'autres commandes sur demande.
De même il est prévu de pouvoir envoyer des infos de Jeedom vers Automate.

[Télécharger le flux ici](Informations.flo)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, il s'appuie sur Automate sur vos Android qui appelle Jeedom uniquement.

## Changelog

[Voir la page dédiée](changelog.md).
