# Ntfy

## Présentation

Le plugin permet d'envoyer des notifications via le service Ntfy, que ce soit ntfy.sh ou une instance auto-hébergée.

## Configuration

Sur un équipement, vous devez remplir le champ URL avec l'URL de notification ntfy.

Par exemple, pour un topic `mytopic` sur ntfy.sh, URL devra être : `https://ntfy.sh/mytopic`.

Sur une instance auto-hébergée, ca sera par exemple : `https://ntfy.self.hosted/mytopic` (si l'instance est sur `https://ntfy.self.hosted` bien sûr).

Les champs `user` et `password` sont disponibles si vous avez mis en place une authentification sur votre instance auto-hébergée.

### Commandes

Une commande unique est créée : « Envoi de message ». Le message sera le contenu publié. Le champ `title` permet de passer les options supportées par Ntfy, en les séparant par un point virgule.

Exemple : `Title: Unauthorized access detected;Priority: urgent;Tags: warning,skull`.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui, celles de Ntfy. Le SaaS ou self-hosted suivant votre configuration.

## Changelog

[Voir la page dédiée](changelog.md).
