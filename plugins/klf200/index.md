# KLF200 - Passerelle IO Homecontrol - Velux

## Présentation

KLF200 est un boitier de chez Velux permettant d'y associer des périphériques IO Homecrontrol. Il possède une interface filaire et aussi une API locale Ethernet.

C'est cette dernière qui est utilisée par Jeedom et permettre ainsi de piloter des appareils IO Homecrontrol en local.

Le plugin permet de controler : "Window", "Blind", "RollerShutter", "GarageDoor", "Awning", "Blade", "Light", "Switch"

## Configuration

### Configuration du KLF200

La connexion Ethernet ne servira que pour l'API, la configuration se fait via le Wifi de la gateway.

Pendant les 20 mns après branchement, le KLF200 fournit un réseau Wifi sur lequel on peut se connecter et qui permet de faire les ajouts de devices et autres

Pour se connecter au Wifi, vous reconnaitrez le nom par "KL200_***" et le mot de passe à utiliser est sur le boitier (on en aura besoin aussi pour Jeedom)

Ensuite, rendez vous sur velux.info avec le compte admin et en mot de passe velux123. Vous pouvez alors ajouter les devices par le moyen supporté qui correspond à votre cas (le plus simple étant la recopie d'une télécommande tactile KLR 200)

Faites attention de bien nommer vos devices sans espace, c'est impératif pour le plugin Jeedom

### Configuration du plugin

Le plugin nécessite deux paramètres à saisir sur la page de configuration du plugin :

  * l'adresse IP de la gateway KLF200 (celle de la carte ethernet)
  
  * le mot de passe du KLF200 (celui utilisé pour le Wifi)
  
  * commandes à utiliser pour allumer et éteindre le KLF200 (en cas de bug sur la communication, le plugin utilisera ces commandes pour relancer le KLF)
  
Ensuite, un bouton scan est disponible : il créera chaque équipement trouvé sur le KLF200 + un équipement global "Window" si au moins une a été trouvée (pareil pour les stores)

### Configuration des équipements

Chaque équipement est créé automatiquement, il affiche son ID, nom et type sur KLF200. Pour les commandes, il y a :
- Niveau ouverture
- Ouverture binaire
- Fermer
- Ouvrir
- Stop
- Définir ouverture (slider en %)
- Refresh

Les équipements ont les types génériques de type volets roulants définis par défaut pour permettre de les remonter dans Google Smart Home par exemple

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, le plugin utilise l'API locale du KLF 200.


## Changelog

[Voir la page dédiée](changelog.md).
