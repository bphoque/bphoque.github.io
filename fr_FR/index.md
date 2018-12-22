Présentation du plugin mobile 
==============================

Le plugin mobile permet d'interagir avec Jeedom depuis un téléphone mobile ou une tablette via l'application officielle Jeedom. L'application est disponible sur les stores Android et Apple.

![presentation-1](../images/presentation-1.png)

Que peut-on faire avec l'application mobile ?
---------------------------------------------

L'ensemble des interactions offert par jeedom est disponible depuis l'application mobile. Il est possible de piloter son éclairage, régler son chauffage, consulter ses températures, visionner et piloter ses caméras, piloter ses scénarios etc..

![presentation-2](../images/presentation-2.png)

Installation du plugin mobile 
==============================

Le plugin mobile n'est pas intégré par défaut lors de l'installation de jeedom. Il faut disposer d'un compte sur le market de jeedom pour pouvoir l'installer. Les utilisateurs disposant d'un pack Power, Ultimate ou Pro peuvent installer gratuitement le plugin.
Les utilisateurs disposant d'un pack Community, devront s'acquitter de 4€ pour pouvoir bénéficier du plugin. 

Installation depuis le market
------------------------------

Pour installer le plugin mobile, il faut se rendre sur le market depuis l'interface web de jeedom via les menus "Plugin" et "gestion des plugins".

![installation-1](../images/installation-1.png)

Il faut ensuite cliquer sur l'icône du market (chariot vert). Une fois dans le market, il suffit de cliquer sur l'icône "App mobile"

![installation-2](../images/installation-2.png) ![installation-3](../images/installation-3.png)

Pour installer le plugin, il faut cliquer sur installation. 

![installation-4](../images/installation-4.png)

Une fois le plugin installé, il faut le configurer en cliquant sur le bouton "D'accord".

![installation-5](../images/installation-5.png)

Configuration post installation
------------------------------

Après l'installation du plugin, il faut l'activer en cliquant sur "Activer". 

![configuration-p1](../images/configuration-p1.png)

Une fois le plugin activer, il est possible d'activer la fonction "ask" des notifications en cliquant sur la coche associée.

![configuration-p2](../images/configuration-p2.png)

Configuration du plugin mobile 
==============================

Une fois le plugin installé, il faut le configurer via le menu "plugin", "communication" et "app mobile".

![configuration-pm1](../images/configuration-pm1.png)

La première chose à faire est de configurer le plugin. Car si un téléphone est lié au plugin avant la configuration, il va falloir régénérer la configuration (un simple clic sur un bouton suffit).

![configuration-pm2](../images/configuration-pm2.png)

Pour configurer le plugin, il faut cliquer sur "plugin".

![configuration-pm3](../images/configuration-pm3.png)

L'ensemble des plugins installés apparaissent. Certains sont compatibles nativement. Ce sont les plugin spéciaux(c'est à dire qu'il n'y a aucun manipulation à faire). Certains sont compatibles en configurant les types génériques. Enfin, certains (les plugins tiers généralement), sont non testés (cela ne veut pas dire qu'il ne sont pas compatibles, il faudra les configurer via les types génériques).

>Le support ne sera pas assuré sur les plugins non testés.

Les plugins spéciaux
---------------------

Il en existe 6.

* Plugin alarme
* Plugin caméra
* Plugin mode
* Plugin méteo
* Plugin thermostat
* Plugin thermostat-netatmo

![pluginspciaux-ps1](../images/pluginspciaux-ps1.png)

Comme expliquez précédemment, les plugins spéciaux ne nécessitent aucune configuration, ils sont pris en charge nativement par l'app mobile. 

![pluginspciaux-ps2](../images/pluginspciaux-ps2.png)

Les plugins via type générique
------------------------------

La plupart des plugins peuvent être utiliser sur l'app mobile via les types génériques.
Chaque commande (info ou action) doit être associée à un type générique.

L'exemple suivant correspond au plugin Hue.

![typegenerique-tg1](../images/typegenerique-tg1.png)

Sur certain plugin, les types génériques sont configurés automatiquement. Si, ils ne sont pas configurés, il faut les renseigner manuellement.
Il existe deux types de "type générique". L'action et l'info.
L'action pourra être utilisé pour allumer une lumière par exemple alors l'info sera utilisé pour donner une température.

Listes des types "info" : 

![typegenerique-tg2](../images/typegenerique-tg2.png)

Listes des types "actions" :

![typegenerique-tg3](../images/typegenerique-tg3.png)

##Tableaux des templates de l’application #

### Les Lumières #

Image                           | type générique               | Partie Dev plugin            | Description          |
:-----------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![LIGHT](../images/LIGHT_1.jpg) | `Lumière Bouton On`<br/>`Lumière Bouton Off` | `LIGHT_ON`<br/>`LIGHT_OFF`| présence de deux boutons "ON" et "Off" pas de retour d'état. |
![LIGHT](../images/LIGHT_2.jpg) | `Lumière Bouton On`<br/>`Lumière Bouton Off`<br/>`Lumière Etat` | `LIGHT_ON`<br/>`LIGHT_OFF`<br/>`LIGHT_STATE` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off |
![LIGHT](../images/LIGHT_2.jpg) | `Lumière Bouton Toggle`<br/>`Lumière Etat` | `LIGHT_TOGGLE`<br/>`LIGHT_STATE` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off |
![LIGHT](../images/LIGHT_3.jpg) | `Lumière Bouton On`<br/>`Lumière Bouton Off`<br/>`Lumière Etat`<br/>`Lumière Slider` | `LIGHT_ON`<br/>`LIGHT_OFF`<br/>`LIGHT_STATE`<br/>`LIGHT_SLIDER` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off et le slider permet de contrôler l'intensité |
![LIGHT](../images/LIGHT_4.jpg) | `Lumière Bouton On`<br/>`Lumière Bouton Off`<br/>`Lumière Etat`<br/>`Lumière Slider`<br/>`Lumière Couleur (info)`<br/>`Lumière Couleur (action)`<br/>`Lumière Mode` (optionnel, il sert à avoir des mode de lumière,par exemple arc-en-ciel sur les philips Hue) | `LIGHT_ON`<br/>`LIGHT_OFF`<br/>`LIGHT_STATE`<br/>`LIGHT_SLIDER`<br/>`LIGHT_COLOR`<br/>`LIGHT_SET_COLOR`<br/>`LIGHT_MODE` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off et le slider permet de contrôler l'intensité. Dans le cercle la couleur de la lampe est présente et lors d'un cloc dans celui-ci vous pouvez changer la couleur et activer un mode |

### Les Prises #

Image                           | type générique               | Partie Dev plugin            | Description          |
:-----------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![ENERGY](../images/ENERGY_1.jpg) | `Prise Bouton On`<br/>`Prise Bouton Off`| `ENERGY_ON`<br/>`ENERGY_OFF`| présence de deux boutons "ON" et "Off" pas de retour d'état. |
![ENERGY](../images/ENERGY_2.jpg) | `Prise Bouton On`<br/>`Prise Bouton Off`<br/>`Prise Etat` | `ENERGY_ON`<br/>`ENERGY_OFF`<br/>`ENERGY_STATE` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off |
![ENERGY](../images/ENERGY_3.jpg) | `Prise Bouton On`<br/>`Prise Bouton Off`<br/>`Prise Etat`<br/>`Prise Slider` | `ENERGY_ON`<br/>`ENERGY_OFF`<br/>`ENERGY_STATE`<br/>`ENERGY_SLIDER` | Retour d'état présent, le bouton de gauche permet de switcher entre On et Off et le slider permet de contrôler l'intensité |

### Les Volets #

Image                           | type générique               | Partie Dev plugin            | Description          |
:-----------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![FLAP](../images/FLAP_1.jpg)   | `Volet Bouton Monter`<br/>`Volet Bouton Descendre`<br/>`Volet Bouton Stop`<br/>`Volet Etat`(optionnel) | `FLAP_UP`<br/>`FLAP_DOWN`<br/>`FLAP_STOP`<br/>`FLAP_STATE`(optionnel) | Présence de trois boutons "Monter", "Descendre", "Stop", retour d'état optionnel. |
![FLAP](../images/FLAP_2.jpg)   | `Volet Bouton Monter`<br/>`Volet Bouton Descendre`<br/>`Volet Bouton Stop`<br/>`Volet Etat`<br/>`Volet Bouton Slider` | `FLAP_UP`<br/>`FLAP_DOWN`<br/>`FLAP_STOP`<br/>`FLAP_STATE`<br/>`FLAP_SLIDER` | Présence d'un slider, avec un bouton Monter/Descendre en Toggle (avec icône d'état) |

### Inondation #

Image                           | type générique               | Partie Dev plugin            | Description          |
:-----------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![FLOOD](../images/FLOOD.jpg)   | `Innondation`<br/>`Température`(optionnel)<br/>`Humidité`(optionnel)<br/>`Sabotage`(optionnel)|`FLOOD`<br/>`TEMPERATURE`(optionnel)<br/>`HUMIDITY`(optionnel)<br/>`HUMIDITY`(optionnel) | Permet d'avoir son capteur d'inondation complet sur une seule ligne.

### Serrure #

Image                         | type générique               | Partie Dev plugin            | Description          |
:---------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![LOCK](../images/LOCK.jpg)   | `Serrure Etat`<br/>`Serrure Bouton Ouvrir`<br/>`Serrure Bouton Fermer` | `LOCK_STATE`<br/>`LOCK_OPEN`<br/>`LOCK_CLOSE` | Retour d'état présent, le bouton de gauche permet de switcher entre on et off |

### Sirène #

Image                         | type générique               | Partie Dev plugin            | Description          |
:---------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![SIREN](../images/SIREN.jpg)   | `Sirène Etat`<br/>`Sirène Bouton On`<br/>`Sirène Bouton Off` | `SIREN_STATE`<br/>`SIREN_ON`<br/>`SIREN_OFF` | Retour d'état présent, le bouton de gauche permet de switcher entre on et off |

### Fumée #

Image                           | type générique               | Partie Dev plugin            | Description          |
:-----------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![SMOKE](../images/SMOKE.jpg)   | `Fumée`<br/>`Température`(optionnel)|`SMOKE`<br/>`TEMPERATURE`(optionnel) | Permet d'avoir son capteur de fumée complet sur une seule ligne.

### Température #

Image                                       | type générique               | Partie Dev plugin            | Description          |
:-----------------------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![TEMPERATURE](../images/TEMPERATURE.jpg)   | `Température`<br/>`Humidité`(optionnel)|`TEMPERATURE`<br/>`HUMIDITY`(optionnel) | Voir Image.

### Présence #

Image                                 | type générique               | Partie Dev plugin            | Description          |
:-----------------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![PRESENCE](../images/PRESENCE.jpg)   | `Présence`<br/>`Température`(optionnel)<br/>`Luminosité`(optionnel)<br/>`Humidité`(optionnel)<br/>`UV`(optionnel)<br/>`Sabotage`(optionnel)|`PRESENCE`<br/>`TEMPERATURE`(optionnel)<br/>`BRIGHTNESS`(optionnel)<br/>`HUMIDITY`(optionnel)<br/>`UV`(optionnel)<br/>`SABOTAGE`(optionnel) | Voir image.

### Ouvrant #

Image                                       | type générique               | Partie Dev plugin            | Description          |
:-----------------------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![OPENING](../images/OPENING.jpg)   | `Porte / Fenêtre`<br/>`Température`(optionnel)|`OPENING / OPENING_WINDOW`<br/>`TEMPERATURE`(optionnel) | Voir Image (à savoir que vous pouvez choisir entre fenêtre et porte).

### Fil pilote #

Image                               | type générique               | Partie Dev plugin            | Description          |
:---------------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![HEATING](../images/HEATING.jpg)   | `Chauffage fil pilote Bouton ON`<br/>`Chauffage fil pilote bouton OFF`<br/>`Chauffage fil pilote Etat`<br/>`Chauffage fil pilote bouton`(optionnel) | `HEATING_ON`<br/>`HEATING_OFF`<br/>`HEATING_STATE`<br/>`HEATING_OTHER`|Les boutons ON/OFF et Etat permette de créer le bouton tout à gauche du template et les `chauffage fil pilote Bouton`sont là pour rajouter des boutons (5 max)

### Générique Action #

Image                             | type générique               | Partie Dev plugin            | Description          |
:-------------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![ACTION](../images/ACTION.jpg)   | `Action Générique`           | `GENERIC_ACTION`             | Le bouton prend la forme du type de l'action. Par défaut c'est un toggle, si c'est un message alors vous avez une enveloppe, si slider vous avez un slider etc...

### Générique Info #

Image                         | type générique               | Partie Dev plugin            | Description          |
:---------------------------: | :--------------------------- | :--------------------------- | :------------------: |
![INFO](../images/INFO.jpg)   | `Information Générique`           | `GENERIC_INFO`             | Le bouton prend la forme du type de l'info.



