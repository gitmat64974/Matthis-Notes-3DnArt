---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Cryptomatte/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[COMPOSITING]]"],"source":["[[Cours compositing Rebuild Shot (insecte 3D2)]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-01","aliases":null}}
---


## La note

![Capture d'écran 2025-04-30 234712.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-30%20234712.png)

Le Cryptomatte est une pass ([[3_GARDEN/Notes permanentes/AOV|AOV]]) qui permet la génération de Mattes à partir de sélections de géométries. Il est calculé dès lors que l’on lance le BatchRender, et qu’un “pxrCryptomatte” (*ou autre selon le moterud de rendu : par exemple unreal -> [[3_GARDEN/Notes permanentes/Render passes unreal|Render passes unreal]]*) est setupé dans la section “Features/SampleFilters” des RenderSettings 

Chaque objet de la scène 3D aura une valeur linéaire float3 (=RGB) unique qui lui sera attribuée. 
Dans NUKE, à l’aide du node “Cryptomatte”, il est possible de faire des sélections de plusieurs de ces valeurs, qui permettront de générer un Matte pour chaque objet ainsi sélectionné : 
1. Connectez le Viewer au node de Cryptomatte; 
2. Affichez les Properties du node de Cryptomatte;
3. CTRL+LMB pour ajouter un élément à la “MatteList”

#### Setup dans Renderman

Créer un nouveau SampleFilter (RightMouseButton - “Append”), puis créer un PxrCryptomatte dans ce nouveau SampleFilter;

![Capture d'écran 2025-05-01 090351.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-01%20090351.png)

En ouvrant le pxrCryptomatte, ajouter le prefix “<layer>” au cas-où vous fassiez un Batch avec des RenderLayers afin d’éviter l’overwriting des frames de Cryptomatte d’un renderLayer sur l’autre;

![Capture d'écran 2025-05-01 090359.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-01%20090359.png)


> [!abstract]
> Pour aller plus loin, il serait même pertinent d’avoir deux Cryptomattes: 
> 
> ![Capture d'écran 2025-05-01 090528.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-01%20090528.png)


## Références 

Comparaison avec un AOV ID : Les Cryptomattes sont **plus précis**, prennent en compte la **présence** et gèrent le **Motion Blur**

## Liens 
