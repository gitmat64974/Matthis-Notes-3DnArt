---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX Autorig builder/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["https://youtube.com/playlist?list=PLXNFA1EysfYlkJDYq1tukRbUW02AkQrkF&si=QgL8x2Z15G_z4i6_"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-28","aliases":null}}
---

## La note 

---


> [!info] Présentation
> Le Autorig builder est un node du système APEX d'houdini permettant de créer automatiquement via drag and drop des systèmes entiers IK FK, switch, rig de pieds, etc et même la création des joints associés si ils ne le sont pas au préalable
> 
> La doc : [Rigging with the Autorig Builder](https://www.sidefx.com/docs/houdini/character/kinefx/autorigbuilder.html)


Par exemple ici on utilise un auto rig builder pour construire un rig seulement à partir d'une geo (sans aucun joint)


![Pasted image 20260117221806.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260117221806.png)

Il suffit de drag and drop les éléments du component catalog directement sur la version grisée à gauche, cela va créer les joints sur la version de gauche et les contrôleurs sur la version de droite (*l'autorig builder affiche 2 versions pour faciliter la construction mais en sortie du node, tout est bien au même endroit dans une seule version*)

On peut éditer les joints sur la version grisée de gauche (translate, rotate, scale) et les controleurs s'updateront sur la version de droite
On peut également bouger les controleurs de la version de droite pour tester et appuyer sur N pour reset les transformations (on peut également cocher skin preview dans le node autorigbuilder : cela va créer un skinning temporaire très léger et vraiment pas terrible qui sert uniquement de preview. Pour le vrai skinning voir [[3_GARDEN/Notes permanentes/Skinning KineFX|Skinning KineFX]])


> [!info] APEX Configure controls : Changer la taille / forme etc des controleurs : 
> On peut ajouter en suivant un node APEX configurecontrols 
> le fonctionnement du node est très intuitif : On ajoute un control config, on sélectionne les controleurs dans le viewport puis on appuie sur le plus à droite pour les ajouter à une modif de config. Puis menu déroulant pour les config
> 
> ![Capture d'écran 2026-09-26 180705.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-26%20180705.png)
> 
> A noter qu'avec ce node on peut aussi définir des limits : limit de translation, d'angle de rotation etc 



---

Si on a déjà des joints : 

![](https://i.imgur.com/3izBNcu.png)


Node APEX Pack character : 
*Il fait l'équivalent du pack folder + autorig component*
Cliquer sur Add FK and Bone deform components




## Références

[[3_GARDEN/MOCs/RIG HOUDINI|RIG HOUDINI]]

Playlist de la chaine YT Houdini : [Intro to Rig Builder - YouTube](https://youtube.com/playlist?list=PLXNFA1EysfYlkJDYq1tukRbUW02AkQrkF&si=QgL8x2Z15G_z4i6_)



> [!example]- Flashcards
> ...




## Liens 




