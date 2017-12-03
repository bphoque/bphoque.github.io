# Yeelight Wifi

## Création des équipements

Un bouton de scan permet de créer automatiquement toutes les lampes répondant au protocole Yeelight disponible sur le réseau (uniquement celles qui n'existent pas déjà dans Jeedom biensûr)

## Configuration des lampes Yeelight

Une présentation complète de la gamme est disponible ici : [Article de présentation](https://lunarok-domotique.com/plugins-jeedom/xiaomi-home-jeedom/yeelight-xiaomi-wifi-lamp/)

Dans l'application Yeelight vous devez activer l'option développeur également

C'est un switch a activé dans les options de chaque ampoule/bandeau

## Commandes des équipements compatibles

Les lampes compatibles proposent les commandes suivantes par défaut : on / off / toggle / luminosité / enchainement

Certaines lampes ajoutent des commandes :

* Yeelight Blanc : pas d'autres commandes

* Desklamp : couleur de blanc

* Yeelight RGB : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Bandeau RGB : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Lampe de Chevet (socle doré) : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Yeelight Ceiling : couleur blanc, mode jour, mode nuit

### Commande enchainement des Yeelight

Pour les Yeelight, une commande spéciale est créée qui a vocation à être utilisée en scénario seulement car on doit envoyer un contenu précis à la commande.

C'est une commande message qui doit avoir par exemple :

3 recover rgb,255,0,0,500,100-wait,400-rgb,255,255,0,500,100

* 3 : c'est un chiffre représentant le nombre de fois que la suite d'effets doit être appliquée avant de s'arrêter (0 veut dire illimité)

* recover : une des 3 options possible (recover = retour à l'état avant effet, off = s'eteint ensuite, stay = reste au statut de fin de boucle)

* le troisième élément est la suite des états avec leur transition, il y en a 4 possible (attention à bien ne pas mettre d'espaces)

Les 4 possibles :

* hsv : paramètres (hue,saturation,duration=300,brightness=100)

* rgb : paramètres (red,green,blue,duration=300,brightness=100)

* temp : paramètres (degrees,duration=300,brightness=100)

* wait(duration=300)

Il faut bien entrer l'enchainement avec des - entre chaque effet. Et pour un enchainement il doit y avoir son nom et tous les paramètres séparés par des virgules