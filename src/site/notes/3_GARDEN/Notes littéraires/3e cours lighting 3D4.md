---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/3e cours lighting 3D4/","tags":["note_litteraire","cours","A_traiter"],"dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[MARI]]"],"source":["[[Cours de lighting rendu ESMA]]"],"Projets":null,"tags":["note_litteraire","cours","A_traiter"],"creation date":"2025-10-10"}}
---


### Decimate


Dans Zbrush -> décimation master : Enlève tous les vertex qui ne servent en rien à la définition de la surface. On peut keep UVs. 

Cela enlève énormément de polys tout en gardant les niveaux de détail grâce à une topo optimisée en triangle, très bonne pour la retopo 

Dans Zbrush : 
1. Keep UVs
2. Pre-Process Current (le subtool actif) : vient sauvegarder les vertex sur le disque temporairement 
3. Choisir le pourcentage de polys à garder / nb de poly 
4. Decimate current


### Channels dans MARI

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

### Node Paint

Appuyer sur P dans le node graph
Bien choisir les paramètres en fonction de la situation

Par exemple pour un masque : 
- Color : noir
- Cocher Raw data et scalar data 

Color : 
- 8 bits
- Colorspace : ACEScg 
- Ne pas cocher Raw Data et Scalar Data

RGB Scalar : 
- 32 bits
- Cocher Raw Data
- Décocher Scalar Data

Paramètre color : 
- Noir : masque
- Transparent : projection 


> [!abstract]+ Node Merge
> Base : correspond au B dans le merge de nuke
> Over : correspond au A dans le merge du nuke

---

Pour la pixel depth : 
[[3_GARDEN/Notes permanentes/Pixel#Pixel Depth|Pixel#Pixel Depth]] 

---

Fichiers .mng : Fichiers très légers
Fichiers contenant des nodes : 
Export des nodes : Clic droit dans le node graph -> file -> export nodes

---

### Projection dans MARI


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Projection dans Mari/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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




</div></div>

