# Telegram

## Présentation

Telegram est un service de messagerie chiffré bout à bout. Ce qui veut dire que même les serveurs intermédiaires ne voient pas ce qui transite.

Vous pouvez l'utiliser pour envoyer des messages depuis et vers Jeedom.

Telegram accepte les pièces jointes également (pour le plugin Caméra par exemple).

Il est également possible dans un message de spécifier en option "tts" ou "geoloc" pour un message.

Le plugin accepte également la fonction 'ask' de Jeedom et fournira un clavier spécifique avec des touches pré-remplies contenant les réponses.

## Configuration

Le plugin ne comporte pas de configuration générale.

Sur la page santé, un test pour vérifier le https en connexion externe est fait. Il n'est pas possible en l'état d'utiliser un certificat auto signé.

Un certificat letsencrypt fonctionne (en ayant bien paramétré le certificat de chaine également)

### Configuration d'un équipement

Chaque équipement correspond à un Bot telegram.

Vous devez donc rentrer la clef fournie par Telegram à la création du bot sur la page équipement.

Vous pouvez configurer le bot pour créer des notifications silencieuses sur les téléphones.

Il est possible de personnaliser le texte que le bot répond à un message et le format par défaut des messages du bot.

Vous pouvez également préciser un emplacement pour stocker les fichiers envoyés au bot. Dans ce cas, les fichiers seront créés suivant le format :

* vidéo : $username.mp4

* photo : $username.png

* document : nom du fichier envoyé

Par la suite, les utilisateurs entrant en communication avec le bot créeront automatiquement une entrée sur l'équipement pour envoyer des messages si l'option est activée.

Pareil pour les groupes et le 'ask' marche sur les groupes (il ne marche pas pour le destinataire "Tous")

### Envoyer des messages

Les commandes actions permettent d'envoyer des messages. Il est possible de fournir des options pour les messages (dans la zone option, sous la forme option="valeur")

* tts : la valeur doit être le chemin d'un fichier audio de type ogg encodé avec opus qui sera notifié en message vocal dans Telegram (sinon un texte mais opus-tools doit être installé)

* snapshot : avec une url de snapshot de camera IP pour envoyer un snapshot

* rtspSnapshot : pour les cameras sans URL de snapshot image, créer une image fixe (nécessite ffmpeg)

* rtspVideo : pour envoyer une courte vidéo de 10s depuis l'url rtsp

* location : la valeur doit être soit une commande geoloc soit "latitude,longitude"

* file : la valeur doit être le path d'un ou plusieurs fichiers

* message : permet d'envoyer un message dans le même ordre

* disable_notify : valeur binaire pour que la notif soit silencieuse (1) ou avec son/vibration (0)

* parse_mode : format du message envoyé (correspond à l'option de conf équipement), valeurs possibles : '', HTML, Markdown

* answers_per_line : cette option n'est utilisée que dans le mode 'ask' et permet de définir combien d'options de réponses sont présentées par ligne. Elle doit être placée comme première option de réponse du 'ask' sous la forme answers_per_line=2

Exemple : tts=/fichier.ogg file=/screen1.png,/screen2.png disable_notify=0

Toutes les pièces jointes ajoutées à une commande action sont envoyées avec un type détecté par rapport à leur extension :

* vidéos en extensions "avi,mpeg,mpg,mkv,mp4,mpe"

* audios en extensions "ogg,mp3"

* images en extensions "gif,jpeg,jpg,png"

* les autres types sont envoyés en tant que pièces jointes

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, il utilise les API Telegram (la version Bot)

>Est-ce que mes données sont visibles sur les serveurs de transit ?

Non, Telegram garantit le chiffrement client à client.

>Est-ce qu'on peut utiliser des emojis ?

Oui, en utilisant son code HTML. Par exemple vous trouverez des emojis avec leur code ici :
https://www.quackit.com/character_sets/emoji/

>Quels sont les tags HTML disponibles pour formater les messages ?

On trouve la liste ici :
https://core.telegram.org/bots/api#html-style

>Est-ce qu'on peut utiliser de la notation Markdown à la place du HTML ?

Oui, soit en configurant tout l'équipement, soit en envoyant l'option dans un message. Pour plus d'informations sur le formatage Markdown avec Telegram :
https://core.telegram.org/bots/api#markdown-style

## Troubleshooting

>Je n'ai pas de retour de Telegram

Il faut bien avoir une adresse en HTTPS, Telegram refuse d'utiliser une URL http en webhook (ce point est visible dans la page santé). De plus, Telegram n'accepte que les ports 443, 80 et 88

>Je ne reçois pas un fichier envoyé

Il faut vérifier que le user www-data a bien accès au fichier envoyé (et aux répertoires parents).

>Le 'ask' sur tous les destinataires ne marche pas

C'est normal, il ne peut pas fonctionner car Telegram ne sait pas reconnaître l'utilisateur à qui on a envoyé la question de celui qui répond, il faut utiliser les groupes pour cela

>Mon utilisateur telegram n'arrive pas à communiquer avec Jeedom / Les messages n'arrivent pas dans Jeedom

Merci de vérifier que vous avez bien paramétré un username dans votre profil Telegram. Regardez le menu options ou settings via le menu sandwich (les 3 barres horizontales les unes sur les autres)

>Après un 'ask', le clavier avec réponses reste actif si il n'y a pas eu de réponse, comment faire ?

Il suffit d'envoyer un message sur timeout avec l'option remove=1

## Changelog

[Voir la page dédiée](changelog.md).
