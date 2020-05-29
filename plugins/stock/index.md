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

Les équipements sont automatiquement créés lors du scan de Grocy par Jeedom. Chaque produit et liste de courses est créé automatique dans Jeedom. Les informations de chaque équipement sont listées ci-dessous.

### Equipement pour un produit

Informations sur le stock :

- Quantité en stock

- Quantité ouverte

- Stock minimum défini dans Grocy

- Statut binaire si le stock est inférieur au seuil minimum

Informations relatives à la date d'expiration :

- Prochaine date d'expiration

- Statut binaire si des produits périmés sont présents

- Statut binaire d'alerte si des produits seront périmés dans moins de X jours (par défaut 3 jours, paramètre de configuration sur l'équipement)

Les commandes relatives à la manipulation du stock :

- Ajout unitaire

- Ajout par quantité libre

- Réduction unitaire

- Réduction par quantité libre

- Définir la quantité en stock

- Prix à utiliser pour les ajouts (commande action pour le définir, comme info pour le récupérer) : va modifier le paramètre de configuration de l'équipement sur utilisation

- Date d'expiration à utiliser pour les ajouts (commande action pour le définir, comme info pour le récupérer) : va modifier le paramètre de configuration de l'équipement sur utilisation

Des informations relatives aux listes de courses :

- si le produit est dans une/des liste(s) (contient le nom des listes séparées par ;)

- la quantité saisie dans cette liste (contient le nom des listes avec : et la quantité séparées par ; - liste : 1 -)

- une action select pour ajouter le produit à une liste

Des informations générales :

- membre d'un groupe de produits (retourne le nom du groupe si oui)

- le nom du produit (pour faciliter l'utilisation en scénario)

Il y a 3 paramètres accessible sur chaque équipement, avec une valeur par défaut si non remplie (ils servent en cas d'ajout de stock) :

- Prix (par défaut 0)

- Date d'expiration (par défaut 2199-12-31)

- Nombre de jours pour l'alerte de date d'expiration (par défaut 3)

### Equipement pour une liste de courses

- Liste des produits avec leur quantité de la liste

- Nom de la liste dans Grocy

- Ajout de tous les produits sous leur seuil

- Enlever tous les produits de la liste

### Equipement général Grocy

- Liste des produits en alerte de stock (à 0)

- Liste des produits en dessous de leur seuil

- Liste des produits ayant du stock périmé

- Liste des produits ayant du stock arrivant à date

- Rafraichir : lance la synchronisation avec Grocy

- Synchronisation des batteries : va créer dans Grocy les batteries présentes dans Jeedom, en indiquant en description le type de batteries et leur charge en %. Mais aussi pour les batteries existantes, il va enregistrer dans Jeedom si une recharge/changement a été indiqué dans Grocy.

- Supprimer les équipements absents de Grocy : permet de supprimer dans Jeedom les équipements pour des produits qui n'existeraient plus dans Grocy

- Remplir les informations complémentaire depuis OpenFoodFacts : pour chaque produit avec un code-barre valide, cela va renseigné des userfields dans Grocy et les commandes locales (récupère les labels, les ingrédients, les allergènes et l'indice de qualité nutritionnelle)


## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de Grocy. Sur réseau local si votre instance est locale.

Une commande unique utilise également l'API de OpenFoodFacts.org

## Changelog

[Voir la page dédiée](changelog.md).
