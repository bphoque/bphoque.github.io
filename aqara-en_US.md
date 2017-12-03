# Xiaomi Aqara Security Home Zigbee

## Création des équipements

Les équipements Aqara sont créés automatiquement

Pour les capteurs Aqara, c'est à leur remontée d'information, donc la fréquence varie en fonction du modèle et ses caractéristiques.

Pour les interrupteurs et boutons Aqara, il peut être nécessaire de les activer pour avoir la création des commandes (un clic par exemple)

## Configuration de la gateway Aqara

Une présentation complète de la gamme est disponible ici : [Article de présentation](https://lunarok-domotique.com/plugins-jeedom/xiaomi-home-jeedom/aqara-lumi-xiaomi-smart-home-security/)

Il est par contre nécessaire de paramétrer la gateway pour activer l'API locale

Pour cela, il faut ajouter la Gateway dans l'application Mi Home et être en China Mainland et Chinese (oui du coup des écrans peuvent contenir beaucoup de caractères illisibles à moins de maitriser le mandarin)

Ensuite cliquer dessus pour la sélectionner, là cliquer sur les "..." et enfin "about"

Là vous avez un numéro de version, cliquez dessus de facon répéter jusqu'à un message (oui en chinois ca aide pas :)) et 2 nouvelles options apparaissent

Choisissez la première option (nouvellement apparue) et activer le bouton switch pour qu'il passe en vert, voilà le mode local est actif et votre gateway est accessible du réseau

Information importante : pour pouvoir envoyer des commandes (prise) vers la gateway, vous devez renseigner son mot de passe sur la page équipement. Ce mot de passe est visible sur la page où l'on active le mode développeur

## Commandes des équipements compatibles

Les équipements actuellement compatibles fournissent les informations :

* Gateway : anneau RGB (avec couleur et intensité, pour éteindre il faut absolument mettre l'intensité à 0), capteur de luminosité, jouer les sons enregistrés (0 à 8, 10 à 13, 20+ correspondent aux sons par défaut dans Mihome, 10000 pour éteindre, 10001 et plus pour les sons personnalisés) [Présentation](https://lunarok-domotique.com/2017/03/mi-smart-gateway-domotique-jeedom/)

* Détecteur de mouvement : commande statut de type binaire activée sur mouvement

* Détecteur d'ouverture : commande statut de type binaire activée sur ouverture

* Capteur température/humidité : commande température, commande humidité

* Bouton Switch : commande click avec pour valeurs click, double_click, long_click_press, long_click_release

* Prise et prise murale : commande statut binaire avec on et off, état d'utilisation et consommation

* Interrupteur mural : commande statut pour chaque interrupteur (click, double_click) et si double une commande qui donne l'appui simultané

* Interrupteur encastré (y compris celui avec neutre) : commande statut binaire avec on et off pour chaque interrupteur

* Cube : commande statut avec pour valeur move, tap_twice, shake_air, alert, flip90, flip180, free_fall, rotate_right, rotate_left et une commande rotate avec la valeur en degré du mouvement [Présentation](https://lunarok-domotique.com/2017/03/aqara-xiaomi-magic-controller-utilisation-dans-jeedom/)

* Détecteur de fumée : commande alarm (binaire), densité (numérique), visibilité (numérique %)

* Détecteur de gaz : commande alarm (binaire), densité (numérique)

* Détecteur d'eau : commande statut (binaire)

* Moteur pour rideau : commande statut (string), position (string) et les commandes actions associées

Remontée des piles : l'API fournie désormais aussi l'état des piles des équipements. Ce qui est retourné c'est le voltage de la pile, avec une fiche technique de l'API indiquant qu'elle sera au max de 3.2V et logiquement à 2.8V la pile n'est plus utilisable. Dans les faits, ce sont des piles 3V, voici donc les informations fournies dans Jeedom :

* Voltage (en commande non visible sur le dash par défaut)

* Batterie (en statut standard, mais aussi en commande non visible) : sa valeur est considérée à 100% si supérieure ou égale à 3V, puis décroit à 0% pour 2.8V

* Le type de pile est indiqué pour chaque équipement sur le récapitulatif