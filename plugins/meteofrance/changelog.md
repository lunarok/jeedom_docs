# Changelog

Important : en cas de mise à jour disponible pour laquelle il n'y a pas d'information dans cette section, c'est qu'elle n'intègre aucune nouveauté majeure. Cela peut être un ajout de documentation, une correction de documentation, des traductions ou bien de la correction de bugs mineurs.

#### 04/06/2023 beta
- Rétablissement des vigilances météo pour la métropole. Les données du site d'archives Météo France sont utilisées. Utilisation d'un cron pour récupérer les données chaque heure entre 6h et 20h. Les données sont fournies par MF pour la France entière au minimum à 6h et 16h.
- Ajout des commandes de prévisions par heures, moment de la journée et jours. Les valeurs de ces commandes sont en JSON. Ajout de widgets pour ces 3 types de commandes. Ces commandes sont utilisables avec leur widget sur les designs. Elles ne sont pas utilisables sur des virtuels car le plugin virtuel en supprimant toutes les " de la valeur pulvérise le JSON. PR sur le plugin virtuel à faire.
- Remplacement de la Rose des vents par une fléche avec dessous la vitesse du vent et celle des rafales s'il y en a. ( Pour les nostalgiques, la template Rose des vents est fournie. )
- Ajout de la possibilité de choisir une template pour représenter l'équipement. Templates custom possibles (Le nom du fichier template doit commencer par custom.meteofrance. )

#### 24/04/2023 beta
- Ajout des liens vers la doc pour les versions beta
- cronTrigger passe en setOnce afin d'être supprimé après son exécution.
- Controle de la fin d'exécution de cronTrigger pour l'affichage de l'équipement. (Erreur 500 si l'on affiche la tuile alors que les commandes ne sont pas toutes créées)
- Création de la commande refresh par cronTrigger. Cette commande est utilisée pour tester la fin de la création des commandes et pour rafraichir toutes les données.
- Après la création des commandes, cronTrigger met à jour les données. ( Evite d'attendre le passage du cronHourly pour avoir une tuile à jour )
- La tuile sur le dashboard affiche un message tant que les commandes ne sont pas créées.
- urlencode du nom de la ville
- Ajout de la colonne Etat dans la liste des commandes. ( Utile à partir de Jeedom v4.3 )
- Affichage de la liste des objets avec leur arborescence
- Ajout de l'icone 0.svg pour avoir un fichier local en cas d'erreur de configuratipn de l'équipement. ( Erreur de CSP )
- La tuile sur le dashboard affiche un message s'il y a une erreur de configuration de l'équipement.
- Corrections diverses pour limiter les PHP warning et PHP notice dans les fichiers log.
- Lors de la mise à jour du plugin, les équipements seront resauvés afin de créer la commande refresh.
- Modif de la template principale pour la partie pluie dans l'heure.
- ...
