== Configuration du plugin Homebridge

=== Création du pont Homebridge

Pour créer le pont Homebridge, il faut aller dans la rubrique "Gestion", et cliquer sur "Configuration".

image::../images/gestion.png[]

Pour créer le pont, il suffit de lui donner un nom et un code "PIN".

image::../images/config-pluginhb.png[]

* *Nom Homebridge* : Permet de nommer le pont Homebridge. 

[IMPORTANT]
Le changement de nom Homebridge obligera à reconfigurer les applications HomeKit.

* *PIN Homebridge* : Permet de personnaliser le code PIN Homebridge.

[IMPORTANT]
Les PIN suivants ne sont pas acceptés par Apple : 000-00-000, 111-11-111, 222-22-222 -> 999-99-999, 123-45-678, 876-54-321. Son changement obligera la reconfiguration des applications HomeKit.

* *Réparer* :  Permet une réparation de Homebridge en modifiant les identifiants. 

[IMPORTANT]
Il faut retirer le bridge de l'application "Maison".

* *Réparer & réinstaller* : Supprime et réinstalle complètement Homebridge. 

[IMPORTANT]
A n'effectuer que sur conseil d'un membre du forum et il faut retirer le pont de l'application "Maison".

* *Plateforme Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type plateforme (homebridge-camera-ffmpeg ou homebridge-nest par exemple).

* *Accessoire Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type accessoire (homebridge-freemote par exemple).

[IMPORTANT]
Réservé à un public averti. Il n'y aura aucun support pour ces deux dernières parties.

Une fois les cases *nom Homebridge et PIN Homebridge* correctement renseignées, la configuration se finalise en cliquant sur **Sauvegarder**. Le démon redémarre.

[TIP]
Un QR code est généré automatiquement. Cela améliore l'intégration du pont jeedom dans Homekit. Voir la partie "Ajout de Jeedom dans HomeKit".

=== Ajout des accessoires dans Homebridge

Les équipements seront à ajouter manuellement. 

image::../images/config-piece.png[]

Afin d'intégrer un accessoire dans Homebridge, il faut sélectionner la pièce où il se trouve.

image::../images/choix-acc.png[]

Afin d'ajouter un accessoire à Homebridge, il suffit de cocher la case "Envoyer à Homebridge". Pour sauvegarder, il suffit de cliquer sur la petite disquette verte.

[IMPORTANT]
*Si des modifications ont été faites, comme le changement du type générique, la modification d'un paramètre, l'ajout d'un accessoire il faut impérativement redémarrer le Démon pour la prise en compte dans Homebridge.*

==== Configuration des types génériques

===== Généralités

En cliquant sur l'équipement, les types génériques utilisés pour la communication entre votre Jeedom et Homebridge apparaissent.

image::../images/typegen-1.png[]

La majorité des types génériques est déjà renseignée. Dans certains cas, une configuration manuelle sera nécessaire (pour le plugin Virtuel par exemple).

Voici les types génériques disponibles : 

Pour les informations : 

image::../images/typeginfo.png[]

Pour les actions : 

image::../images/ypegeaction.png[]

include::configurationHomebridgeTypeGenerique.asciidoc[]

*Des exemples de configurations sont disponibles à la fin de la documentation*

Pour valider, il faut aller dans la configuration du plugin et relancer le démon Homebridge en cliquant sur "(Re)Démarrer".

image::../images/demon-homebridge.png[]

==== Ajout de Jeedom dans HomeKit

Il existe plusieurs applications sur l'appstore compatibles HomeKit. L'application "Maison" d'Apple sera utilisée pour la rédaction de la documentation.

image::../images/app-domicile.jpg[]

Le pont peur être inclu manuellement en entrant le code PIN et en sélectionnant le pont ou automatiquement en scannant le QR code.

===== Ajout du pont par QR code

Pour ajouter le pont dans Homekit, il suffit de scanner le QR code avec l'application "Appareil photo". 

image::../images/qr-code.png[]

Une notification est affichée en haut de l'écran. Il suffit de cliquer dessus et le pont est inclu automatiquement dans Homekit.

image::../images/qr-code1.png[]

[IMPORTANT]
Comme expliqué plus haut dans la doc, Homebridge n'est pas reconnu officiellement par Apple. Un message indique que l'accessoire n'est pas certifié, il faut valider l'inclusion en cliquant sur "Poursuivre l'ajout".

image::../images/qr-code2.png[]

Le pont est maintenant intégré dans Homekit.

===== Ajout manuel du pont

L'inclusion de Jeedom dans HomeKit, se fait en ouvrant l'application "Maison" et en cliquant sur "Ajouter un accessoire". 

image::../images/home-1.jpg[]

[TIP]
Dans l'exemple, le domicile s'appelle "Test". Son nom peut être modifié en allant dans les réglages de l'application.

Il faut scanner le code PIN 

image::../images/home-2.jpg[]

[TIP]
*Le code PIN peut être également rentré manuellement en cliquant sur "Code absent ou impossible à scanner ?".*

Il faut sélectionner le pont à inclure.

image::../images/home-3.jpg[]


[IMPORTANT]
Comme expliqué plus haut dans la doc, Homebridge n'est pas reconnu officiellement par Apple. Un message indique que l'accessoire n'est pas certifié, il faut valider l'inclusion en cliquant sur "Poursuivre l'ajout".

image::../images/home-4.png[]

*Le pont Jeedom est maintenant intégré à HomeKit.*

[IMPORTANT]
*Il n'est pas possible d'inclure le pont Jeedom sur plusieurs appareils IOS. Pour utiliser Homebridge sur plusieurs appareils IOS, il suffit de partager le domicile en suivant la procédure suivante :*

image::../images/partage.png[]

==== Rangement des accessoires dans HomeKit

Les accessoires doivent être rangés correctement dans HomeKit. Il faudra créer des pièces pour y intégrer les accessoires.

[IMPORTANT]
*Les pièces dans Jeedom ne sont pas importées dans Homebridge. Ceci n'est pas dû à Jeedom mais à la gestion des pièces par Apple.*

Le premier accessoire à "ranger" est le pont Jeedom. 

image::../images/home-5.jpg[]

Il faut sélectionner la pièce où sera installé le pont. Si elle n'existe pas, il faudra la créer en cliquant sur "Créer".

image::../images/home-05.jpg[]

Définir le nom de la nouvelle pièce. Il est également possible de lui attribuer un fond d'écran dédié. Pour finaliser la création de la pièce, il faut cliquer sur "Enregistrer".

image::../images/home-051.jpg[]

Maintenant, il ne reste plus qu'à ranger tous les accessoires dans les différentes pièces.

image::../images/home-052.jpg[]

[TIP]
*La fonction "Inclure dans les favoris" permet d'afficher l'accessoire dans la page principale de l'application*

image::../images/home-053.jpg[]

*Les accessoires doivent être "rangés" un par un. Si il y en a beaucoup, cette partie prendra du temps*.

La documentation complète de l'application "Maison" d'Apple est disponible https://support.apple.com/fr-fr/HT204893[ici].
