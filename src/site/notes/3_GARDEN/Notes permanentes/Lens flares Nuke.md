---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Lens flares Nuke/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.794+01:00","mtime":"2026-04-24T17:43:18.813+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["#video [This Unreal 5 + Nuke Workflow is Actually Insane - YouTube](https://youtu.be/hFM_jGd46as?si=UgaxkK6rWeXQcR4S)"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-02-16","aliases":null}}
---


## La note 

Exemple de vrai lens flare : 

![Capture d'écran 2025-02-16 224140.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20224140.png)

On a plusieurs artefacts : 
- les beams 
- le wide trait horizontal 
- les artefacts à l'opposé de la light source

Les lens flare se produisent directement dans la lens (l'objectif), donc ils sont toujours à mettre en dernier en compositing. 
Aussi l'effet lens flare ne se produit que quand un light pointe directement vers la caméra

#### Dans Nuke

*A la main on peut prendre des stocks de lens flare, les mettre sur une image plane avec la caméra du rendu, mettre un merge en plus et animer le gain

*Faire automatiquement :*

![Capture d'écran 2025-02-16 225355.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20225355.png)

On prend un seul stock de lens flare qui va nous servir pour tous
Le keyer vient isoler les highlight pour que le convolve et donc le stock de flare n'agisse que sur eux : 

![Capture d'écran 2025-02-16 225443.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20225443.png)

##### Pour aller plus loin

1 : Horizontal lign
Sport flare node (de nukepidia) 
mettre un transform pour l'écraser horizontalement
Combiner ça avec le convolve etc

2: Inverse artefact 
Créer transform node; rotate 180 pour inverser, 
Ajouter keyer et convolve avec une autre texture : 

![Capture d'écran 2025-02-16 230357.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20230357.png)

On peut avoir ça : 
![Capture d'écran 2025-02-16 230426.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20230426.png)

et en scalant la texture et en répétant à plusieurs endroits différents, avec plusieurs couleurs différentes (grade après la texture): 

![Capture d'écran 2025-02-16 230452.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20230452.png)
## Références



## Liens 




