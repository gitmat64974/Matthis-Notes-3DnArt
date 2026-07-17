---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Channels dans MARI/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[MARI]]"],"source":["[[3e cours lighting 3D4]]"],"Projets":null,"tags":["note_permanente"],"creation date":202607171637,"aliases":null}}
---

## La note 

Dans MARI, rien à voir avec la terminologie habituelle, un Channel est une map qu’on exporte
Ils sont identifiés toujours par un node blanc aux bords carrés avec le nom du Channel (diffusecolor, specular roughness, etc). Ce sont ces nodes qui gèrent l’export. 

> [!NOTE]+ Export de Channel : 
> Sélectionner tous les nodes channel 
> Clic droit -> File -> Export selected channel nodes flattened 
> 
> Là on a une fenêtre qui s’ouvre et qui se réouvrira pour chaque channel. 
> -> $ : variable 

*(tif / tiff : exactement la même chose)*

> [!tip]
> Exporter son albédo en 16bit au lieu de 8 si on fait beaucoup de color correct en LookDev 

Voir aussi : [[3_GARDEN/Notes permanentes/Les 2 grands types d’informations en texturing|Les 2 grands types d’informations en texturing]]

En Scalar : cocher dans le node channel : 
- Raw Data
- Scalar Data 

Resize un channel : 
Clic droit sur un channel -> resize

Créer un channel : 

Un va créer un channel de displace en rgb (pourquoi ? => Voir [[3_GARDEN/Notes permanentes/Displace#DispRGB|Displace#DispRGB]])

> [!tip]+ Créer le channel : 
> Clic droit dans le node graph -> channel 
> Paramètres : 
> - Name : DISPrgb
> - Size : 4K 
> - Depth : 32bit 
> - Color Data : 
> 	- Cocher RAW data 
> 	- Ne pas cocher scalar data car il y a 3 couches en rgb et pas une seule en noir et blanc

---

==On utilise un noeud color pour le rgb par contre si c’est scalaire ou rgb scalar on utilise le constant==


## Références


> [!example]- Flashcards
> ...




## Liens 
