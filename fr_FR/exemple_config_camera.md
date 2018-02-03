=== Caméra

Homebrige prend en charge les caméras.

image::../images/camera2.png[]

En touchant la capture de la caméra souhaitée, elle s'affiche en plein écran et en live !

image::../images/camera3.png[]

Suivant les configurations matérielles, la qualité de la transmission peut varier. Par exemple, sur un NUC gen7 core i7, c'est quasiment du live ! La latence est très faible.

Celles-ci peuvent afficher une notification lorsqu'un mouvement est détecté par un capteur de présence. Il faut que la caméra et le capteur soient configurés dans la même pièce et que les notifications du capteur soient activées.

image::../images/notif.jpg[]

Les caméras décrites ci-dessous ont été testées. Elles sont donc fonctionnelles dans Homebridge.



L'intégration des caméras se fait via la bouton rouge "Plateforme Homebridge supplémentaire".

image::../images/plateforme-hb.png[]

==== Foscam C1

[source,]
----
{
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
}
----

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

==== Foscam C1 V2

[source,]
----
{
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
}
----

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.


==== Foscam FI9821P 

[source,]
----
      {
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
}
----


Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

==== Foscam FI9803 V3

[source,]
----
{
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
}
----

==== wanscam rtsp HWXXX

[source,]
----
{
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
}
----

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

==== Dlink DCS-5020L

[source,]
----
{
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
----

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

==== Netatmo Welcome

Cette caméra deviendra officielement compatible HomeKit en fin d'année 2017. 
Son intégration dans Homebridge est néanmoins possible.

[source,]
----
{
"platform": "Camera-ffmpeg",
"cameras": [
{
"name": "Camera Name",
"videoConfig": {
"source": "-re -i http://xxx.xxx.xxx.xxx/<Local_Access_Key>/live/files/high/index.m3u8",
"stillImageSource": "-i http://xxx.xxx.xxx.xxx/<Local_Access_Key>/live/snapshot_720.jpg",
"maxStreams": 2,
"maxWidth": 1280,
"maxHeight": 720,
"maxFPS": 30
}
}
]
}
----

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP la caméra et  <Local_Access_Key> -> voir dans le plugin Caméra l'URL de capture /<Local_Access_Key>/live/snapshot_720.jpg.

image::../images/camera.png[]

==== Configurer plusieurs caméras (ou plateformes)

Pour configurer plusieurs caméras, il suffit de mettre une barre | entre les deux configurations.

[source,]
----
{
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
}

----

*Cela est également valable pour toute autre plateforme comme le thermostat NEST par exemple.*
