# Time Manager

## Présentation

Time Manager permet 3 types de fonctions principales :

- Créer des actions retardées

- Créer des actions récurrentes

- Créer des planifications dépendantes d'une commande information donnant un horaire

Le point principal est que le plugin permet de gérer le séquencement à la seconde.

## Configuration

Il n'y a pas de configuration générale.

### Configuration de l'équipement

On créer un équipement et on choisit son type (actions retardées, actions récurrentes, actions planifiées)

#### Configuration d'un équipement "Actions Retardées"

Cet équipement à vocation à proposer X commandes séparées. Chaque commande quand elle est activée sera réellement déclenchée après le délai choisit.

Pour ce type d'équipement, il y a à définir :

* le mode de saisie du décalage : variable ou fixe

* si mode variable : on choisit dans la liste des variables Jeedom laquelle utilisée (elle devra être du format XX pour des secondes, par exemple 30 donnera 30s. Si vous désirez fournir en minutes, ca sera XX:XX. En heures, pareil XX:XX:XX)

* si mode fixe : un compteur permet de choisir la valeur du décalage.

#### Configuration d'un équipement "Actions Récurrentes"

Cet équipement à vocation à proposer un planification récurrente "à la seconde", mais qui peut prendre par exemple la forme de "toutes les 2h30mn40s". Quand la planification s'active, toutes les actions sont déroulées de la première à la dernière.

Pour ce type d'équipement, il y a à définir :

* la planification : via le compteur proposé.

#### Configuration d'un équipement "Actions Planifiées"

Cet équipement à vocation à proposer un planification journalière, via une commande info Jeedom ou saisie manuelle. Quand la planification s'active, toutes les actions sont déroulées de la première à la dernière. Dans ce mode, des conditions basiques sont disponibles en plus.

Pour ce type d'équipement, il y a à définir :

* le mode pour définir l'heure : par commande info ou manuelle

* si mode commande info : il faut choisir la commande et on peut en plus définir un décalage en plus/moins. Par exemple, l'heure du lever du soleil - 5mn. Le décalage se saisit avec le compteur affiché.

* si mode manuel : il faut définir l'heure via le compteur

* jours de la semaine : on peut choisir dans ce mode quels jours la planification sera valable

* semaine paire/impaire : on peut choisir dans ce mode quels jours la planification sera valable

#### Condition et Options envoyées aux commandes

Tous les types d'équipements proposent 2 options de configuration non obligatoire.

* Condition : il est possible de définir une expression qui devra être valide pour chaque déclenchement. Si la condition est fausse, aucune action de l'équipement ne s'éxécutera.

* Options : ce sont les options qui seront passées aux commandes de l'équipement. Par exemple : title="Mon message";message="Message de notification";color="#FF0000"

### Configuration des actions

Pour chaque action créée, on peut y rattacher une ou plusieurs actions de Jeedom ainsi qu'un scénario facultatif.

#### Condition et Options envoyées aux commandes

Comme au niveau de l'équipement, il est possible de définir une condition et des options envoyées à la commande.

La condition d'une action ne s'applique qu'à la commande. Si on a une condition sur l'équipement et l'action, les deux doivent être vraies.

Les options ne s'appliquent que sur la commande. Elles viennent fusionner avec celles de l'équipement si elles existent. Les valeurs au niveau de la commande prenant l'ascendence.

#### Type d'action

Pour les équipements de types planifié ou réccurent, le type d'action ne servira pas.

Pour les actions retardées, vous pouvez vous en servir pour faire matcher le type avec les actions déclenchées. Exemple choisir un type couleur permettra d'afficher sur le dashboard un choix de couleur qui sera envoyé aux commandes activées. Cette valeur d'option prend l'ascendant sur les options définies sur l'équipement ou la commande.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de dkron géré par le plugin. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
