=== Type Générique Custom

Le type générique "Custom" permet de faire remonter n'importe quelle valeur "info" de tout type dans Homebridge. *Quelques exemples sont décris dans ce chapitre.*

*L'information à remonter dans Homebridge ne doit pas dépasser 64 caractères.*  

[IMPORTANT]
*Seule l'application d'Elgato Eve est compatible avec ce type générique. Les équipements utilisant ce type générique n'apparaitront pas dans l'application Maison d'Apple.*

[IMPORTANT]
*Les interactions avec Siri ainsi que les automations ne sont pas possibles avec ce type générique*

[IMPORTANT]
*Il est n'est pas possible de renommer l'accessoire*

==== Utilisation avec le plugin Mode

Cela permet d'afficher l'intitulé du mode jeedom en cours.

image::../images/custom-1.png[]

Dans ce cas, il faut attribuer le type générique "Info/Générique" au nom de commande "Mode".


image::../images/custom-2.png[]

==== Utilisation avec le plugin Netatmo (station météo)

Cela permet d'afficher les informations de type pression, CO2, noise.

image::../images/custom-3.png[]

image::../images/custom-4.png[]

[TIP]
*Si le champ unité a été indiqué dans jeedom, il remontra dans le type custom.*

image::../images/custom-9.png[]

==== Utilisation avec le plugin vigilance méteo

image::../images/custom-7.png[]

image::../images/custom-6.png[]




