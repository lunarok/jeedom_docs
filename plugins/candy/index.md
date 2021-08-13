# Candy

## Présentation

Le plugin permet pour les appareils électroménagers Candy avec le Simply-Fi de récupérer les informations qu'il fournit sur son état.
L'ajout des actions est planifier dans une prochaine version.

## Configuration

Pour chaque appareil Candy Simply-Fi, vous devez ajouter un équipement et saisir son adresse IP (penser à la mettre en réservation sur votre boxe Internet pour pas qu'elle change)
Une fois cela fait, vous pouvez utiliser le bouton de récupération de la clef. Une fois récupérée, elle apparait sur la page de configuration.

### Commandes

Chaque appareil dispose d'une commande "online" indique si il est bien présent sur le réseau (sinon c'est qu'il est en veille et donc non interrogeable)
En plus, une commande est créée pour chaque information fournie. Attention ses informations pour certaines ne sont pas "clairement identifiable" car elle porte un nom du type "r1" alors que d'autres comme "MissSalt" parlent d'elles-même.
Au fur et à mesure qu'elles seront référencées et confirmées, un tableau de correspondance sera mis en place.
De même les commandes sont créées par défaut en sous-type "texte", mais elles peuvent être basculées en numérique ou binaire.

Ce fonctionnement permet de rendre le plugin compatible théoriquement avec tous les appareils Candy.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il récupère les infos de vos appareils en local.

> Quand je lance la recherche de clef, je n'ai pas résultat ?

Par précaution, allumer votre appareil. Suivant le type, ils sont en veille et non interrogeable, le plus simple est alors de les réveiller.

## Changelog

[Voir la page dédiée](changelog.md).
