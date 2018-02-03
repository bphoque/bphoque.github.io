===== Lumières
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Lumière Etat (Binaire)| NON | Ajout pour les lumières

dont la luminosité ne change pas

lorsqu'elle est éteinte (Yeelight, Ikea, ...)

0 = Eteint 

autre que 0 = Allumé
| Info/Lumière Etat | OUI | Luminosité

0-100 ou 0-99 ou 0-255

(en fonction du max de Action/Lumière Slider)

ou Binaire

0 = Eteint

autre que 0 = Allumé 
| Action/Lumière Slider

(Luminosité)
| OUI | Réf. vers Lumière Etat
| Action/Lumière Bouton On | OUI | Réf. vers Lumière Etat :

- Binaire s'il est présent

- Etat sinon
| Action/Lumière Bouton Off | OUI | Réf. vers Lumière Etat :

- Binaire s'il est présent

- Etat sinon
| Info/Lumière Couleur| NON | Format #RRGGBB
| Action/Lumière Couleur| Si Info/Lumière Couleur | Réf. vers Info/Lumière Couleur
| Info/Lumière Température Couleur| NON | Numérique (Kelvin)

(en fonction du min-max de Action/Lumière Température Couleur)

(Eve Seulement)
| Action/Lumière Température Couleur| Si Info/Lumière Température Couleur | Réf. vers Info/Lumière Température Couleur

(Eve Seulement)
| Action/Lumière Toggle | NON Utilisé | N/A
| Action/Lumière Mode | NON Utilisé | N/A
|===

===== Prises
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Prise Etat | OUI | 0 = Eteint 

1 = Allumé
| Action/Prise Bouton On | OUI | Réf. vers Info/Prise Etat
| Action/Prise Bouton Off | OUI | Réf. vers Info/Prise Etat
| Action/Prise Slider | NON Utilisé | N/A
|===

===== Volets
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Volet Etat | OUI | 0 = Fermé 

>95 = Ouvert
| Action/Volet Bouton Monter | Si Descendre | Réf. vers Info/Volet Etat
| Action/Volet Bouton Descendre | Si Monter | Réf. vers Info/Volet Etat
| Action/Volet Bouton Stop | NON Utilisé | N/A
| Action/Volet Bouton Slider | Si Seul | Réf. vers Info/Volet Etat
|===

===== Volets BSO
Pas encore supportés

===== Chauffage fil pilote
N'existe pas en HomeKit

===== Serrures
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Serrure Etat | OUI | pas 1 = Non Sécurisée 

1 = Sécurisée
| Action/Serrure Bouton Ouvrir | OUI | Réf. vers Info/Serrure Etat
| Action/Serrure Bouton Fermer | OUI | Réf. vers Info/Serrure Etat
|===

===== Sirènes
N'existe pas en HomeKit

===== Thermostats
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Thermostat Etat (BINAIRE) | NON | 0 = Eteint 

1 = Allumé
| Info/Thermostat Etat (HUMAIN) | NON | Générique (Eve Seulement)
| Info/Thermostat Mode | OUI si associé mode homekit | Générique (Eve Seulement)
| Action/Thermostat Mode | NON | Peut être associé mode homekit
| Info/Thermostat Température Extérieure| NON utilisé | N/A
| Info/Thermostat Température Ambiante| NON | -50 -> 100
| Info/Thermostat Consigne| OUI | 10 -> 38
| Action/Thermostat Consigne| OUI | 10 -> 38
| Info/Thermostat Verrouillage| NON | 0 = Non Verrouillé 

1 = Verrouillé
| Action/Thermostat Verrouillage| OUI si Info/Verrouillage | N/A
| Action/Thermostat Déverrouillage| OUI si Info/Verrouillage | N/A
|===

===== Portails ou Garages
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Portail état ouvrant

Info/Garage état ouvrant

(même traitement)| OUI | 0 = Fermé 

252 = Fermeture en cours

253 = Stoppé

254 = Ouverture en cours

255 = Ouvert

(Configurable)
| Action/Portail ou garage bouton toggle | Si seul | Réf. vers Info/Portail état ouvrant

ou

Réf. vers Info/Garage état ouvrant
| Action/Portail ou garage bouton d'ouverture | Si pas Toggle | Réf. vers Info/Portail état ouvrant

ou

Réf. vers Info/Garage état ouvrant
| Action/Portail ou garage bouton de fermeture | Si pas Toggle | Réf. vers Info/Portail état ouvrant

ou

Réf. vers Info/Garage état ouvrant
|===

===== Haut-Parleurs (Eve Seulement)
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Haut-Parleur Mute | OUI | 1 = Pas de son 

0 = Son
| Action/Haut-Parleur Mute | Si pas Toggle | Réf. vers Info/Haut-Parleur Mute
| Action/Haut-Parleur UnMute | Si pas Toggle | Réf. vers Info/Haut-Parleur Mute
| Action/Haut-Parleur Toggle Mute | Si seul | Réf. vers Info/Haut-Parleur Mute
| Info/Haut-Parleur Volume | NON | %
| Action/Haut-Parleur Volume | OUI si Info/HP Volume | Réf. vers Info/Haut-Parleur Volume
|===

===== Generic
[options="header",cols=",^m,"]
|===
| Type générique | Obligatoire | Valeurs possibles 
| Info/Puissance Electrique | NON | Watts
| Info/Consommation Electrique

(cachée)| NON | KWh
| Info/Température | NON | -50->100 °C 
| Info/Luminosité | NON | 0.0001-> 100000 lux
| Info/Présence | NON | 0 = Pas de mouvement

1 = Mouvement
| Info/Batterie| NON | %
| Info/Batterie en charge| NON | 0 = NON

pas 0 = OUI
| Info/Détection de fumée | NON | pas 1 = Pas de fumée détectée

1 = fumée détectée
| Info/Inondation | NON | pas 1 = Pas de fuite détectée

1 = fuite détectée
| Info/Humidité | NON | %
| Info/Porte

Info/Fenêtre

(même traitement)| NON | pas 1 = Contact

1 = Pas de contact
| Info/Sabotage | NON | 1 = Pas de sabotage

0 = Sabotage
| Info/Choc | NON | Générique (Eve Seulement)
| Info/Pression | NON | Générique (Eve Seulement)
| Info/Son (dB) | NON | Générique (Eve Seulement)
| Info/UV | NON | Générique (Eve Seulement)
| Info/Générique | NON | Valeur <64 charactères 

avec Unité indiquée ou pas

(Eve Seulement)
| Action/Générique 

(N'existe pas en HomeKit)| NON | N/A
| Info/Pluie (accumulation) | NON | Générique (Eve Seulement)
| Info/Pluie (mm/h) | NON | Générique (Eve Seulement)
| Info/Vent (direction) | NON | Générique (Eve Seulement)
| Info/Vent (vitesse) | NON | Générique (Eve Seulement)
| Info/Actif | NON | 0 = inactif

1 = actif
| Info/Defectueux | NON | 0 = non

1 = oui
|===

