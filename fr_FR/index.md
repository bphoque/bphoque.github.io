# Présentation HomeBridge #

*Le plugin Homebridge* est un demon qui permet d’interagir avec un système domotique via l’assistant vocal Siri sous iOS. Le HomeKit a été introduit depuis iOS 8, mais est véritablement opérationnel depuis iOS 10 via l’application Maison. 

![homekit-logo](../images/homekit-logo.jpg)

Le plugin Homebridge de Jeedom permet donc d’exposer des équipements Jeedom qui seront vus comme des accessoires compatibles au protocole *HomeKit*.

>Homebridge n'est pas officiellement supporté par Apple. A tout moment Apple peut bloquer ce protocole.

## Que peut-on faire avec HomeBridge ? #

Homebridge peut s'utiliser avec une application compatible HomeKit ou avec l'assistant vocal Siri.

Depuis iOS 10, l'application Maison (inclue par défaut avec iOS) permet le pilotage d'équipements compatibles HomeKit. 

![cuisine-homekit](../images/cuisine-homekit.jpg)

Les équipements peuvent être classés par pièce.

![piece-homekit](../images/piece-homekit.jpg)

Beaucoup d'accessoires sont pris en charge.

![garage-homekit](../images/garage-homekit.png)

Siri peut aussi interagir. Il répond aux questions : 

![siri-01](../images/siri-01.jpg)

Siri peut également faire des actions : 

![siri-02](../images/siri-02.jpg)

HomeKit a l'avantage d'être utilisable à l'extérieur du domicile. Seule condition: il faut disposer d'un concentrateur. 
L'iPad et l'AppleTV (et bientôt le HomePod) peuvent servir de concentrateur. Pour cela, ils doivent être connectés au même compte iCloud.



>HomeKit est le nom officiel du protocole développé par Apple. Homebridge est son équivalent Open Source développé par nfarina. Ce dernier a étendu le projet HAP-NodeJS qui est le moteur d'Homebridge.

## Type d'accessoire compatible avec HomeKit (on les ajoutera peu à peu à HomeBridge)

![cchb](../images/acchb.jpg)
