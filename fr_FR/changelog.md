=== Plugin HomeBridge

==== v1.4.0 (???)
    * Meilleur code de génération pour le QRcode (en php)
    * Changement de plusieurs libellés dans la configuration du plugin.
    * Nouveau type spécifique homebridge : "Occupation" légèrement différent de "mouvement" dans Maison et dans Eve, il est plus clair pour par exemple afficher une présence (plutot qu'un mouvement).
    * Nouveau type spécifique homebridge : "Online" permettant de passer le composant en "Sans réponse" dans Maison s'il a la valeur de 0.
    * Meilleur gestion du type Haut-Parleur (si pas de Mute)
    * Gestion automatique pour la serrure TheKeys
    * Séparation des types "Prise" et "Interrupteur"
    * Les prises dans Jeedom sont maintenant des vrais prises dans Homebridge
    * Les scénarios Jeedom sont ajoutés en tant qu'interrupteur dans Homebridge (si sélectionné dans la configuration) [En cours]
    * Composant "Pression" modifié pour apparaitre mieux dans Eve
    * Les interrupteur programmables dans homekit font leur apparition :)
      ** Interrupteur Programmable (Multi-Valeur) (Homebridge) : Il s'agit d'un interrupteur avec une commande de type info qui contiendra plusieurs valeurs en fonction du type de click effectué. ("click", "double_click", "long_click" par exemple ou encore 11 , 21 , 30). Ces valeurs sont configurables.
      ** Interrupteur Programmable Binaire (Simple Click) (Homebridge) : Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un simple click sur le bouton.
      ** Interrupteur Programmable Binaire (Double Click) (Homebridge) : Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un double click sur le bouton.
      ** Interrupteur Programmable Binaire (Long   Click) (Homebridge) : Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un long click sur le bouton.
    * Affichage des graphiques dans l'application Eve (support Alpha). Fonctionne pour les types suivants :
      ** Température (chaque point de donnée est une moyenne des 10min précédentes)
      ** Humidité (chaque point de donnée est une moyenne des 10min précédentes)
      ** Pression (chaque point de donnée est une moyenne des 10min précédentes)
      ** Porte ou Fenêtre 
      ** Mouvement 
      ** Puissance Electrique (chaque point de donnée est une moyenne des 10min précédentes)
[IMPORTANT]      
      Il s'agit d'un support Alpha, juste car c'est fun :) Les graphiques ont été développés par ingénierie inversée des composants Elgato Eve et il peut y avoir des incohérences. Les données des graphiques sont les données collectées lorsque le démon Homebridge est démarré, il peut donc manquer certaines informations. Les graphiques sont là à titre informatif.

==== v1.3.5 (12-12-2017)
    * Suppression du besoin de sélection de l'utilisateur
    * Plus besoin que les actions réfèrent l'état auquel elles sont liées sauf si multi-prises ou multi-relay (on split)
    * QRCode pour configurer le bridge (attention, les cameras et plateformes supplémentaires doivent toujours scanner le PIN)
    * Plus jolie config
    * Afficher une erreur si l'adresse interne est en https
    * Mise à jour de Homebridge en 0.4.32 et HAP-Nodejs en 0.4.36

==== v1.3.4 (29-11-2017)
    * Réécriture du mode de fonctionnement des thermostats, plus logique :)
    * Accessoire supplémentaire pour installer les plugin Homebridge qui ne publient qu'un accessoire
    * Mise à jour documentation.
    * Corrections de bugs

==== v1.3.3 (13-11-2017)
    * Modification documentation
    * Gestion des actions Ouvrir et Fermer pour les portes de garages.
    * DebugInfo affiche maintenant le log de création d'accessoires (si celui-ci n'est pas encore tronqué)

==== v1.3.2 (09 et 10 et 12-11-2017)
    * Fichier fusionné pour la doc
    * Autre bug sur Inversion corrigé
    * Bug Siri "Ouvre tous les volets du salon" corrigé
    * Meilleure réparation et réinstallation
    * Documentation corrigée

==== v1.3.1 (31-10-2017)
    * Bug invertBinary sur présence sans inversion
    * Mise à jour documentation
    * Compatibilité Serrure Nuki

==== v1.3 (30-10-2017)
    * Plugin séparé du plugin App Mobile.
    * Récupération de la configuration du plugin App Mobile s'il est installé.
    * Meilleure réparation et installation plus poussée pour éviter des problèmes divers.
    * Documentation complètement réécrite et adaptée par @bphoque, près de 60 pages A4 !!!
    * Type "Info/Générique" supporté pour les infos Jeedom de type Numérique, Binaire, Autre dans l'application Eve uniquement (pas encore disponnible dans "Maison").
[IMPORTANT]
ne pas modifier ce type dans Jeedom pendant que Homebridge fonctionne
    * Les types génériques "Info/Choc", "Info/Vent (direction)", "Info/Vent (vitesse)", "Info/Pluie (mm/h)", "Info/Pluie (accumulation)", "Info/Pression", "Info/Son (dB)" sont gérés comme des "Info/Générique" et affichés dans Eve.
    * Lumières : Fonctionnement est corrigé pour certains plugins (voir annonce forum)
[TIP]
Si vous aviez un pont Philips Hue v1, vous avez maintenant accès à HomeKit :)
    * Alarme : les modes sont liables aux modes imposés d'HomeKit : Absent, Nuit, Présent, Désactivé. Fonctionne en consultation ET action.
    * Thermostat : (Fonctionne mieux dans Eve) : Température de consigne fonctionne, les modes peuvent être liés aux modes imposés d'HomeKit : Chauf., Clim.. L'asservissement se faisant dans Jeedom, le mode auto ne sert à rien dans HomeKit. Le statut est dans un champ générique (visible dans Eve) (cette façon de faire permet de lier les modes et d'avoir une fonctionnalité supplémentaire au lieu  de simplement vous montrer que votre chauffage chauffe). Le verrouillage apparait aussi dans Eve.
    * Nouveau design du plugin, simplification, plus besoin de choisir les plugins qui seront envoyés à Homebridge, le choix est maintenant par équipement.
    * Fenêtre "DebugInfo" (en niveau de log "info" ou "debug") pour donner des éléments importants de votre configuration en cas de demande d'aide sur le forum (à la demande).
    * Périphériques invisibles ajoutés à Homebridge, tant que "Envoyer dans Homebridge" est coché.
    * Temporisation des Slider des lumières et des volets et volumes, sinon toutes les valeurs sont envoyées à Jeedom, maintenant elles ne le sont que si le slider dans Maison ne bouge plus depuis 500ms.
    * Type Générique officiel Sabotage supporté (binaire).
    * Possibilité de personnaliser les états des Portes de Garage (Ouvert (255), En Ouverture (254), Stopé (253), En Fermeture (252), Fermé (0)) avec d'autres valeurs.
    * Les types spécifiques à Homebridge : j'ai maintenant la possibilité de créer des types spécifiques pour Homebridge, ceux-ci ne font pas partie du core (comme les types génériques) mais les complètent. Il faut néanmoins les définir manuellement dans le plugin (les types génériques restent utilisés principalement, ces types sont un ajout pour les types génériques qui n'existent pas).
    * Nouveaux types spécifiques à Homebridge : 
      ** Status Defectueux (binaire : 0:non/ 1:oui -> peut-être mappé à un binaire représentant par exemple un lien mort chez Z-Wave) .
      ** Status Actif (binaire : 0:non/ 1:oui -> peut-etre mappé au status "online" d'une Xiaomi Yeelight par exemple).
      ** Haut-parleurs, il devrait fonctionner automatiquement avec le plugin Sonos par exemple (à tester), les types sont : 
         *** Info/Haut-parleur Mute (binaire)
         *** Info/Haut-parleur Volume (pourcentage)
         *** Action/Haut-parleur Mute
         *** Action/Haut-parleur Unmute
         *** Action/Haut-parleur Toggle Mute (soit Toggle soit Mute/Unmute, les deux choix sont possibles séparément)
         *** Action/Haut-parleur Volume (typiquement un slider)
[IMPORTANT]
Info/Haut-parleur Mute est obligatoire, c'est étrange mais c'est une obligation coté HomeKit.

==== v1.2.1
    * Bugfix : capteurs Fenêtres
    * Bugfix : volets Somfy
    * Bugfix : Consommation Electrique qui bug sur composants Z-Wave
    * Bugfix : En chargement pour périf avec batterie

==== v1.2.0
    * Realease Stable

==== v1.1.4

    * Bugfix : unregister Accessories si on a une erreur
    * Update Homebridge & HAP-NodeJS
    * Bugfix : Temperature isNaN -> 0
    * pré-support Sabotage
    * Bugfix : Interdire une valeur Null ou Undefined d'être envoyée à HomeKit
    
==== v1.1.2

    * Support basique Alarme : besoin d'une config coté plugin pour mapper les modes NUIT, ABSENT, PRESENT avec des ALARM_SET_MODE Jeedom
    
==== v1.1.1 
    * Bugfix : Restauration des valeurs en cache au redémarrage
    * Bugfix : Bornage des valeurs du détecteur de lumière
    
==== v1.1.0 

    * Support des Plateformes Homebridge en mode expert (Cameras, autre...)
    * Documentation code
    * Freeze des fonctionnalités, debugging à faire en vue de version stable
    
==== v1.0.27

    * Simplifié l'ajout/suppression des services
    * Commencé à résoudre les problèmes LightBulbs mais pas terminé
    
==== v1.0.26

    * Gestion pourcentage batterie via le type générique "BATTERY"
    * Si < 20% on set un flag "LowBattery" dans Homekit pour afficher dans Maison/Eve/...
    * Gestion du "charge en cours" définit sur "non chargeable" pour l'instant car il faut voir comment on gère ca coté Jeedom

==== v1.0.25 

    * Nettoyage du code et simplification
    * Meilleure gestion des services en cas de modification de ceux-ci (modification des types génériques)

==== v1.0.24

    * Optimisation (on break les boucles si on a trouvé l'élément, plus rapide sur les grosses installations)

==== v1.0.23

    * si un volet est ouvert à 95% afficher 100% dans Maison (usure mécanique, recalibration)

==== v1.0.22

    * Préparation des Sonnettes en prévision du support dans HomeKit par Apple

==== v1.0.21

    * Corrigé la gestion des Serrures, elles fonctionnent
        *!!! si vous utilisez un iPad comme concentrateur HomeKit, pensez a désactiver Siri pour éviter à qqun de crier "siri ouvre la porte d'entrée" par la boite aux lettres (c'est arrivé !) !!!*

==== v1.0.20

    * Logs plus clairs et plus de verbosité sur la création des Characteristics

==== v1.0.19

    * Support pour les portes de garage/barrières, N'utiliser que BARRIER_STATE ou GARAGE_STATE (même traitement, états 255,254,253,252,0) et GB_TOGGLE

==== v1.0.18

    * Combiné les types OPENING et OPENING_WINDOW car c'est un même type dans Homebridge.
    * Ajout du Model (nom du type de l'eqLogic) et du Serial Number (id de l'objet + id logique) dans Homebridge.

==== v1.0.17

    * Prise en charge du niveau de debug du plugin App Mobile (il faut sauver le niveau et relancer le demon pour prise en charge)
    * Simplification du code (retiré des choses inutiles comme la création d'un serveur http)

==== v1.0.16

    * activation d'un mode debug dans la plateforme, il sera lié au status du plugin.
    * Francisation des messages du log, plus de verbosité, plus de clareté et de détails pour encore mieux vous aider en cas de problème.
    * Modification des paramètres de composition des UUID, uniquement l'id Jeedom et le nom du périphérique (la pièce Jeedom entrait en considération).
[IMPORTANT]
Cela signifie qu'à l'installation de cette version, vos périphériques dans Maison vont disparaitre pour réapparaitre dans la pièce par défaut (et casser vos scènes et automations).

        ** Point positif : vous pouvez maintenant changer de pièce dans Jeedom les périphériques sans les perdre dans Maison. Malheureusement, ils ne changeront pas dans Maison (non-implémenté dans Homebridge).
        ** j'ai gardé le nom du périphérique pour l'instant dans l'identifiant car le renommage d'un périphérique dans Jeedom casserait tout dans Maison (pour l'instant) de toute façon.
    * Modification du délais d'interrogation-longue pour optimiser les systèmes avec moins de changements d'états.
    * Modification du modèle de fonctionnement. Maintenant on prend un état des périphérique au démarrage du plugin et on le met à jour en temps réel à chaque changement dans Jeedom ou Maison. Moins de requêtes sur l'API Jeedom, plus petits temps de réponse dans Maison.
    * Ajout d'un ramasse miettes à la fin de l'ajout des périphériques présent dans Jeedom à Homebridge, tout ce qui n'a pas été ajouté/modifié est supprimé d'Homebridge (si vous avez rendu invisible un périf ou supprimé dans Jeedom par exemple).
    * Suppression du bouton Regénérer le fichier de configuration : plus besoin, lorsqu'on sauvegarde la configuration, on regénère le fichier automatiquement et on relance le daemon.
    * Suppression du bouton Effacer le cache : plus besoin, on gère la suppression individuelle des périphériques. 
[TIP]
Si vous avez un problème avec un périphérique malgré tout : décochez "Envoyer à Homebridge" | relancez le daemon | décochez "Envoyer à Homebridge" | relancez le daemon : il sera recréé tout proprement (et dans la pièce par défaut de Maison).

    * Ajout d'avertissements et de messages d'attention si on s'approche du nombre fatidique de 100 accessoires envoyés dans Homebridge (HomeKit ne supporte pas plus de 100 accessoires).
    * Au démarrage du daemon, vérification si avahi-daemon et dbus sont bien lancés, sinon, les démarrer.
    * A l'install des dépendances, passer avahi-daemon et dbus à enabled si pas le cas.
    * Corrections diverses, simplifications et optimisations.
    
    
