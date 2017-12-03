# Xiaomi Home

## Présentation

Une présentation complète du plugin est disponible ici : [Article de présentation](https://lunarok-domotique.com/plugins-jeedom/xiaomi-home/)

Le plugin implémente 3 protocoles Xiaomi ce qui donne un éventail conséquent de matériel supporté

### Xiaomi Aqara Home Gateway

La Xiaomi Aquara Home Gateway permet d'utiliser différents capteurs Zigbee Xiaomi.

[Voir la doc sur les périphériques Aqara](aqara.html)

### Yeelight Wifi

Le plugin permet également d'utiliser les lampes qui supportent le protocole Yeelight Wifi.

[Voir la doc sur les périphériques Yeelight](yeelight.html)

### Appliances Wifi

Il existe aussi un protocole Xiaomi commun à beaucoup de périphériques Wifi. Ce protocole est implémenté dans le plugin et rend compatible les appliances l'utilisant (Vacuum, Prises, Purificateurs ...)

[Voir la doc sur les périphériques Wifi](wifi.html)

### Bluetooth ?

Les produits Xiaomi Bluetooth ne sont pas pris en charge par ce plugin. Néanmoins vous pouvez en retrouver une bonne partie dans le plugin BLEA (Bluetooth Advertisment), dont :

* bracelets Miband (au moins pour la présence sur le 2)

* lampe de chevet

* balance (1ère génération avec le poids seulement)

## FAQ

>Quel type de gateway Xiaomi est supporté ?

La "Aqara" avec anneau led pour le Zigbee qu'il faut bien paramétrer en mode développeur pour y accéder localement, pour cela il faut un firmware au moins en 1.4


>Je n'arrive pas à passer ma gateway Aqara en mode local ?

Il faut également bien utilisé Mi Home en anglais et sur China Mainland si on rencontre des problèmes d'inclusion

>Une information de mes capteurs ne remonte pas ?

Si vous n'avez pas de commande équivalente créée dans Jeedom, ca peut être que l'API n'expose pas cette information. Il faut attendre peut être une mise à jour du firmware

Toute les informations ne remontent pas à la même fréquence, par exemple la batterie peut n'être envoyée que quotidiennement

>Je n'arrive pas à controler mes capteurs Aqara (couleur et son gateway, prise ...) ?

Vous devez bien saisir la clef de la gateway visible dans Mi Home sur l'équipement gateway dans Jeedom

>Mes commandes sur capteurs Aqara qui fonctionnaient ne fonctionnent plus ?

Vérifier si la clef à changer dans Mi Home, cela peut se produire après une montée de firmware par exemple

>Jeedom ne parvient pas à découvrir la gateway et les capteurs ?

Vérifier que votre routeur laisse bien passer les paquets broadcast du réseau Wifi vers l'ethernet par exemple

>Jeedom ne parvient pas à utiliser ma gateway créer manuellement ?

Il ne faut pas créer les gateway/capteurs à la main, ils sont automatiquement découverts, si ce n'est pas le cas il y a autre chose et il faut trouver la raison

>Combien de capteurs au maximum sur une Gateway Aquara ?

Les remontées utilisateurs indiquent 31 capteurs + la Gateway. Au delà il faut supprimer l'appairage d'un capteur pour en remettre un. Le plugin supporte plusieurs gateways.

>Quelles ampoules sont supportées ?

Les Yeelight Wifi uniquement (la liste est fournie dans la documentation)

>Certaines Yeelight ne remontent pas ?

Les Yeelight Wifi doivent toutes être paramétrées avec le mode développeur pour être joignable sur le réseau local.
Pour ceci, il vous faut installer l'application Yeelight (et non pas seulement Mi Home), renseigner votre login /mot de passe, aller dans chaque équipement, accéder aux settings via les ' ... ' et activer le 'Developer Mode'.
Note : Il n'est pas nécessaire de changer la langue de l'application.

>Je n'arrive pas à controler une appliance, le robot par exemple ?

Vérifier que vous avez bien obtenu le token, pour les appliances qui ne le fournissent pas, des tutos sont présents dans la doc.

## Changelog

[Voir la page dédiée](changelog.md)
