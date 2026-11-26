---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Créer et gérer des USD animés/","tags":["note_permanente"],"ctime":"2026-11-26T10:51:30.248+01:00","mtime":"2026-11-26T10:54:27.093+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/SOLARIS]]","[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

*Comment écrire un fichier USD animé sur le disque ?* 

USD ROP : il suffit de se mettre en render specific frame range et pas en render current frame 

Le mieux pour être bien propre est que l'usd animé corresponde à un layer usd bien propre, et pas au milieu de plein d'autres choses dans un fichier usd. Cela va nous permettre facilement de swapper les anim en fonction des shots par exemple, en fonction des takes ou pour faire des test etc


#### Stitching per frame

Il y a des cas où on va devoir exporter un fichier usd pour chaque frame (très grosses sim etc) car un fichier unique serait beaucoup trop lourd et trop long à écrire du à la mise en cache de chaque frame avant l'écriture

Parametres pour etre dans ce mode : 
- Valid frame range : render specific frame range
- Chemin d'export : mettre $F3 ou $F4 à la fin 
- Cocher Flash Data After Each Frame : c'est ça qui va séparer en plusieurs fichiers
- Décocher Track Primitive Existence to Set Visibility : sinon solaris va check toute la sequence à chaque fois pour écrire la visibilité


##### Importer de la manière la plus efficace une sequence USD

###### Méthode 1

On va rebuild la sequence usd exportée dans un seul fichier unique pour maximiser la vitesse de chargement 

Etapes : 
- Créer un ROP network
- A l'intérieur créer un usd stitch 
	- input file : la séquence usd
	- output file : le fichier usd stitched

Résultat : le fichier exporté est exactement le même que si on aurait exporté la séquence usd dans un seul fichier de base. ça permet donc d'avoir les bénéfices d'output de la séquence et les bénéfices d'input du fichier unique

Problème : c'est destructif car le fichier stitched ne référence pas la séquence précédente

###### Méthode 2 

Idem mais au lieu d'utiliser un ``Usd stitch``, on va utiliser un `Usd Stitch clips`, une méthode qui est bien moins destructive car le fichier sorti référence la séquence précédente
Parametres : 
- Input file : la sequence
- Template file : le fichier qu'on va écrire
- Clip primitive path : la primitive qui a l'animation
- Clip Set Name : le nom du clip d'anim qu'on veut donner



## Références


> [!example]- Flashcards
> ...




## Liens 




