# Cas d'usage, exemples d'implémentation

Voici quelques exemples d'utilisation.

## Vérification du log d'erreurs Web

La commande est : check_log

Les arguments par exemple : -F /usr/share/nginx/www/jeedom/log/nginx-error.log -O /tmp/nginx.tmp -q ?

## Vérification du log cron_execution de Jeedom

La commande est : check_log

Les arguments par exemple : -F /usr/share/nginx/www/jeedom/log/cron_execution -O /tmp/cron_exec.tmp -q PHP

## Vérification des logs plugins

La commande est : /check_logserror.sh

Les arguments par exemple : -D /usr/share/nginx/www/jeedom/log

## Vérification de la sauvegarde Market

La commande est : /check_cloudbackup.php

## Vérification de la présence d'un fichier de sauvegarde récent

La commande est : /check_backup.sh

Les arguments par exemple : -D /usr/share/nginx/www/jeedom/backup

## Vérification de l'uptime

La commande est : /check_uptime.pl

Les arguments par exemple : -c 30

## Vérification de la mémoire

La commande est : check_mem

Les arguments par exemple : aucun

## Vérification de l'utilisation CPU

La commande est : check_load

Les arguments par exemple : -w 5,5,5 -c 10,10,10

## Vérification de la présence d'un service

Un des checks à disposition est check_procs. Un usage basique est de lui donner le nombre de process qui doivent être existants et le label à chercher.

Voici quelques exemples de configuration :

![Illustration](check_procs.png?raw=true "Illustration")

Dans cet exemple, le service ne remontera qu'en warning, donc visible sur le widget mais sans remontée automatique d'alerte par Jeedom (mais bien sûr, c'est faisable avec un scénario).

Comme pour tout check, pour plus de possibilités et d'arguments, n'hésitez pas à passer la commande ""/usr/lib/nagios/plugins/check_procs -h" pour avoir l'aide.

## Vérification du RAID d'un serveur distant

Un exemple avec l'utilisation d'un check distant et un utilisant sudo:

![Illustration](check_disks.png?raw=true "Illustration")

Dans cet exemple, il y a deux checks différents :

  - le premier vérifie l'état SMART de chaque disque (en utilisant sudo en même temps);

  - le deuxième vérifie l'état global du RAID logiciel.

Ces deux checks ont été copiés dans un répertoire du serveur qui les exécute, sans que nagios-plugins soit installé dessus.

## Vérification d'un NAS Synology

Par défaut, le paquet nagios-plugins n'a pas de check pour les NAS Synology. Mais comme dit, on peut ajouter tout script au format Nagios (le format Nagios n'impose pas un langage mais une norme de sortie 0/1/2/3 suivant OK/WARN/CRIT/UNK).

Exemple, le script disponible ici :

https://exchange.nagios.org/directory/Plugins/Network-and-Systems-Management/Others/Synology-status/details

On le télécharge, on le copie dans le répertoire de /usr/lib/nagios/plugins/ de notre Jeedom (via WinSCP par exemple) sans oublier de le rendre éxécutable (chmod +x).

Il faut également installer snmp : sudo apt-get install snmp

Essayer ensuite en SSH la commande :

  /usr/lib/nagios/plugins/check_snmp_synology -2 public -h adresse_syno -v

En remplacant -2 par la version SNMP, public par la communauté et bien sûr adresse_syno par l'adresse du NAS.

Dans l'équipement on ajoute une commande et on saisit :

  - le nom souhaité;

  - on ne coche ni sudo ni ssh;

  - check_snmp_synology dans la boite check;

  - pour les options : -2 public -h adresse_syno (comme plus haut mettre les valeurs qu'il faut).

Comme pour tout check, pour plus de possibilités et d'arguments, n'hésitez pas à passer la commande ""/usr/lib/nagios/plugins/check_snmp_synology -h" pour avoir l'aide.
