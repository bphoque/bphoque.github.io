Présentation Homebridge
=======================

*Le plugin Homebridge* est un demon qui permet d’interagir avec un système domotique via l’assistant vocal Siri sous iOS. Le HomeKit a été introduit depuis iOS 8, mais est véritablement opérationnel depuis iOS 10 via l’application Maison. 

![homekit-logo](../images/homekit-logo.jpg)

Le plugin Homebridge de Jeedom permet donc d’exposer des équipements Jeedom qui seront vus comme des accessoires compatibles au protocole *HomeKit*.

>Homebridge n'est pas officiellement supporté par Apple. A tout moment Apple peut bloquer ce protocole.

Que peut-on faire avec Homebridge ?
---------------------------------

Homebridge peut s'utiliser avec une application compatible HomeKit ou avec l'assistant vocal Siri.

Depuis iOS 10, l'application Maison (inclue par défaut avec iOS) permet le pilotage d'équipements compatibles HomeKit. 

![cuisine-homekit](../images/cuisine-01.png) ![cuisine-homekit](../images/salon-01.png) ![cuisine-homekit](../images/salle-de-bain-01.png)

Les équipements peuvent être classés par pièce. Il est également possible de mettre des accessoires en favoris sur la pages d'accueil. Une page spécifique indique l'ensemble des états des accessoires.

![piece-homekit](../images/piece-homekit.jpg) ![piece-homekit](../images/accueil-01.png) ![etat](../images/etat.png)

Beaucoup d'accessoires sont pris en charge.

![garage-homekit](../images/acchb.png)

Siri peut aussi interagir. Il répond aux questions et fait des actions.  

![siri-01](../images/siri-01.jpg) ![siri-02](../images/siri-02.jpg)

HomeKit a l'avantage d'être utilisable à l'extérieur du domicile. Seule condition: il faut disposer d'un concentrateur. 
L'iPad et l'AppleTV (et bientôt le HomePod) peuvent servir de concentrateur. Pour cela, ils doivent être connectés au même compte iCloud.


>HomeKit est le nom officiel du protocole développé par Apple. Homebridge est son équivalent Open Source développé par nfarina. Ce dernier a étendu le projet HAP-NodeJS qui est le moteur d'Homebridge.

Installation et activation du plugin Homebridge
==============================================

Le plugin Homebridge doit être installé via le market Jeedom. *Le plugin App Mobile officiel n'est plus indispensable.*

*Pour les migrations depuis le plugin App Mobile officiel, il est important de ne pas désactiver le plugin App Mobile. Une rubrique "Migration depuis le plugin App Mobile" est disponible dans la documentation.* 

![pluginHB](../images/pluginHB.png) ![pluginHB](../images/pluginHB2.png)

Une fois le plugin installé, il suffit de l'activer en cliquant sur "Activer".

![activationHB](../images/activationHB.png)

Installation des dépendances
----------------------------

Les dépendances sont installées automatiquement par Jeedom dans les 5 min. Elles seront également réinstallées lors d'une mise à jour du plugin si besoin.

![installationDep](../images/installationDep.png)

*Le temps d'installation des dépendances peut varier en fonction du matériel utilisé.*

*Systèmes compatibles avec Homebridge :*

* Raspberry Pi 2 et 3 (Le Pi 3 est conseillé)

* Box Jeedom Mini +

* Box Jeedom pro

* Box Jeedom smart

* Box Jeedom pro V2

* Tout système basé sur Debian 8 ou 9


>Les installations sous Docker et Raspberry Pi 1 ne sont pas compatibles avec cette version de Homebridge.

Une fois les dépendances installées, le démon se lance (dans les 5 min). Si le statut n'est pas sur "OK", il faut cliquer sur "(Re)Démarrer".

![demon-homebridge](../images/demon-homebridge.png)

Mise à jour manuelle des dépendances
------------------------------------

Pour mettre à jour manuellement les dépendances, il faut cliquer sur "Relancer".

![dependances-homebridge](../images/dependances-homebridge.png)

Fichiers LOG
------------

Les fichiers log permettent d'analyser pas à pas l'activité interne du processus et ses interactions avec son environnement.

Ces fichiers peuvent être nécessaires en cas de dysfonctionnement du plugin.

![log](../images/log.png)

* Homebridge : Historise toutes les communications avec le démon homebridge.

* Homebridge_daemon : Historise les actions effectuées par Homebridge (par exemple si un accessoire est envoyé à Homebridge mais n'apparaît pas dans l'application Maison, c'est ici qu'il faut aller voir).

* Homebridge_dep : Historise toutes les étapes de l'installation des dépendances. Si le démon refuse de démarrer par exemple, un coup d'oeil peut aider).

Configuration du plugin Homebridge
=================================

Création du pont Homebridge
--------------------------

Pour créer le pont Homebridge, il faut aller dans la rubrique "Gestion", et cliquer sur "Configuration".

![gestion](../images/gestion.png)

Pour créer le pont, il suffit de lui donner un nom et un code "PIN".

![config-pluginhb](../images/config-pluginhb.png)

* *Nom Homebridge* : Permet de nommer le pont Homebridge. 


>Le changement de nom Homebridge obligera à reconfigurer les applications HomeKit.

* *PIN Homebridge* : Permet de personnaliser le code PIN Homebridge.


>Les PIN suivants ne sont pas acceptés par Apple : 000-00-000, 111-11-111, 222-22-222 -> 999-99-999, 123-45-678, 876-54-321. Son changement obligera la reconfiguration des applications HomeKit.

* *Réparer* :  Permet une réparation de Homebridge en modifiant les identifiants. 


>Il faut retirer le bridge de l'application "Maison".

* *Réparer & réinstaller* : Supprime et réinstalle complètement Homebridge. 


>A n'effectuer que sur conseil d'un membre du forum et il faut retirer le pont de l'application "Maison".

* *Plateforme Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type plateforme (homebridge-camera-ffmpeg ou homebridge-nest par exemple).

* *Accessoire Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type accessoire (homebridge-freemote par exemple).


>Réservé à un public averti. Il n'y aura aucun support pour ces deux dernières parties.

Une fois les cases *nom Homebridge et PIN Homebridge* correctement renseignées, la configuration se finalise en cliquant sur **Sauvegarder**. Le démon redémarre.


>Un QR code est généré automatiquement. Cela améliore l'intégration du pont jeedom dans Homekit. Voir la partie "Ajout de Jeedom dans HomeKit".

Ajout des accessoires dans Homebridge
------------------------------------

Les équipements seront à ajouter manuellement. 

![config-piece](../images/config-piece.png)

Afin d'intégrer un accessoire dans Homebridge, il faut sélectionner la pièce où il se trouve.

![choix-acc](../images/choix-acc.png)

Afin d'ajouter un accessoire à Homebridge, il suffit de cocher la case "Envoyer à Homebridge". Pour sauvegarder, il suffit de cliquer sur la petite disquette verte.


>Si des modifications ont été faites, comme le changement du type générique, la modification d'un paramètre, l'ajout d'un accessoire il faut impérativement redémarrer le Démon pour la prise en compte dans Homebridge.

Configuration des types génériques
=================================

Généralités
----------

En cliquant sur l'équipement, les types génériques utilisés pour la communication entre votre Jeedom et Homebridge apparaissent.

![typegen-1](../images/typegen-1.png)

La majorité des types génériques est déjà renseignée. Dans certains cas, une configuration manuelle sera nécessaire (pour le plugin Virtuel par exemple).

Voici les types génériques disponibles : 

Pour les informations : 

![typeginfo](../images/typeginfo.png)

Pour les actions : 

![ypegeaction](../images/ypegeaction.png)


Lumière
----------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:---------:|-------------|
|Info/Lumière Etat (Binaire)|`NON`|Ajout pour les lumières dont la luminosité ne change pas lorsqu’elle est éteinte (Yeelight, Ikea, …​)<br/>0 = Eteint<br/>Autre que 0 = Allumé|
|Info/Lumière Etat|`OUI`|Luminosité<br/>0-100 Ou 0-99 ou 0-255<br/>(en fonction du max de Action/Lumière Slider)<br/>ou Binaire<br/>0 = Eteint<br/> autre que 0 = Allumé| 
|Action/Lumière Slider (Luminosité)|`OUI`|Réf. vers Lumière Etat|
|Action/Lumière Bouton On|`OUI`|Réf. vers Lumière Etat :<br/>- Binaire s’il est présent<br/>- Etat sinon|
|Action/Lumière Bouton Off|`OUI`|Réf. vers Lumière Etat :<br/>- Binaire s’il est présent<br/>- Etat sinon|
|Info/Lumière Couleur| `NON` |Format #RRGGBB|
|Action/Lumière Couleur|   `Si Info/Lumière Couleur `|Réf. vers Info/Lumière Couleur|
|Info/Lumière Température Couleur|`NON`|Réf. vers<br/>- Info/Lumière Température Couleur<br/>(Eve Seulement)|
|Action/Lumière Toggle|  `NON Utilisé`  |N/A|
| Action/Lumière Mode|  `NON Utilisé` |N/A|

Prises
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Prise<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Prise<br/>Bouton On|`OUI`|Réf. vers Info/Prise Etat| 
|Action/Prise<br/>Bouton Off|`OUI`|Réf. vers Info/Prise Etat|
|Action/Prise<br/>Slider|`NON Utilisé`|N/A|
|Action/Lumière<br/>Bouton Off|`OUI`|Réf. vers Lumière Etat :<br/>- Binaire s’il est présent<br/>- Etat sinon|


Volets
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Volet Etat|`OUI`|0 = Fermé<br/>> 95 = Ouvert|
|Action/Volet Bouton Monter|`Si Descendre`|Réf. vers Info/Volet Etat| 
|Action/Volet Bouton Descendre|`Si Monter`|Réf. vers Info/Volet Etat|
|Action/Volet Bouton Stop|`NON Utilisé`|N/A|
|Action/Volet Bouton Slider|`Si seul`|Réf. vers Info/Volet Etat|

Volets BSO
----------

Pas encore supportés

Chauffage fil pilote
---------------------

N’existe pas en HomeKit

Serrures
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Serrure Etat|`OUI`|pas 1 = Non Sécurisée<br/>1 = Sécurisée|
|Action/Serrure Bouton Ouvrir|`OUI`|Réf. vers Info/Serrure Etat| 
|Action/Serrure Bouton Fermer|`OUI`|Réf. vers Info/Serrure Etat| 

Sirènes
-------

N’existe pas en HomeKit

Thermostats
-------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Thermostat Etat (BINAIRE)|`NON`|0 = Eteint<br/>1 = Allumé|
|Info/Thermostat Etat (HUMAIN)|`NON`|Générique (Eve Seulement)| 
|Info/Thermostat Mode|`OUI si associé mode homekit`|Générique (Eve Seulement)| 
|Action/Thermostat Mode|`NON`|Peut être associé mode homekit|
|Info/Thermostat Température Extérieur|`NON utilisé`|N/A
|Info/Thermostat Température ambiante|`NON`|-50 → 100| 
|Info/Thermostat Consigne|`OUI`|10 → 38| 
|Action/Thermostat Consigne|`OUI`|10 → 38| 
|Info/Thermostat Verrouillage|`NON`|0 = Non Verrouillé<br/>1 = Verrouillé| 
|Action/Thermostat Verrouillage|`OUI si Info/Verrouillage`|N/A
|Action/Thermostat Déverrouillage|`OUI si Info/Verrouillage`|N/A

Portails ou Garages
--------------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Portail état ouvrant<br/>Info/Garage état ouvrant<br/>(même traitement)|`OUI`|0 = Fermé<br/>252 = Fermeture en cours<br/>253 = Stoppé<br/>254 = Ouverture en cours<br/>255 = Ouvert<br/>(Configurable)|
|Action/Portail ou garage bouton toggle|`Si seul`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant| 
|Action/Portail ou garage bouton d’ouverture|`Si pas Toggle`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant
|Action/Portail ou garage bouton de fermeture|`Si pas Toggle`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant

Haut-Parleurs (Eve Seulement)
-----------------------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Haut-Parleur Mute|`OUI`|1 = Pas de son<br/>0 = Son|
|Action/Haut-Parleur Mute|`Si pas Toggle`|Réf. vers Info/Haut-Parleur Mute| 
|Action/Haut-Parleur UnMute|`Si pas Toggle`|Réf. vers Info/Haut-Parleur Mute| 
|Action/Haut-Parleur Toggle Mute|`Si seul`|Réf. vers Info/Haut-Parleur Mute|
|Info/Haut-Parleur Volume|`NON`|%| 
|Action/Haut-Parleur Volume|`OUI si Info/HP Volume`|Réf. vers Info/Haut-Parleur Volume| 

Interrupteur programmable
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Interrupteur programmable<br/>(multi-valeur)|`NON`|Watts|
|Info/Interrupteur programmable "binaire"<br/>(Double Click)|`NON`|Watts|
|Info/Interrupteur programmable "binaire"<br/>Long Click)|`NON`|Watts|
|Info/Interrupteur programmable "binaire"<br/>Simple Click)|`NON`|Watts|


Generic
----------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Puissance Electrique|`NON`|Watts|
|Info/Consommation Electrique<br/>(cachée)|`NON`|KWh
|Info/Température|`NON`|-50→100 °C| 
|Info/Luminosité|`NON`|0.0001→ 100000 lux| 
|Info/Présence|`NON`|0 = Pas de mouvement<br/>1 = Mouvement|
|Info/Batterie|`NON`|%| 
|Info/Batterie en charge|`NON`|0 = NON<br/>pas 0 = OUI| 
|Info/Détection de fumée|`NON`|pas 1 = Pas de fumée détectée<br/>1 = fumée détectée| 
|Info/Inondation|`NON`|pas 1 = Pas de fuite détectée<br/>1 = fuite détectée| 
|Info/Humidité|`NON`|%| 
|Info/Porte<br/>Info/Fenêtre<br/>(même traitement)|`NON`|pas 1 = Contact<br/>1 = Pas de contact| 
|Info/Sabotage|`NON`|1 = Pas de sabotage<br/>0 = Sabotage| 
|Info/Détection de fumée|`NON`|1 = Pas de sabotage<br/>1 = fumée détectée| 
|Info/Choc|`NON`|Générique (Eve Seulement)
|Info/Pression|`NON`|Générique (Eve Seulement)
|Info/Son (dB)|`NON`|Générique (Eve Seulement)
|Info/UV|`NON`|Générique (Eve Seulement)
|Info/Générique|`NON`|Valeur <64 charactères<br/>avec Unité indiquée ou pas<br/>(Eve Seulement)| 
|Action/Générique<br/>(N’existe pas en HomeKit)|`NON`|N/A|
|Info/Pluie (accumulation)|`NON`|Générique (Eve Seulement)|
|Info/Vent (direction)|`NON`|Générique (Eve Seulement)|
|Info/Vent (vitesse)|`NON`|Générique (Eve Seulement)|
|Info/Actif|`NON`|0 = inactif<br/>1 = actif|
|Info/Defectueux|`NON`|0 = non<br/>1 = oui|

*Des exemples de configurations sont disponibles à la fin de la documentation*

Pour valider, il faut aller dans la configuration du plugin et relancer le démon Homebridge en cliquant sur "(Re)Démarrer".

![demon-homebridge](../images/demon-homebridge.png)

Ajout de Jeedom dans HomeKit
===========================

Il existe plusieurs applications sur l'appstore compatibles HomeKit. L'application "Maison" d'Apple sera utilisée pour la rédaction de la documentation.

![app-domicile](../images/app-domicile.jpg)

Le pont peut être inclu manuellement en entrant le code PIN et en sélectionnant le pont ou automatiquement en scannant le QR code.

Ajout du pont par QR code
-------------------------

Pour ajouter le pont dans Homekit, il suffit de scanner le QR code avec l'application "Appareil photo".  Une notification est affichée en haut de l'écran. Il suffit de cliquer dessus et le pont est inclus automatiquement dans Homekit. 

![qr-code](../images/qr-code.png)
![qr-code1](../images/qr-code1.png)
![qr-code21](../images/qr-code21.png)

>Comme expliqué plus haut dans la doc, Homebridge n'est pas reconnu officiellement par Apple. Un message indique que l'accessoire n'est pas certifié, il faut valider l'inclusion en cliquant sur "Poursuivre l'ajout".

Le pont est maintenant intégré dans Homekit.

Ajout manuel du pont
-------------------

L'inclusion de Jeedom dans HomeKit, se fait en ouvrant l'application "Maison" et en cliquant sur "Ajouter un accessoire". 

![home-1](../images/home-1.jpg)


>Dans l'exemple, le domicile s'appelle "Test". Son nom peut être modifié en allant dans les réglages de l'application.

Il faut scanner le code PIN et sélectionner le pont à inclure. Le pont Jeedom sera intégré à Homekit

![home-2](../images/home-2.jpg)
![home-3](../images/home-3.jpg)
![home-4](../images/home-4.png)


>Le code PIN peut être également rentré manuellement en cliquant sur "Code absent ou impossible à scanner ?"



>Il n'est pas possible d'inclure le pont Jeedom sur plusieurs appareils IOS. Pour utiliser Homebridge sur plusieurs appareils IOS, il suffit de partager le domicile en suivant la procédure suivante :

![partage](../images/partage.png)

Rangement des accessoires dans HomeKit
====================================

Les accessoires doivent être rangés correctement dans HomeKit. Il faudra créer des pièces pour y intégrer les accessoires.


>Les pièces dans Jeedom ne sont pas importées dans Homebridge. Ceci n'est pas dû à Jeedom mais à la gestion des pièces par Apple.

Le premier accessoire à "ranger" est le pont Jeedom. Il faut sélectionner la pièce où il sera installé. Si elle n'existe pas, il faudra la créer en cliquant sur "Créer". Ensuite, il faut définir le nom de la nouvelle pièce. Il est également possible de lui attribuer un fond d'écran dédié. Pour finaliser la création de la pièce, il faut cliquer sur "Enregistrer".

![home-5](../images/home-5.jpg)
![home-05](../images/home-05.jpg)
![home-051](../images/home-051.jpg)

Maintenant, il ne reste plus qu'à ranger tous les accessoires dans les différentes pièces.

![home-052](../images/home-052.jpg)


>La fonction "Inclure dans les favoris" permet d'afficher l'accessoire dans la page principale de l'application

![home-053](../images/home-053.jpg)

**Les accessoires doivent être "rangés" un par un. Si il y en a beaucoup, cette partie prendra du temps**.

La documentation complète de l'application "Maison" d'Apple est disponible à cette adresse : https://support.apple.com/fr-fr/HT204893.

Migration depuis le plugin App Mobile
=====================================

Le nouveau plugin Homebridge importe automatiquement la configuration Homebridge du plugin App Mobile. Il n'y a aucune opération à faire. 

Lorsque l'importation est terminée, la rubrique Homebridge disparait des paramètres du plugin App Mobile. 

![plugnmobilesanshb](../images/plugnmobilesanshb.png)

Homebridge est complètement désolidarisé du plugin App Mobile. Il fonctionne maintenant de manière autonome.

Lors de l'installation du plugin Homebridge, tous les accessoires vont être indisponibles. C'est normal.

![migration1](../images/sans-reponse.png)

Dès que l'installation des dépendances est terminée, tous les accessoires seront de nouveau disponibles.

Troubleshooting
=================

Support
-------
**Merci de passer par le forum, de créer *un* sujet par demande et de lire les autres sujets s'ils ressemblent au votre (ceux créés après la sortie de ce plugin, c'est logique :-))**

Point important
---------------

>Les références vers l'état dans les actions sont primordiales !! Sinon pas de lien entre l'état et ses actions possibles.

Pour un "virtuel" : 

![plugnmobilesanshb](../images/reference-etat.png)

Pour un accessoire physique (Dimmer 2 de Fibaro par exemple) : 

![ref2.png](../images/ref2.png)

FAQ
----

**-> Le pont Homebridge n'apparaît pas dans l'application Maison !**

>Vérifiez que le statut du démon Homebridge est sur OK.

![demon-homebridge.png](../images/demon-homebridge.png)

>Pour inclure votre Jeedom dans HomeKit, via une application compatible (par exemple Maison ou Eve), vérifiez que votre appareil iOS est connecté au même réseau que votre Jeedom.

![config-pluginhb](../images/config-pluginhb.png)

**-> Le démon Homebridge ne veut pas démarrer !**

>Vérifiez que vous disposez de la dernière version des dépendances. En cas de doute, il est possible de les réinstaller en cliquant sur "Relancer". Si la réinstallation des dépendances ne fonctionne pas ou indique une erreur dans le log des dépendances, cliquez sur "Réparer et Réinstaller".

![dependances-homebridge](../images/dependances-homebridge.png)

**-> Mon équipement n'apparaît pas dans Homebridge !**

>Vérifiez que la case "Envoyer à Homebridge" est cochée dans la configuration du plugin Homebridge.

**-> La case "Envoyer à Homebridge" est bien cochée mais mon équipement n'apparaît toujours pas !**

>Vérifiez dans la configuration de votre équipement que celui-ci est activé, et dans une pièce.

<br/>

>Vérifiez que les types génériques sont bien configurés. Chaque équipement envoyé à Homebridge doit avoir au moins un type générique "Etat".

![ypegelumi](../images/ypegelumi.png)

**-> J'ai mon Homebridge qui n'exécute pas les commandes !**

>Il faut bien mettre à jour le plugin.

**-> J'ai bien le retour d'état d'un équipement mais impossible de le piloter !**

>Vérifiez que les types génériques sont bien configurés. Il doit y avoir une cohérence entre les types. Si vous avez le type "Info Lumière Etat", vérifiez que les actions sont de types "Action / Lumière Bouton On" etc... Voir aussi la référence à l'état (le point important ci-dessus)

**-> Le message "sans réponse" apparaît dans l'application Maison ou Eve**

![sans-reponse](../images/sans-reponse.png)

1. Si vous n'avez pas de concentrateur HomeKit (iPad ou Apple TV), vérifiez que vous êtes connecté au même réseau que votre Jeedom. 
2. Vérifiez que le démon est activé. Si ce n'est pas le cas, redémarrez le.
3. Relancez votre box.
4. Si malgré tout vous avez toujours ces états, lancez une réparation.

>Beaucoup d'informations se trouvent dans les logs, le prochain chapitre vous expliquera comment les analyser.

Interprétation des LOGS Homebridge
-----------------------------------

<pre><code>----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 1 (111)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire visible, pas coché pour Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire Ignoré
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 1 est visible mais la case "Envoyer vers Homebridge" n'est pas cochée. L'accessoire ne sera donc pas ajouté dans Homebridge.

<pre><code>----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 2 (222)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Nouvel accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] [INFO]  Ajout service :Accessoire 2 subtype:222-918|0|920- cmd_id:918 UUID:00000049-0000-1000-8000-0026BB765291
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] [INFO]     Caractéristique :On valeur initiale:false
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Ajout de l'accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 2 est visible et la case "Envoyer vers Homebridge" est cochée. L'accessoire sera donc ajouté dans Homebridge.

<pre><code>----
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 3 (333)
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Info/Prise Etat"
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire sans Type Générique
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Vérification d'existance de l'accessoire dans Homebridge...
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire non existant dans Homebridge
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire Ignoré
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 3 est visible et la case "Envoyer vers Homebridge" est cochée. Mais il n'y a pas de type générique "Etat" (ou celui-ci n'est pas visible). L'accessoire ne sera donc pas intégré dans Homebridge. Pour corriger ce problème, ajoutez le type générique "Info / Prise Etat" à l'accessoire (ou cochez la case "visible").

<pre><code>----

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
----</code></pre>

>Il y a une incohérence entre les types génériques. Les types "actions" ne correpondent pas au type "info". Pour corriger le problème, modifiez les types génériques de l'accessoire en gardant une cohérence entre les types actions et info.

<pre><code>----
sh: 1: homebridge: not found
----</code></pre>

>Les dépendances Homebridge ne sont pas installées ou certains fichiers sont manquants. Cliquez sur "Relancer"

![dependances-homebridge](../images/dependances-homebridge.png)


Exemple de configuration
=========================

Lumière
-------

Type d'accessoire : Dimmer 2 de Fibaro (Z-Wave)

![lumiere](../images/lumiere.png)

Type d'accessoire : Double contact de Nodon (EnOcean)

![lumiere-2](../images/lumiere-2.png)

Si les deux contacts sont utilisés, copier-coller les types génériques On-1 sur On-2, Off-1 sur Off-2 et Etat-1 sur Etat-2.

Température et hydrométrie
---------------------------

Type d'accessoire : Sonde Oregon (RfxCom) et Xiaomi Aqara

![temperature](../images/temperature.png)

Détecteur d'ouverture
----------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

### Fenêtre #

![fenetre](../images/fenetre.png)

Si un capteur de température est utilisé, mettre "Info / Température" sur le nom de la commande Température.

### Porte #

![porte](../images/porte.png)

Si un capteur de température est utilisé, mettre "Info / Température" sur le nom de la commande Température.

Détecteur de fuite
------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

![fuite](../images/fuite.png)

Détecteur de fumées
--------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

![fumee](../images/fumee.png)

Volets roulants
----------------- 

Type d'accessoire : Détecteur Fibaro FGR-222 (Z-Wave)

![volet](../images/volet.png)

Porte de garage
-----------------

Type d'accessoire : Aeotec - Contrôleur de porte de garage (GEN5) (Z-Wave)

![garage](../images/garage.png)

Interrupteur programable
-----------------------

### Interrupteur programmable multi-valeur #

Type d'accessoire : NODON Interrupteur mural Z-Wave Plus

![bouton](../images/bouton.png)

La tableau ci dessus indique les valeurs renvoyées par l'interrupteur pour chaque type d'appuie. Il faudra reporter les valeurs dans les paramètres du plugin.

![tg-inter](../images/tg-inter.png)

Type d'accessoire : Bouton simple Click XIAOMI Aquara

![bouton-xiaomi](../images/bouton-xiaomi.png)

### Interrupteur programmable binaire #

Virtuel
--------

Type d'accessoire : Interrupteur bistable avec le plugin virtuel

![virtuel](../images/virtuel.png)

![virtuel-tg](../images/virtuel-tg.png)

Caméra
------

Homebrige prend en charge les caméras.

![camera2.](../images/camera2.png)

En touchant la capture de la caméra souhaitée, elle s'affiche en plein écran et en live !

![camera3](../images/camera3.png)

Suivant les configurations matérielles, la qualité de la transmission peut varier. Par exemple, sur un NUC gen7 core i7, c'est quasiment du live ! La latence est très faible.

Celles-ci peuvent afficher une notification lorsqu'un mouvement est détecté par un capteur de présence. Il faut que la caméra et le capteur soient configurés dans la même pièce et que les notifications du capteur soient activées.

![notig](../images/notif.jpg)

Les caméras décrites ci-dessous ont été testées. Elles sont donc fonctionnelles dans Homebridge.

L'intégration des caméras se fait via la bouton rouge "Plateforme Homebridge supplémentaire".

![plateforme-hb](../images/plateforme-hb.png)

### Foscam C1 # 

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Salon",
         "videoConfig":{
            "source":"-re -i rtsp://login:password@xxx.xxx.xxx.xxx:554/videoMain",
            "stillImageSource":"-i http://192.168.1.121:88/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30,
            "vcodec": "h264"
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam C1 V2 # 

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Son nom",
         "videoConfig":{
            "source":"-re -i rtsp://login:password@xxx.xxx.xxx.xxx:Portrtsp/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam FI9821P #

<pre><code>{
         "name":"son nom",
         "videoConfig":{
            "source":"-re -i rtsp://login:password@xxx.xxx.xxx.xxx:Port/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam FI9803 V3 #

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Son nom",
         "videoConfig":{
            "source":"-re -i rtsp://login:password@xxx.xxx.xxx.xxx:Portrtsp/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

### wanscam rtsp HWXXX #

<pre><code>{
 "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Arrière",
         "videoConfig":{
            "source":"-re -i rtsp://login:password@xxx.xxx.xxx.xxx:554/1",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx/web/tmpfs/snap.jpg",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30,
            "vcodec": "h264"
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Dlink DCS-5020L #

<pre><code>{
  "platform": "Camera-ffmpeg",
  "cameras": [
    {
      "name": "Camera Cellier",
      "videoConfig": {
        "source": "-re -f mjpeg -i http://login:password@xxx.xxx.xxx.xxx/mjpeg.cgi",
        "stillImageSource": "-f mjpeg -i http://login:password@xxx.xxx.xxx.xxx/image/jpeg.cgi",
        "maxStreams": 2,
        "maxWidth": 640,
        "maxHeight": 480,
        "maxFPS": 30,
        "vcodec": "h264"
      }
    }
  ]
}
</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Netatmo Welcome #

Cette caméra deviendra officielement compatible HomeKit courant 2018. 
Son intégration dans Homebridge est néanmoins possible.

<pre><code>{
"platform": "Camera-ffmpeg",
"cameras": [
{
"name": "Camera Name",
"videoConfig": {
"source": "-re -i http://xxx.xxx.xxx.xxx/Local_Access_Key/live/files/high/index.m3u8",
"stillImageSource": "-i http://xxx.xxx.xxx.xxx/Local_Access_Key/live/snapshot_720.jpg",
"maxStreams": 2,
"maxWidth": 1280,
"maxHeight": 720,
"maxFPS": 30
}
}
]
}</code></pre>


Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP la caméra et Local_Access_Key -> voir dans le plugin Caméra l'URL de capture /Local_Access_Key/live/snapshot_720.jpg.

![camera](../images/camera.png)

### Configurer plusieurs caméras (ou plateformes) #

Pour configurer plusieurs caméras, il suffit de mettre une barre entre les deux configurations.

<pre><code>{
  "platform": "Camera-ffmpeg",
  "cameras": [
    {
      "name": "Cellier 1",
      "videoConfig": {
        "source": "-re -f mjpeg -i http://login:password@adresseIP/mjpeg.cgi",
        "stillImageSource": "-f mjpeg -i http://login:password@adresseIP/image/jpeg.cgi",
        "maxStreams": 2,
        "maxWidth": 640,
        "maxHeight": 480,
        "maxFPS": 30,
        "vcodec": "h264"
      }
    }
  ]
}
|
{
"platform": "Camera-ffmpeg",
"cameras": [
{
"name": "Salon 1",
"videoConfig": {
"source": "-re -i http://adresseip/xxxxxxx/live/files/high/index.m3u8",
"stillImageSource": "-i http://adresseIP/xxxxxx/live/snapshot_720.jpg",
"maxStreams": 2,
"maxWidth": 1280,
"maxHeight": 720,
"maxFPS": 30
}
}
]
}</code></pre>

**Cela est également valable pour toute autre plateforme comme le thermostat NEST par exemple.**

Type Générique Custom
---------------------

Le type générique "Custom" permet de faire remonter n'importe quelle valeur "info" de tout type dans Homebridge. **Quelques exemples sont décris dans ce chapitre.**

**L'information à remonter dans Homebridge ne doit pas dépasser 64 caractères.**

>**Seule l'application d'Elgato Eve est compatible avec ce type générique. Les équipements utilisant ce type générique n'apparaitront pas dans l'application Maison d'Apple.**

>**Les interactions avec Siri ainsi que les automations ne sont pas possibles avec ce type générique**

>**Il est n'est pas possible de renommer l'accessoire**

### Utilisation avec le plugin Mode #

Cela permet d'afficher l'intitulé du mode jeedom en cours.

![custom-1](../images/custom-1.png)

Dans ce cas, il faut attribuer le type générique "Info/Générique" au nom de commande "Mode".


![custom-2](../images/custom-2.png)

### Utilisation avec le plugin Netatmo (station météo) #

Cela permet d'afficher les informations de type pression, CO2, noise.

![custom-3](../images/custom-3.png)

![custom-4](../images/custom-4.png)


>**Si le champ unité a été indiqué dans jeedom, il remontra dans le type custom.**

![custom-9](../images/custom-9.png)

### Utilisation avec le plugin vigilance méteo #

![custom-7](../images/custom-7.png)

![custom-6](../images/custom-6.png)

Plugins spécifiques
===================

Plugin "Thermostat"
---------------------

>Pour configurer le plugin "Thermostat", il faut se référer à la documentation du plugin à cette adresse : https://jeedom.github.io/plugin-thermostat/fr_FR/.

### Configuration #

Seuls les modes "Chauffer" et "Refroidir" sont à configurer. Il faut attribuer un mode du plugin "Thermostat" à un mode de HomeKit.

![thermostat](../images/thermostat.png)


### Présentation #

![thermostat1](../images/thermostat1.png)

* **A** : Température Cible ou Consigne : Température envoyée au plugin Thermostat (Passe en mode Auto sur Maison et Eve / Mode Aucun sur widget Thermostat)
* **B** : Température Ambiante : Température de référence pour le plugin Thermostat.
* **C** : Commande de modification de la Consigne A : Augmenter ou diminuer la température à l’aide du curseur. Cela aura pour action de modifier également le mode du chauffage E qui passera à AUCUN dans le dashboard Jeedom.
* **D** : Statut du thermostat retourné par le plugin Thermostat : Arrêté (ou Désactivé ou Eteint) (Rond vert dans Maison) / Chauffage (Rond Orange dans Maison) / Climatisation (Rond Bleu dans Maison).

* **E** : Mode Auto (dans Maison ou Eve) : correspond au mode Aucun dans Jeedom où le Plugin Thermostat décide de ce qu'il doit faire en fonction de la température qu'on lui envoie. Ce mode permet de régler une température cible via le curseur C

* **F** : Mode Clim / Refroidir : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* **G** : Mode Chauf / Chauffer : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* **H** : Eteint / Off : permet d'éteindre le thermostat.
* **I** : Verrouillage/Protection Enfants (uniquement dans Eve) : permet de verrouiller le thermostat. (modifié)

### Utilisation #

En cliquant sur "CHAUF" ou "Chauffer", on active le mode du thermostat associé. Idem pour "CLIM" ou "Refroidir".

Plugin "Alarme"
---------------

>La fonctionnalité de l'alarme dans Homebridge est compatible uniquement (pour l'instant) avec le plugin Jeedom "Alarme". Pour configurer le plugin "Alarme", il faut se référer à la documentation du plugin disponible à cette adresse : https://jeedom.github.io/plugin-alarm/fr_FR/.

**Ce mode fonctionne avec l'application d'Apple Maison et celle d'Elgato Eve.**

### Configuration #

Dans HomeKit, la fonction alarme est gérée suivant 4 modes : "Désactivée", "Nuit", "A distance" et "Domicile".

![alarme](../images/alarme.png)
![alarmeeve](../images/alarmeeve.png)

Le mode "Désactivé", inhibe l'ensemble des modes d'alarme du plugin "Alarme". Les actions de l'onglet "Désactivation OK" sont lancées (en fonction du mode de sortie).

![inhibe](../images/inhibe.png)

Les 3 autres modes, sont à définir dans la configuration du plugin Homebridge.


![configalarme](../images/configalarme.png)


>Le "mode Jeedom" correspond aux modes du plugin "Alarme".

![modealarme](../images/modealarme.png)

Il suffit d'affecter le "mode Jeedom" au mode Homebridge choisi.

### Utilisation #

Il suffit de cliquer sur l'icone "Alarme" dans l'application Maison.

![iconealarme](../images/iconealarme.png)

Et de sélectionner le mode.

![selmodealarme](../images/selmodealarme.png)

L'alarme est activée.

Sur le dashboard : 

![alarmeactive](../images/alarmeactive.png)

Sur l'application Maison : 

![alarmeactive2](../images/alarmeactive2.png)

Pour la désactiver, il suffit de sélectionner "Désactivée". Les actions définies dans la partie "Désactivation OK" du plugin "Alarme" vont s'exécuter.

![desactivationok](../images/desactivationok.png)

En cas de déclenchement de l'alarme, une notification apparaît sur le téléphone.

![alarmedeclanchee](../images/alarmedeclanchee.png)
![reinitialiseralarme](../images/reinitialiseralarme.png)

Pour la désarmer, il faut cliquer sur l'icône "Alarme" et sélectionner "Désactivée".


Les actions définies dans la partie "Réinitialisation" du plugin "Alarme" vont s'éxécuter.

![reinitialisation](../images/reinitialisation.png)

Changelog
=========

v1.4.0 (???)
-------------

* Meilleur code de génération pour le QRcode (en php).

* Changement de plusieurs libellés dans la configuration du plugin.

* Nouveau type spécifique homebridge : "Occupation" légèrement différent de "mouvement" dans Maison et dans Eve, il est plus clair pour par exemple afficher une présence (plutot qu'un mouvement).

* Nouveau type spécifique homebridge : "Online" permettant de passer le composant en "Sans réponse" dans Maison s'il a la valeur de 0.

* Nouveau type spécifique homebridge : "Bouton poussoir" qui est en fait un interrupteur mais qui s'éteint tout seul. Cela permet d'associer n'importe quelle commande action de type "autre".

* Support du type générique Action/Générique pour les commandes action de type "autre" seulement. (Comme un Bouton poussoir).

* Support des commandes camera comme bouton pousoir(Haut,Bas,Gauche,Droite,Zoom,DéZoom,Preset) et de l'enregistrement comme un interrupteur.

* Meilleur gestion du type Haut-Parleur (si pas de Mute).

* Gestion automatique pour la serrure TheKeys.

* Séparation des types "Prise" et "Interrupteur".

* Les prises dans Jeedom sont maintenant des vrais prises dans Homebridge.

* Les scénarios Jeedom sont ajoutés en tant qu'interrupteur dans Homebridge (si sélectionné dans la configuration).

* Composant "Pression" modifié pour apparaitre mieux dans Eve.

* Les interrupteur programmables dans homekit font leur apparition.

* Interrupteur Programmable (Multi-Valeur) (Homebridge) : 
 * Il s'agit d'un interrupteur avec une commande de type info qui contiendra plusieurs valeurs en fonction du type de click effectué. ("click", "double_click", "long_click"

* Interrupteur Programmable Binaire (Simple Click) (Homebridge) : 
 * Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un simple click sur le bouton.
* Interrupteur Programmable Binaire (Double Click) (Homebridge) :
 * Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un double click sur le bouton.
* Interrupteur Programmable Binaire (Long   Click) (Homebridge) :
 * Il s'agit d'un interrupteur ou la commande de type info est un binaire et correspond à un long click sur le bouton.

* Compatibilité (Alpha) avec Docker : (toujours aucun support) mais quelques modifications ont été faites pour faciliter l'utilisation du plugin sous Docker officiel Jeedom en mode réseau "Host".

* Affichage des graphiques dans l'application Eve (support Alpha). Fonctionne pour les types suivants :

 * Température (chaque point de donnée est une moyenne des 10min précédentes)
 * Humidité (chaque point de donnée est une moyenne des 10min précédentes)
 * Pression (chaque point de donnée est une moyenne des 10min précédentes)
 * Porte ou Fenêtre 
 * Mouvement 
 * Puissance Electrique (chaque point de donnée est une moyenne des 10min précédentes)

> Il s'agit d'un support Alpha, juste car c'est fun :) Les graphiques ont été développés par ingénierie inversée des composants Elgato Eve et il peut y avoir des incohérences. Les données des graphiques sont les données collectées lorsque le démon Homebridge est démarré, il peut donc manquer certaines informations. Les graphiques sont là à titre informatif. A part les trois premiers qui peuvent être dans le même Périphérique, les autres ne peuvent pas être combinés (il faut coller aux produits Elgato).

v1.3.5 (12-12-2017)
------------------
* Suppression du besoin de sélection de l'utilisateur
* Plus besoin que les actions réfèrent l'état auquel elles sont liées sauf si multi-prises ou multi-relay (on split)
* QRCode pour configurer le bridge (attention, les cameras et plateformes supplémentaires doivent toujours scanner le PIN)
* Plus jolie config
* Afficher une erreur si l'adresse interne est en https
* Mise à jour de Homebridge en 0.4.32 et HAP-Nodejs en 0.4.36

v1.3.4 (29-11-2017)
-------------------
* Réécriture du mode de fonctionnement des thermostats, plus logique :)
* Accessoire supplémentaire pour installer les plugin Homebridge qui ne publient qu'un accessoire
* Mise à jour documentation.
* Corrections de bugs

v1.3.3 (13-11-2017)
-------------------
* Modification documentation
* Gestion des actions Ouvrir et Fermer pour les portes de garages.
* DebugInfo affiche maintenant le log de création d'accessoires (si celui-ci n'est pas encore tronqué)

v1.3.2 (09 et 10 et 12-11-2017)
---------------------
* Fichier fusionné pour la doc
* Autre bug sur Inversion corrigé
* Bug Siri "Ouvre tous les volets du salon" corrigé
* Meilleure réparation et réinstallation
* Documentation corrigée

v1.3.1 (31-10-2017)
---------------
* Bug invertBinary sur présence sans inversion
* Mise à jour documentation
* Compatibilité Serrure Nuki

v1.3 (30-10-2017)
------------------
* Plugin séparé du plugin App Mobile.
* Récupération de la configuration du plugin App Mobile s'il est installé.
* Meilleure réparation et installation plus poussée pour éviter des problèmes divers.
* Documentation complètement réécrite et adaptée par @bphoque, près de 60 pages A4 !!!
* Type "Info/Générique" supporté pour les infos Jeedom de type Numérique, Binaire, Autre dans l'application Eve uniquement (pas encore disponnible dans "Maison").

>Ne pas modifier ce type dans Jeedom pendant que Homebridge fonctionne

* Les types génériques "Info/Choc", "Info/Vent (direction)", "Info/Vent (vitesse)", "Info/Pluie (mm/h)", "Info/Pluie (accumulation)", "Info/Pression", "Info/Son (dB)" sont gérés comme des "Info/Générique" et affichés dans Eve.
* Lumières : Fonctionnement est corrigé pour certains plugins (voir annonce forum)
> Si vous aviez un pont Philips Hue v1, vous avez maintenant accès à HomeKit.
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
 * Status Defectueux (binaire : 0:non/ 1:oui -> peut-être mappé à un binaire représentant par exemple un lien mort chez Z-Wave) .
 * Status Actif (binaire : 0:non/ 1:oui -> peut-etre mappé au status "online" d'une Xiaomi Yeelight par exemple).
* Haut-parleurs, il devrait fonctionner automatiquement avec le plugin Sonos par exemple (à tester), les types sont : 
 * Info/Haut-parleur Mute (binaire)
 * Info/Haut-parleur Volume (pourcentage)
 * Action/Haut-parleur Mute
 * Action/Haut-parleur Unmute
 * Action/Haut-parleur Toggle Mute (soit Toggle soit Mute/Unmute, les deux choix sont possibles séparément)
 * Action/Haut-parleur Volume (typiquement un slider)

>Info/Haut-parleur Mute est obligatoire, c'est étrange mais c'est une obligation coté HomeKit.

v1.2.1
--------
* Bugfix : capteurs Fenêtres
* Bugfix : volets Somfy
* Bugfix : Consommation Electrique qui bug sur composants Z-Wave
* Bugfix : En chargement pour périf avec batterie

v1.2.0
-------
* Realease Stable

v1.1.4
----
* Bugfix : unregister Accessories si on a une erreur
* Update Homebridge & HAP-NodeJS
* Bugfix : Temperature isNaN -> 0
* pré-support Sabotage
* Bugfix : Interdire une valeur Null ou Undefined d'être envoyée à HomeKit

v1.1.2
----
* Support basique Alarme : besoin d'une config coté plugin pour mapper les modes NUIT, ABSENT, PRESENT avec des ALARM_SET_MODE Jeedom

v1.1.1
--------
* Bugfix : Restauration des valeurs en cache au redémarrage
* Bugfix : Bornage des valeurs du détecteur de lumière

v1.1.0
--------
* Support des Plateformes Homebridge en mode expert (Cameras, autre...)
* Documentation code
* Freeze des fonctionnalités, debugging à faire en vue de version stable

v1.0.27
---------
* Simplifié l'ajout/suppression des services
* Commencé à résoudre les problèmes LightBulbs mais pas terminé

v1.0.26
----------
* Gestion pourcentage batterie via le type générique "BATTERY"
* Si < 20% on set un flag "LowBattery" dans Homekit pour afficher dans Maison/Eve/...
* Gestion du "charge en cours" définit sur "non chargeable" pour l'instant car il faut voir comment on gère ca coté Jeedom

v1.0.25 
--------
* Nettoyage du code et simplification
* Meilleure gestion des services en cas de modification de ceux-ci (modification des types génériques)

v1.0.24
----------
* Optimisation (on break les boucles si on a trouvé l'élément, plus rapide sur les grosses installations)

v1.0.23
--------
* si un volet est ouvert à 95% afficher 100% dans Maison (usure mécanique, recalibration)

v1.0.22
--------
* Préparation des Sonnettes en prévision du support dans HomeKit par Apple

v1.0.21
----------
* Corrigé la gestion des Serrures, elles fonctionnent
*!!! si vous utilisez un iPad comme concentrateur HomeKit, pensez a désactiver Siri pour éviter à qqun de crier "siri ouvre la porte d'entrée" par la boite aux lettres (c'est arrivé !) !!!*

v1.0.20
-------
* Logs plus clairs et plus de verbosité sur la création des Characteristics

v1.0.19
---------
* Support pour les portes de garage/barrières, N'utiliser que BARRIER_STATE ou GARAGE_STATE (même traitement, états 255,254,253,252,0) et GB_TOGGLE

v1.0.18
--------
* Combiné les types OPENING et OPENING_WINDOW car c'est un même type dans Homebridge.
* Ajout du Model (nom du type de l'eqLogic) et du Serial Number (id de l'objet + id logique) dans Homebridge.

v1.0.17
--------
* Prise en charge du niveau de debug du plugin App Mobile (il faut sauver le niveau et relancer le demon pour prise en charge)
* Simplification du code (retiré des choses inutiles comme la création d'un serveur http)

v1.0.16
--------
* activation d'un mode debug dans la plateforme, il sera lié au status du plugin.
* Francisation des messages du log, plus de verbosité, plus de clareté et de détails pour encore mieux vous aider en cas de problème.
* Modification des paramètres de composition des UUID, uniquement l'id Jeedom et le nom du périphérique (la pièce Jeedom entrait en considération).

>Cela signifie qu'à l'installation de cette version, vos périphériques dans Maison vont disparaitre pour réapparaitre dans la pièce par défaut (et casser vos scènes et automations).

 * Point positif : vous pouvez maintenant changer de pièce dans Jeedom les périphériques sans les perdre dans Maison. Malheureusement, ils ne changeront pas dans Maison (non-implémenté dans Homebridge).
 * j'ai gardé le nom du périphérique pour l'instant dans l'identifiant car le renommage d'un périphérique dans Jeedom casserait tout dans Maison (pour l'instant) de toute façon.
* Modification du délais d'interrogation-longue pour optimiser les systèmes avec moins de changements d'états.
* Modification du modèle de fonctionnement. Maintenant on prend un état des périphérique au démarrage du plugin et on le met à jour en temps réel à chaque changement dans Jeedom ou Maison. Moins de requêtes sur l'API Jeedom, plus petits temps de réponse dans Maison.
* Ajout d'un ramasse miettes à la fin de l'ajout des périphériques présent dans Jeedom à Homebridge, tout ce qui n'a pas été ajouté/modifié est supprimé d'Homebridge (si vous avez rendu invisible un périf ou supprimé dans Jeedom par exemple).
* Suppression du bouton Regénérer le fichier de configuration : plus besoin, lorsqu'on sauvegarde la configuration, on regénère le fichier automatiquement et on relance le daemon.
* Suppression du bouton Effacer le cache : plus besoin, on gère la suppression individuelle des périphériques. 

>Si vous avez un problème avec un périphérique malgré tout : décochez "Envoyer à Homebridge" | relancez le daemon | décochez "Envoyer à Homebridge" | relancez le daemon : il sera recréé tout proprement (et dans la pièce par défaut de Maison).

* Ajout d'avertissements et de messages d'attention si on s'approche du nombre fatidique de 100 accessoires envoyés dans Homebridge (HomeKit ne supporte pas plus de 100 accessoires).
* Au démarrage du daemon, vérification si avahi-daemon et dbus sont bien lancés, sinon, les démarrer.
* A l'install des dépendances, passer avahi-daemon et dbus à enabled si pas le cas.
* Corrections diverses, simplifications et optimisations.



