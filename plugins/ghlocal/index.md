# Google Home Local

## Présentation

Ce plugin a pour but de gérer vos Google Home et par extension vos Chromecast.

Le plugin permet d'envoyer des médias vers vos Google Home et Chromecast, qu'ils soient locaux, distants, ou des rapports Jeedom ou bien encore consulter un site pour les écrans.

Pour les Google Home, il permet aussi de récupérer les alarmes et timers, l'activation du mode silencieux, le scan bluetooth

## Configuration

Le plugin dispose d'une page de configuration pour entrer vos identifiants Google pour récupérer les tokens Google Home.

Pour trouver ce token : https://gist.github.com/rithvikvibhu/1a0f4937af957ef6a78453e3be482c1f

Pour chaque équipement créé manuellement, il faut indiquer si c'est un Google Home ou Chromecast, ainsi que son IP.

Pour les Google Home, un champ "Nom dans Google Home" est à remplir, il permet de récupérer le token d'accès à l'API locale. Le nom est visible dans Google Home ou dans les logs du plugin en mode debug quand on sauvegarde la configuration.

Les périphériques Bluetooth sont créés automatiquement.

Les commandes sont créées automatiquement dans tous les cas.

## Commandes

Les commandes suivantes sont communes aux Google Home et Chromecast (car elles utilisent la fonctionnalité Chromecast du Google Home) :

Stop lecture : arrête toute lecture en cours

Pause lecture : met en pause la lecture en cours

Reprise lecture : reprend la lecture en cours

Définir volume lecture : règle le volume des medias en %

Jouer un Fichier : permet de lancer un média supporté par le GH/Chromecast (audio sur tout, pour ce qui dispose d'un écran, ca peut être une image ou vidéo).

Ouvrir une URL : permet d'afficher un site sur un GH/Chromecast avec écran (ou lire une vidéo youtube)

Ouvrir une URL Jeedom : permet d'afficher Jeedom sur un GH/Chromecast avec écran (et de le controler si cet écran est tactile comme le Nest Hub)

Commande Scénario : est prévue pour être utilisée en scénario sur les commandes report et notification de caméra

Radio : permet de lire une des radios, c'est une commande de type select avec une liste prédéfinie

Sons locaux : permet de lire un des sons présents dans le plugin (des sons de notification). Le plugin propose un modal permettant de gérer les fichiers.


Les Google Home ont des commandes spécifiques qui s'appuient sur leur API locale non officielle :

Alarmes informations brutes : présente un json des informations sur les alarmes définies sur le GH

Alarme existante : info binaire indiquant si au moins une alarme existe

Alarme existante ce jour : info binaire indiquant si la prochaine alarme est aujourd'hui

Heure de la prochaine Alarme : heure au format Jeedom (pour l'utiliser avec un scénario et en condition "A ...." par exemple) de l'alarme

Timers informations brutes : présente un json des informations sur les timers définies sur le GH

Timer existant : info binaire indiquant si au moins un timer existe

Durée original du timer (en mn) : durée d'origine du compte à rebours

Heure du prochain Timer : heure au format Jeedom (pour l'utiliser avec un scénario et en condition "A ...." par exemple) du timer

Volume Alarmes (avec Définir Volume Alarme) : volume spécifique des alarmes

Etat Notification (avec Notification On, Notification Off) : commandes gérant et indiquant le mode DND (Do Not Disturb)

Rafraichir : standard Jeedom

Redémarrer : pour redémarrer votre GH

Les Android TV :

Commande notification : avec titre et message. Titre et Message correspondent aux deux champs de l'api pipup. IL est possible de saisir les autres en utilisant le champ titre. Il faut alors saisir par exemple :
title=Mon Titre,duration=42,position=2
Plus d'infos sur les champs : https://github.com/rogro82/pipup

Les Android ADB, pour vos Android sur lesquels vous avez activer les commandes ADB via le réseau :

- Select Commande : qui permet de choisir une commande prédéfinie (le plugin vient avec une dizaine, mais un modal vous permet d'en ajouter, qui seront alors dispo sur tous les équipements Android ADB)

- Commande spécfique : de type message, vous pouvez y saisir une commande à envoyer

- Commande info : contient le retour de la dernière commande adb éxécuter

Et les périphériques Bluetooth scannés par au moins une GH se voient dotés d'une commande RSSI par Google Home à portée. On peut ainsi obtenir le RSSI relatif d'un objet bluetooth par rapport à plusieurs points correspondant aux GH. Une commande générale "Visible" est positive (1) si au moins un des Google Home trouve le périphérique dans les 5 mns passées, elle est nulle si aucun Google Home ne le détecte dans les 5 dernières minutes.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Google Home. C'est donc sur le réseau local.

> Quels formats sont supportés ?

Pour les fichiers, il s'agit de MP3, MP4, PNG. Plus les URL de site et Youtube.

> Quelle est la fréquence des informations sur les GH ?

Toutes les 5 mns par défaut (voir le tableau des cron utilisés par le plugin sur la page de configuration générale plugin)

> Je n'arrive pas à faire fonctionner le scan des Google Home, je suis sous Debian Stretch (9) ?

Les scripts utilisés nécessitent une version de golang non présente en Stretch. Il est préférable de passer sur la dernière Debian Stable, à savoir en 2020 Debian Buster.

> Je n'arrive pas à faire fonctionner le scan dans un Docker ?

Les scripts utilisés pour se connecter au Google Play Services posent des difficultés en docker à cause de l'identification matérielle. Il est alors possible d'activer l'option sur la page de configuration pour avoir le token mis à jour par API. Et il faut alors déployer le script get_tokens.py du répertoire resources sur un autre serveur, le lancer en cron et envoyer le résultat par api via https://jeedom/plugins/ghlocal/core/api/jeeGHlocal.php?apikey=...&token=...

## Changelog

[Voir la page dédiée](changelog.md).
