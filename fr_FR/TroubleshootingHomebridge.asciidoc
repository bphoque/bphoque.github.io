=== Aide Homebridge

==== Support

*Merci de passer par le forum, de créer *un* sujet par demande et de lire les autres sujets s'ils ressemblent au votre (ceux créés après la sortie de ce plugin, c'est logique :-))*

==== Point important

[IMPORTANT]
Les références vers l'état dans les actions sont primordiales !! Sinon pas de lien entre l'état et ses actions possibles.

Pour un "virtuel" : 

image::../images/reference-etat.png[]

Pour un accessoire physique (Dimmer 2 de Fibaro par exemple) : 

image::../images/ref2.png[]

==== FAQ

*-> Le pont Homebridge n'apparaît pas dans l'application Maison !*

TIP: Vérifiez que vous êtes connectés au même réseau que le pont Homebridge et que les fonctions Igmp snooping ou dns multicast sont activées sur votre box, routeur ou switch. Le protocole HomeKit n'est pas routable.

*-> Je n'arrive pas à inclure Jeedom dans HomeKit !*

TIP: Vérifiez que le statut du démon Homebridge est sur OK.

image::../images/demonHB.png[]

TIP: Pour inclure votre Jeedom dans HomeKit, via une application compatible (par exemple Maison ou Eve), vérifiez que votre appareil iOS est connecté au même réseau que votre Jeedom.

image::../images/config-pluginhb.png[]

*-> Le démon Homebridge ne veut pas démarrer !*

TIP: Vérifiez que vous disposez de la dernière version des dépendances. En cas de doute, il est possible de les réinstaller en cliquant sur "Relancer". Si la réinstallation des dépendances ne fonctionne pas ou indique une erreur dans le log des dépendances, cliquez sur "Réparer et Réinstaller".

image::../images/dependances-homebridge.png[]

*-> Mon équipement n'apparaît pas dans Homebridge !*

TIP: Vérifiez que la case "Envoyer à Homebridge" est cochée dans la configuration du plugin Homebridge.

*-> La case "Envoyer à Homebridge" est bien cochée mais mon équipement n'apparaît toujours pas !*

TIP: Vérifiez dans la configuration de votre équipement que celui-ci est activé, et dans une pièce.

TIP: Vérifiez que les types génériques sont bien configurés. Chaque équipement envoyé à Homebridge doit avoir au moins un type générique "Etat".

image::../images/ypegelumi.png[]

*-> J'ai mon Homebridge qui n'exécute pas les commandes !*

TIP: Il faut bien mettre à jour le plugin App Mobile, puis dans la configuration des dépendances, il suffit de renseigner un utilisateur avec des droits d'exécution sur les commandes.

*-> J'ai bien le retour d'état d'un équipement mais impossible de le piloter !*

TIP: Vérifiez que les types génériques sont bien configurés. Il doit y avoir une cohérence entre les types. Si vous avez le type "Info Lumière Etat", vérifiez que les actions sont de types "Action / Lumière Bouton On" etc... Voir aussi la référence à l'état (le point important ci-dessus)

*-> Le message "sans réponse" apparaît dans l'application Maison ou Eve*

image::../images/sans-reponse.jpg[]

1. Si vous n'avez pas de concentrateur HomeKit (iPad ou Apple TV), vérifiez que vous êtes connecté au même réseau que votre Jeedom. 
2. Vérifiez que le démon est activé. Si ce n'est pas le cas, redémarrez le.
3. Relancez votre box.
4. Si malgré tout vous avez toujours ces états, lancez une réparation.

TIP: Beaucoup d'informations se trouvent dans les logs, le prochain chapitre vous expliquera comment les analyser.
