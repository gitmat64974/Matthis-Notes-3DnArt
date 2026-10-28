---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Pipeline USD/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[USD]]","[[LIGHTING]]","[[3D]]","[[Pipeline de production en animation]]"],"source":["[[COURS ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-10-28","aliases":null}}
---

## La note 

#### Version simplifiée : 

![Capture d'écran 2026-10-28 092810.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-28%20092810.png)

#### En détail : 


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/excalidraw/USD Pipeline Schema/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Modé 
Publish Modé 
FBX / USD 
Texturing 
Lookdev asset 
Rigging 
PBH Asset 
USD 
PBH Rig 
MA 
PBH Modules 
USD 
Assemblage modules 
Master Layout 
PBH Lighting master 
USD 
PBH Layout master 
USD 
Hipnc 
Multishot Layout 
Hipnc 
PBH Layout shot 
USD 
PBH Cams Layout 
USD 
Anim Shot 
FX 
PBH Anim 
USD 
PBH Layout anim edit 
USD 
Anim shot précisions : 

On importe en dur les caméras, et on garde uniquement celle liée à notre shot. On importe en référence le layout master, et on importe en référence le rig. On fait l'animation des personnages et des props et si on veut déplacer les items ou modules autour des personnages, on crée un layer usd, et on modifie ce dernier. Ainsi, on pourra exporter uniquement les modifications apportées à notre fichier. C'est le fichier layout edit  
CFX 
PBH CFX 
USD 
PBH cam shot 
USD 
PBH FX 
USD 
Multishot confo 
Hipnc 
PBH Shot confo 
USD 
Multishot Lighting 
Hipnc 
Publish Input Compositing 
EXR 
Compositing 
Publish Input 
Montage 
EXR 
Modules précisions : 

On peut prendre des assets et les regrouper pour créer des assembly d'asset

exemple : Une étagère 
Master Layout :

Dans le master layout, on fait le setdressing d'un décor général : le master comme celui d'une séquence par exemple, donc on pose les lookdev des items, modules et enviros pour créer un master layout. On place ensuite les caméras de tous les shots qui vont se dérouler dans ce master layout. Et finalement on fait le lighting de ce layout master, un lighting général qui a pour but d'être ajusté plus tard au shot. 
Multi shot layout : 

On prend le master layout et on modifie le layout et les cams selon les besoins pour chaque shot 
ASSET 
CREATION 
SEQUENCE 
CREATION 
SHOT
CREATION 
POST
PRODUCTION 


</div></div>



## Références


> [!example]- Flashcards
> ...




## Liens 




