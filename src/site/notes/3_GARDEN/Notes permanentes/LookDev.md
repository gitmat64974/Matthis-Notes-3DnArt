---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/LookDev/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.908+01:00","mtime":"2026-09-30T23:05:57.061+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-11-26","aliases":null,"banner":"https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia.caveacademy.com%2Fwp-content%2Fuploads%2F2023%2F06%2F18153809%2FCAVE_HTUTSLDK1003_v001_r001.jpg&f=1&nofb=1&ipt=262fd6d6761f410664c80ab90321c250171144d9eec1b844dffa749b97e95c77"}}
---


## La note

C’est la gestion du matériau avec les lumières, l’objet est entouré d’un lightRig classique et de 4 sphères, les lookdev balls.

1. Chrome : Diff 0 spec  face 1 - edge 1  rough : 0
2. Grey (ou neutre) Diff 0.180  Valeur de luminance doit être à peu près à 18%. c’est un gris à 50% en linear
3. White Diff 0.840  Aucune blancheur réel ne dépasse 80% de la luminosité, excepté la neige.
4. Black Diff  0.004  Le noir pur n’est pas courant, et seul des objet industriel sont aussi sombre.

*Les LookDev balls doivent être environ au même niveau que l’asset (même distance cam, le plus proche possible)*


![Calibrage_de_lumiere_LookdevBalls.png](/img/user/Pi%C3%A8ces%20jointes/Calibrage_de_lumiere_LookdevBalls.png)


Pour le process on fait cet environnement neutre d’abord puis ensuite, on prendra l’HDR du shot pour la mettre dans le LookDev et voir la réaction de l’objet à cet HDR


## Références 


Voir les ressources Lookdev sur le HUB du prof 


## Liens 

