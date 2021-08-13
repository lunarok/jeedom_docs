# QR Code Manager

## Présentation

Le plugin permet de gérer des codes (QR Code ou Barcode). Ils peuvent être importés par image ou créer en saisissant leur contenu.
Leur utilisation se fait via panel sur desktop ou mobile.

## Configuration



### Créer des QR Code spécifiques

Il est possible de créer des QR Code qui seront automatiquement reconnus pour une fonction précise, par exemple :

- Localisation : en utilisant geo: en début de contenu avec latitude et longitude ensuite (geo:51.185013,-1.859105)
- Numéro de téléphone : en commencant avec "tel:"
- Un email : en commencant par "mailto:" et en ajoutant ensuite "?subject=" et enfin "&body=" (exemple mailto:test@test.go?subject=test&body=test)
- Un site web : en commencant par "https://"
- Un SMS : avec "smsto:" et le texte séparé par une virgule (exemple smsto:00000,texte)
- Une connexion Wifi : avec "WIFI:T:WPA;S:<SSID>;P:<PSWD>;;"
- Un contact : en utilisant le contenu d'un vcard
- Un évènement : en utilisant le contenu d'un vevent

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non.

## Changelog

[Voir la page dédiée](changelog.md).
