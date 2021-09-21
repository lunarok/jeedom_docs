# Deepstack

## Présentation

Deepstack est un logiciel qui fournit en API de l'analyze d'image. L'avantage c'est que le produit est self-hosted et facile à installer en docker par exemple.

Le plugin Deepstack permet d'envoyer des images à une instance Deepstack pour la faire analyser.
Ce que permet comme analyse Deepstack :
- trouver des visages
- reconnaitre des visages
- trouver des objets
- reconnaitre une 'scène'

N'oubliez pas que pour activer un type de reconnaissance dans Deepstack, la bonne variable doit être renseignée dans la commande docker, exemple pour la détection de visage : VISION-FACE=True

Chacune des actions dispose d'une action de type message. Pour l'utiliser, soit vous fournissez dans le champ image le chemin d'une image à analyser, soit vous utilisez cette commande avec un envoi de snapshot par exemple (le champe image devant alors rester vide)

Chacune des actions dispose ensuite d'au moins 2 commandes infos, une pour indiquer si l'API a pu traité l'image (success), les autres donnant accès aux informations de l'API (taux de fiabilité, nom des objets ...)

## Configuration

On créer un équipement par Deepstack qu'on souhaite utiliser, vous pouvez ainsi avoir une seule instance avec tout activé ou plusieurs réparties (pour rappel, Deepstack comme toute reconnaissance d'objet est consommateur en ressource)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Deepstack. C'est donc sur le réseau local.

> Comment installer Deepstack ?

Le plus facile est en docker, vous trouverez tout sur leur site : https://docs.deepstack.cc/index.html

## Changelog

[Voir la page dédiée](changelog.md).
