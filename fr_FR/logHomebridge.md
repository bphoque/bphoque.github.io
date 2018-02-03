=== Interprétation des LOGS Homebridge

[source,]
----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 1 (111)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire visible, pas coché pour Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire Ignoré
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----
[TIP]
L'Accessoire 1 est visible mais la case "Envoyer vers Homebridge" n'est pas cochée. L'accessoire ne sera donc pas ajouté dans Homebridge.


[source,]
----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 2 (222)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Nouvel accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] [INFO]  Ajout service :Accessoire 2 subtype:222-918|0|920- cmd_id:918 UUID:00000049-0000-1000-8000-0026BB765291
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] [INFO]     Caractéristique :On valeur initiale:false
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Ajout de l'accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----
[TIP]
L'Accessoire 2 est visible et la case "Envoyer vers Homebridge" est cochée. L'accessoire sera donc ajouté dans Homebridge.


[source,]
----
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 3 (333)
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Info/Prise Etat"
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire sans Type Générique
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire Ignoré
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] └─────────
----
[TIP]
L'Accessoire 3 est visible et la case "Envoyer vers Homebridge" est cochée. Mais il n'y a pas de type générique "Etat" (ou celui-ci n'est pas visible). L'accessoire ne sera donc pas intégré dans Homebridge. Pour corriger ce problème, ajoutez le type générique "Info / Prise Etat" à l'accessoire (ou cochez la case "visible").


[source,]
----
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 4 (444)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Info/Lumière Etat" ou "Info/Lumière Couleur"
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Action/Prise Bouton On" ou reférence à l'état non définie sur la commande On
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ Nouvel accessoire (Accessoire 4)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [INFO]  Ajout service :Accessoire 4 subtype:444-919|0|921- cmd_id:919 UUID:00000049-0000-1000-8000-0026BB765291
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [INFO]     Caractéristique :On valeur initiale:false
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ Ajout de l'accessoire (Accessoire 4)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] └─────────
----
[TIP]
Il y a une incohérence entre les types génériques. Les types "actions" ne correpondent pas au type "info". Pour corriger le problème, modifiez les types génériques de l'accessoire en gardant une cohérence entre les types actions et info.


[source,]
----
sh: 1: homebridge: not found
----
[TIP]
Les dépendances Homebridge ne sont pas installées ou certains fichiers sont manquants. Cliquez sur "Relancer".

image::../images/dependances-homebridge.png[]
