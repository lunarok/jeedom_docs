# Gestion de Stock

## Présentation

Ce plugin permet de s'interfacer avec un gestionnaire de stock Grocy et ainsi pouvoir ineragir avec vos différents stocks depuis Jeedom.

Grocy est un logiciel complet de gestion de vos stocks frigo, placards etc. Il peut être utilisé également pour vos cuves de fioul, stock de bois, citerne d'eau ...

Pour votre stock de pellets, il pourra gérer vos différente localisations, les évolutions de tarifs. Et avec Jeedom vous pourrez le mettre à jour en automatique en monitorant le niveau du stock, permettant de vous alertez sur seuil. Vous pouvez utiliser les interactions Telegram pour saisir les informations de vos commandes.

Et pour vos placards, bonus Jeedom saura vous alertez de données périssables. Pour la saisie des consommations/ajouts, vous avez la possibilité d'utiliser Barcode Buddy qui est très complet.

## Installation de Grocy

Pour installer Grocy, plusieurs méthodes sont disponibles (sur un serveur web, en docker ou application windows) :

https://github.com/grocy/grocy#how-to-install

Pour saisir vos denrées en scannant les codes barres, deux possibilités :

L'application mobile Grocy : https://play.google.com/store/apps/details?id=xyz.zedler.patrick.grocy

Elle permet de retrouver toutes vos infos et faire vos ajouts/retraits par code barre

La bascule entre les modes consommation/ajout de produit se fait alors directement à l'écran de capture, d'un simple clic

En cas de nouveau code barre, il vous demandera de l'associer à un produit existant

Il existe aussi une application compagnion de Grocy qui en cas de code barre inconnu ira chercher une référence dans OpenFoodFacts :

https://barcodebuddy-documentation.readthedocs.io/en/latest/

Barcode Buddy dispose d'une application mobile permettant le scan de vos produits en direct

En cas de nouveau code barre, il permet de faire une recherche dans OpenFactFoods et trouver le produit. L'association étant faite plus tard.

Pour passer d'un mode à l'autre, il nécessite d'imprimer des codes barres spécifiques.

Les deux applications permettent d'utiliser la caméra du téléphone ou un lecteur séparé (Grocy en direct permet aussi d'utiliser un lecteur physique attaché au serveur exécutant Grocy)

* Avis Personnel * L'application mobile Grocy est mieux faite, contient plus d'informations sur Grocy (en gros, pour suivre votre Grocy sur téléphone, de toute facon vous en aurez besoin). Et après essais, le mode de saisie est plus "naturel" avec ce changement de consommation/ajout directement visible sur l'écran. L'association code barre et produit est plus simple aussi. Il faut juste penser à avoir saisi ses produits à l'avance, mais la recherche dans OpenFoodFacts n'apporte pas grand chose.

## Configuration

Il faut remplir les éléments de configuration pour accéder à Grocy :

- Adresse IP

- Port d'écoute

- Token API

Vous pouve également sélectionner un objet de Jeedom pour y ajouter les nouveaux équipements par défaut.

Il n'y a pas de scan à lancer, le plugin utilise le cron 1mn de Jeedom pour récupérer toutes les infos de Grocy. Les produits trouvés dans Grocy sont automatiquement créés, les infos sont automatiquement mises à jour. Lors de l'utilisation de commandes action dans Jeedom pour enlever ou ajouter du stock, c'est mis à jour immédiatement dans Grocy.

## Equipements

Les équipements sont automatiquement créés lors du scan de Grocy par Jeedom. Chaque produit est créé comme un équipement Jeedom avec les commandes ci-dessous disponible :

- Quantité en stock

- Quantité ouverte

- Stock minimum défini dans Grocy

- Statut binaire si le stock est inférieur au seuil minimum

- Prochaine date d'expiration

- Statut binaire si des produits périmés sont présents

- Statut binaire d'alerte si des produits seront périmés dans moins de X jours (par défaut 3 jours, paramètre de configuration sur l'équipement)

- Ajout unitaire

- Ajout par quantité libre

- Réduction unitaire

- Réduction par quantité libre

- Définir la quantité en stock

- Prix à utiliser pour les ajouts (commande action pour le définir, comme info pour le récupérer) : va modifier le paramètre de configuration de l'équipement sur utilisation

- Date d'expiration à utiliser pour les ajouts (commande action pour le définir, comme info pour le récupérer) : va modifier le paramètre de configuration de l'équipement sur utilisation

Il y a 2 paramètres accessible sur chaque équipement, avec une valeur par défaut si non remplie (ils servent en cas d'ajout de stock) :

- Prix (par défaut 0)

- Date d'expiration (par défaut 2199-12-31)

- Nombre de jours pour l'alerte de date d'expiration (par défaut 3)

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de Grocy. Sur réseau local si votre instance est locale.

## Changelog

[Voir la page dédiée](changelog.md).