# Changelog

Important : en cas de mise à jour disponible pour laquelle il n'y a pas d'information dans cette section, c'est qu'elle n'intègre aucune nouveauté majeure. Cela peut être un ajout de documentation, une correction de documentation, des traductions ou bien de la correction de bugs mineurs.


#### 19/07/2023 beta
- Correction des vigilances lors de l'utilisation de l'API. La date de la dernière interrogation n'était pas mise à jour.
- Récupération d'un 4ème fichier des vigilances CDP_TEXTES_VIGILANCE.json A voir si il y a des informations utiles à l'intérieur pour peut-etre renseigner les commandes Alertes qui sont vides depuis un moment.
- Ajout d'un séparateur vertical entre les jours dans les prévisions.
- Ajout d’icônes pour les intensités de pluie. les icones de pluie sont de couleur rouge quand les previsons de pluie sont désactivées.
- Correction des svgs de vigilance. ( Commentaires en trop )
- Suppression de la création de commandes obsolètes. Météo du jour - xxx - Vent,   Météo du Jour - H+1 - Icone
- Ajout dans la liste des commandes d'un équipement d'un bouton pour supprimer chaque commande.
- Corrections mineures sur les templates pour les commandes json  cmd.info.string
- Ajout de la direction du vent Variable avec son icône. Modifications des templates fournies en conséquence. Cela peut entrainer une modification sur vos templates custom.
- Ajout du % de la couverture nuageuse dans la prévision de l'heure actuelle.
- Modification de l'URL pour récupérer les clés de l'API Vigilances qui est un peu capricieuse https://portail-api.meteofrance.fr/devportal/apis -> https://portail-api.meteofrance.fr/devportal
***
#### 26/06/2023 Stable
Passage en stable du plugin. Toutes les modifications des versions beta ci-dessous sont inclues.

***
#### 25/06/2023 beta
- Divers réglages et mises au point des templates (principalement les templates pour mobile).
- Ajout du paramètre "Affichage prévisions en version mobile"

***
#### 23/06/2023 beta
- Les commandes heures, jours et moments ne sont plus vidées quand MF ne répond pas. Warning dans le log.
- Réduction des requêtes à MF. 1 requête OK / heure. Si NOK essai toutes les 5 minutes
- Récupération de l'éphéméride 1 fois par jour. Calcul sunrise et sunset si MF HS.
- Réduction du volume de logs en debug.
- Rétablissement de la commande Vigilancelist
- Possibilité d'utiliser l'API vigilance de MF dans la configuration du plugin pour récupérer les vigilances.
- Correction des templates.
  
***
#### 12/06/2023 beta
- Correction du lendemain qui ne s'affichait pas dans les prévisions.
- Correction des commandes Meteoproba*xxx* La commande MeteoprobaStorm est obsolète.
- Signalement dans les valeurs des commandes si elles sont obsolétes. Valeur -666 si numérique ou Obsolete command si de type texte.
- Correction des vigilances si MF publie des infos partielles. Seule la dernière (qui pouvait être partielle) était traitée.
- Correction des bulles d'aide sur les vigilances. La chronologie des niveaux de vigilance est ajoutée.
- Contournement de la suppression par le plugin virtuel des " dans les valeurs des commandes. Les widgets de commandes Json peuvent être utilisés pour isoler une information fournie par le plugin. Ex: info de la météo du jour sur un design ...
- Ajout de la commande Json: VigilanceJson avec l'ébauche de son widget: cmd.info.string.Vigilance.html
- Correction de la template pour affichage sur mobile.

***
#### 06/06/2023 beta
- Rétablissement des vigilances météo pour la métropole. Les données du site d'archives Météo France sont utilisées. Utilisation d'un cron pour récupérer les données chaque heure entre 6h et 20h. Les données sont fournies par MF pour la France entière au minimum à 6h et 16h. Les données sont stockées dans le répertoire data du plugin. (Fichiers: CDP_CARTE_EXTERNE.json et les 2 fichiers VIGNETTE_NATIONAL_J_500X500.png VIGNETTE_NATIONAL_J1_500X500.png )
- Ajout des commandes de prévisions par heures, moments de la journée et jours. Les valeurs de ces commandes sont en JSON. Ces nouvelles commandes sont créées lors de la mise à jour du plugin. 
  - Ajout de widgets pour ces 3 types de commandes. Ces commandes sont utilisables avec leur widget sur les designs. Elles ne sont pas utilisables sur des virtuels car le plugin virtuel en supprimant toutes les " de la valeur pulvérise le JSON. PR sur le plugin virtuel à faire. Les widgets ont des paramètres optionnels pour contrôler l'affichage des différentes valeurs.
  - La récupération des valeurs contenues dans le JSON de ces commandes peut se faire avec la fonction `meteofrance::getJsonInfo($cmd_id,$request);`
- Ajout de la possibilité de choisir un template pour représenter l'équipement. Templates custom possibles (Le nom du fichier template doit commencer par `custom.meteofrance.` ) Ex: `custom.meteofrance.Mon template.html`
  - Paramétrage de l'affichage de la prévision de l'heure suivante, du nombre de jours à afficher en moments de la journée et du nombre total de jours.
  - Remplacement de la Rose des vents par une fléche avec la vitesse du vent et celle des rafales s'il y en a. ( Pour les nostalgiques, la template Rose des vents est fournie. )

- Obsolescence des commandes: Météo du Matin, Météo du Midi, Météo du Soir et Météo de la nuit (soit 48 commandes) Ces commandes ne sont plus créées. Elles ne sont plus renseignées par le plugin. Elles sont remplacées par les commandes JSON: Moment de la journée *x* - Json ( logicalId: MeteoInstant*x*Json )
- Les 23 commandes Marine *xxx* et Marée *xxx* ne sont plus systématiquement créées. ( Selon `bulletin_cote` dans les détails de la localisation ) 
- Changement de source Météo France de `/rpcache-aa.meteofrance.com/internet2018client` à `/webservice.meteofrance.com` . Cela rend des commandes obsolètes. Ex: Vitesse, direction et rafales du vent dans les Météo du jour.


***

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
