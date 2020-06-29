# Human Centric Lighting

## Présentation

Permet de gérer vos lumières à travers Jeedom pour le quotidien. Le plugin crée un équipement par objet de Jeedom. Il scanne tous les équipements avec le type générique lumière disponibles dans la catégorie Lumière de l'objet.

Le plugin permet de :

- gérer des "ambiances" ou types d'éclairage (lecture, repas, soirée ...) qui correspondent à un éclairage donné (par exemple en lecture, seule la lampe de chevet de la pièce sera allumée à 70% en blanc froid)

- lier un/des déclencheur(s) (comme les détecteurs de mouvement) pour activer en automatique un mode

- gérer un timer pour éteindre automatiquement les lumières

- ajouter une sonde de luminosité pour ne pas allumer la lumière quand ce n'est pas nécessaire (avec seuil configurable)

- basculer l'ambiance utilisée par défaut (pour gérer via la présence, les modes, l'heure, le sommeil ...). Exemple : passer en ambiance soirée au coucher du soleil pour l'éclairage automatique. Mais en pouvant toujours passer en ambiance lecture en appuyant sur un interrupteur

- utiliser des valeurs "Circadian Lighting" pour l'éclairage

## Configuration

### Scan

Le plugin s'appuie sur un scan des équipements Jeedom et des objets.
Pour chaque objet, il va créér un équipement "Gestion Lumière". Chaque équipement de la catégorie "Lumière" y sera lié et visible sur la page de l'équipement "Light Management"

Pour pouvoir utiliser les différentes commandes du plugin, le scan utilise également les types génériques. Ainsi, une lampe pour pouvoir y faire un on/off devra proposer à minimum Lumière Bouton On/Lumière Bouton Off/Lumière Etat. Une seule lampe par équipement est possible.

Voici les types nécessaires sur l'équipement pour permettre les actions :

|Fonction|Types à avoir sur l'équipement|
|On/Off|Lumière Bouton On,Lumière Bouton Off,Lumière Etat|
|Luminosité|Lumière Slider,Lumière Etat (et Lumière Etat(Binaire) pour la version binaire du coup)|
|Température|Lumière Température Couleur(action),Lumière Température Couleur(info)|
|Couleur|Lumière Couleur(action),Lumière Couleur(info)|

### Correction des équipements

Le plugin permet aussi de "corriger" automatiquement les équipements trouvés (il s'assure que les commandes action pointent bien vers leur valeur info, que la visibilité et widget soient cohérents)

Sur chaque équipement "Light Management", vous retrouvez un tableau avec les équipements liés et leur statut (OK/NOK) pour les fonctions switch/luminosité/température/couleur. En cas de défaut de type générique, il est possible d'accéder directement à l'équipement par le lien présenté.

### Gestion des paramètres

Des paramètres sont utilisés par le plugin et sont ajustables à plusieurs niveaux (valeur par défaut, page de conf du plugin, page de l'équipement, modal de l'ambiance). La valeur utilisée est connue ainsi :

- valeur présente sur le modal de l'ambiance en premier

- sinon, si définie sur l'équipement, c'est cette valeur qui est précisée

- sinon, si définie sur la page de configuration du plugin

- par défaut si rien d'autre n'est défini, c'est la valeur par défaut (visible sur la page de configuration)

Ainsi, si on définit une durée d'allumage de 2 mns sur la page de configuration, et 20 mns pour le salon, c'est bien 20 qui sera utilisé pour la lumière du salon.

Les paramètres disponibles :

- Durée d'allumage automatique

- Timer d'extinction automatique

- Timer de non déclenchement automatique

- Niveau de luminosité pour allumage sur détecteur

- Information du niveau de luminosité

## Utilisation

### Avec détecteur de mouvement

Si vous voulez saisir plusieurs détecteurs de mouvement, il faut bien mettre && entre chaque dans le champ.

Sur détection d'un mouvement, la lumière sera allumée, SAUF :

  - si la luminosité est suffisante
  
  - si la lampe n'est pas autorisée en ce moment
    
### Extinction automatique

Ce paramètre permet de mettre en place une vérification automatique que les lumières non nécessaires sont éteintes quand les détecteurs de mouvement n'ont plus de présence. Il est sans effet si le trigger n'est pas renseigné.

### Contrôle manuel

Plusieurs actions sont disponibles, des classiques : luminosités, on, off, température, couleur. Elles sont envoyées à toutes les lumières de manière normales.

Le toggle : lui envoie un OFF à toutes les lumières, si AU MOINS 1 lumière est allumée. Sinon c'est un ON

Le "Mode Courant" : active le mode défini avec (Mode Select) -> c'est ce mode qui est lancé par les détecteurs de mouvement

Le "Mode Once" : va lancer juste cette fois un mode sélectionné dans le menu

"On Force" : va allumer les lampes, même si la luminosité est suffisante

### Les modes

Le plugin permet de gérer différents modes. Certains viennent en standard, mais il est possible de créer des personnalisés.

Pour les standards, ils concernent toutes les lampes de l'équipement :

  - Général : équivalent au classique, enverra un ON à toutes les lampes
  
  - Off : fait en sorte que toute commande sans "Force" ne déclenche pas l'allumage
  
  - Relax, Calme, Neutre, Attentif, Concentration : sont des modes utilisant des recommandations de luminosité/température pour le bien-être
  
  - Naturel : active les lumières dans une luminosité/température reproduisant le cycle naturel du soleil
  
Pour les modes personnalisés, via le modal vous pouvez choisir pour chaque lampe son état.

### Statut

Les statuts luminosité, température et couleur sont liés à l'équipement global sans corrélation par rapport aux lampes qui le constituent

Par contre, pour le statut général, il est à 1 si AU MOINS 1 lampe est allumée. Pour être à 0, tout doit être éteint.

Un indicateur permet de connaitre le nombre de lampes allumées.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non.

[Tu es un kevin, la suite ici](kevin.md).

## Changelog

[Voir la page dédiée](changelog.md).
