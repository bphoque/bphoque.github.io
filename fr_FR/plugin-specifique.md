=== Plugins spécifiques

==== Plugin "Thermostat"

[IMPORTANT]
Pour configurer le plugin "Thermostat", il faut se référer à la https://jeedom.github.io/documentation/plugins/thermostat/fr_FR/index.html[documentation du plugin].

===== Configuration

Seuls les modes "Chauffer" et "Refroidir" sont à configurer. Il faut attribuer un mode du plugin "Thermostat" à un mode de HomeKit.

image::../images/thermostat.png[]

===== Présentation

image::../images/thermostat1.png[]

* *A* : Température Cible ou Consigne : Température envoyée au plugin Thermostat (Passe en mode Auto sur Maison et Eve / Mode Aucun sur widget Thermostat)
* *B* : Température Ambiante : Température de référence pour le plugin Thermostat.
* *C* : Commande de modification de la Consigne A : Augmenter ou diminuer la température à l’aide du curseur. Cela aura pour action de modifier également le mode du chauffage E qui passera à AUCUN dans le dashboard Jeedom.
* *D* : Statut du thermostat retourné par le plugin Thermostat : Arrêté (ou Désactivé ou Eteint) (Rond vert dans Maison) / Chauffage (Rond Orange dans Maison) / Climatisation (Rond Bleu dans Maison).

* *E* : Mode Auto (dans Maison ou Eve) : correspond au mode Aucun dans Jeedom où le Plugin Thermostat décide de ce qu'il doit faire en fonction de la température qu'on lui envoie. Ce mode permet de régler une température cible via le curseur C

* *F* : Mode Clim / Refroidir : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* *G* : Mode Chauf / Chauffer : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* *H* : Eteint / Off : permet d'éteindre le thermostat.
* *I* : Verrouillage/Protection Enfants (uniquement dans Eve) : permet de verrouiller le thermostat. (modifié)

===== Utilisation

En cliquant sur "CHAUF" ou "Chauffer", on active le mode du thermostat associé. Idem pour "CLIM" ou "Refroidir".

==== Plugin "Alarme"

[IMPORTANT]
La fonctionnalité de l'alarme dans Homebridge est compatible uniquement (pour l'instant) avec le plugin Jeedom "Alarme". Pour configurer le plugin "Alarme", il faut se référer à la https://jeedom.github.io/documentation/plugins/alarm/fr_FR/index.html[documentation du plugin].

*Ce mode fonctionne avec l'application d'Apple Maison et celle d'Elgato Eve.*

===== Configuration

Dans HomeKit, la fonction alarme est gérée suivant 4 modes : "Désactivée", "Nuit", "A distance" et "Domicile".

Depuis l'application Maison : 

image::../images/alarme.png[]

Depuis l'application Eve : 

image::../images/alarmeeve.png[]

Le mode "Désactivé", inhibe l'ensemble des modes d'alarme du plugin "Alarme". Les actions de l'onglet "Désactivation OK" sont lancées (en fonction du mode de sortie).

image::../images/inhibe.png[]

Les 3 autres modes, sont à définir dans la configuration du plugin Homebridge.

image::../images/configalarme.png[]

[IMPORTANT]

Le "mode Jeedom" correspond aux modes du plugin "Alarme".

image::../images/modealarme.png[]

Il suffit d'affecter le "mode Jeedom" au mode Homebridge choisi.

===== Utilisation

Il suffit de cliquer sur l'icone "Alarme" dans l'application Maison.

image::../images/iconealarme.png[]

Et de sélectionner le mode.

image::../images/selmodealarme.png[]

L'alarme est activée.

Sur le dashboard : 

image::../images/alarmeactive.png[]

Sur l'application Maison : 

image::../images/alarmeactive2.png[]

Pour la désactiver, il suffit de sélectionner "Désactivée". Les actions définies dans la partie "Désactivation OK" du plugin "Alarme" vont s'exécuter.

image::../images/desactivationok.png[]

En cas de déclenchement de l'alarme, une notification apparaît sur le téléphone.

image::../images/alarmedeclanchee.png[]

Pour la désarmer, il faut cliquer sur l'icône "Alarme" et sélectionner "Désactivée".

image::../images/reinitialiseralarme.png[]

Les actions définies dans la partie "Réinitialisation" du plugin "Alarme" vont s'éxécuter.

image::../images/reinitialisation.png[]



