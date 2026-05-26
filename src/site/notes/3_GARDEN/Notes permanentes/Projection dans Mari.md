---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Projection dans Mari/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[SHADING TEXTURING]]","[[MARI]]"],"source":["[[3e cours lighting 3D4]]","[[4e cours lighting 3D4]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-06","aliases":null}}
---

## La note 


-> Ressources maps de texturing xyz

On va donc utiliser 3 maps correspondant aux 3 couches RGB : 

R: Displace
G : Tertiary
B : Micro

> [!NOTE]+ Préparer les textures de *texturing xyz* pour MARI
> Ouvrir les psd -> enregistrer en tiff et bien cocher le profil ICC pour garder les valeurs de midpoint 
> Ensuite dans NUKE : 
> 
> On fait en sorte de tout merge pour répartir les 3 maps selon les couches RGB : 
> 
> ![IMG_1291.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1291.png)
> 
> Bien attention à avoir dans cet ordre (de droite à gauche sur la capture d’écran): 
> 
> R: Displace
> G : Tertiary
> B : Micro
> 
> On met l’input A rouge dans l’output vert de l’ouput du premier shuffle
> Dans le deuxième shuffle : input À rouge dans l’output bleu 
> 
> Ensuite on met 3 crop avec lesquels on va séparer les 3 morceaux de la texture pour éviter d’avoir une seule texture énorme à projeter dans MARI ce qui risque d’être compliqué pour les performances. 

Importer dans MARI : 

Image manager -> drag and drop une des textures 
- Bien cocher Raw data

Ensuite drag and drop la texture dans le viewport 

**Shift H / Ctrl shift H** : hide / unhide la sélection (UV island, géos, etc)

On peut copier coller des Informations d’un UV Time sur un autre (ctrl C / ctrl V): c’est comme ça qu’on fait la symétrie par exemple

Sélectionner un UV Tile -> Fill : permet de « flood » avec une couleur

#### Paint buffer

Paramètres du paint buffer : 

![IMG_1321.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1321.png)

P : Sortir de la projection
U : Entrer dans la projection

> [!abstract]+ Utilisation du Paint buffer et raccourcis : 
> #### Navigation
> Ctrl : rotate
> Shift : translate 
> Ctrl + shift : agrandit / réduit
>  
> - - -
> #### Baking
> Bake : B : projeter les détails 
Ctrl + shift + C : Clear le paint buffer
Ctrl + shift + B : Bake and clear 
> 



## Références


> [!info]- Comment charger des nouvelles versions de la geo
> Dans la toolbar à droite : 
> -> Objets -> Venir charger des nouvelles versions de la géométrie (on espère que ça casse pas tout mais si les UVs layout ont changés, ça casse tout …)
> - Clic droit sur l’objet -> add version 
> - Choisir la version si jamais dans l’onglet geometry (toujours dans objet)


> [!example]- Flashcards
> ...




## Liens 




