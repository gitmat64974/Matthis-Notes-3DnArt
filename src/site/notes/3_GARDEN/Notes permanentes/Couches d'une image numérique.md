---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Couches d'une image numérique/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:26.445+01:00","mtime":"2026-04-24T17:43:18.652+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/1er cours compositing esma 3d2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


## La note

Quelle que soit l'image que l'on trouve sur l'internet, les données numériques sont aujourd'hui toujours structurées de la même manière.  

**Displays**, **Layers** & **Channels** sont des termes couramment utilisés pour définir certains éléments de cette structure. Mais qu'est-ce que c'est exactement ?

> [!multi-column]
> > [!important]+ Display 
> > Le display contient toutes les données de l'image, et donc toutes celles calculées par un moteur de rendu, si on est en 3D. 
> > Les données calculées par le moteur de rendu peuvent être réparties dans plusieurs display, créant ainsi de multiples séquences d'images. 
> > > [!example]-
> > > Par exemple une séquence rendue avec 3 Displays : 
> > > *RDR_CAMShape_beauty.####.exr (0-40)*
> > > *RDR_CAMShape_utils.####.exr (0-40)*
> > > *RDR_CAMShape_cryptomatte_PTH.####.exr (0-40)*
> 
> > [!success]+ Layer
> > Un Display est composé **d'une ou de plusieurs** couches (layer). Une **couche** est la sous-structure d'un display. 
> > Elles sont aussi communément appelées **» [[3_GARDEN/Notes permanentes/AOV\|AOV]]** “ (= Arbitrary Output Values) ou **” Passes** » dans les moteurs de rendu.
> > 
> > Cela peut être de la couleur, ou des informations utiles de la scène 3D dont le Département Compositing aura besoin. 
> > 
> > <font color="#9bbb59">Un Display peut avoir n'importe quel nombre de Calques. Mais à un coût : plus il y a de Calques, plus la taille du fichier de chaque .EXR est importante.</font>
> 
> > [!NOTE]+ Channel
> > Un layer est composée d'un ou plusieurs canaux (channel). Un channel est la sous-structure d'une couche, et contient des données dans chaque pixel de chaque image.
> > 
> > > [!example]-
> > > exemple : Le calque RGBA est composé de 4 canaux: 
> > > - <font color="#c00000">R - Red</font> - Détermine la quantité de rouge par pixel 
> > > - <font color="#00b050">G - Green</font>- Détermine la quantité de vert par pixel  
> > > - <font color="#00b0f0">B - Bleu</font> - Détermine la quantité de bleu par pixel 
> > > - A - Alpha - Détermine la valeur de l'opacité par pixel
> > 
> > Si un calque a **plus de 4 canaux**, NUKE commencera à rencontrer des problèmes de performance lors de la lecture des écrans
> 

| ![Pasted image 20241104202149.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241104202149.png) | ![rdr_RAW.webp](/img/user/Pi%C3%A8ces%20jointes/rdr_RAW.webp)                    |
| ------------------------------------ | ------------------------------------ |
| ![rdrUtils_RAW.webp](/img/user/Pi%C3%A8ces%20jointes/rdrUtils_RAW.webp)               | ![Pasted image 20241104202216.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241104202216.png) |

## Références 

- [[3_GARDEN/Notes permanentes/OpenEXR\|OpenEXR]]
## Liens 
