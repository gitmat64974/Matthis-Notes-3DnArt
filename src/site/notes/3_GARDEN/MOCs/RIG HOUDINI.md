---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/RIG HOUDINI/","tags":["MOC"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[RIG]]"],"source":["Houdini doc"],"tags":["MOC"],"creation date":"2026-09-26","aliases":null}}
---


# Cartographie


# Définition


---
*La page de présentation de sidefx : [Rigging \| SideFX](https://www.sidefx.com/products/whats-new-in-h21/rigging/)*


<span style="background:rgba(240, 107, 5, 0.2)">Le rigging dans Houdini se fait via le framework APEX qui est une surcouche de KineFX, le système de rig plus ancien d'houdini</span>


<u>Les 3 informations principales contenues dans APEX sont : </u>
- <font color="#b7dde8">geometrie et ou geometrie skinnée</font>
- Joints
- <font color="#b2a2c7">Controleurs</font>

<u>Il y a plusieurs manières de construire un rig dans APEX :</u> 
On peut construire les joints à la main avec les nodes skeleton puis skinner la geo avec (voir [[3_GARDEN/Notes permanentes/Skinning KineFX|Skinning KineFX]]) pour ensuite "rentrer" dans APEX et construire tout le système de controleurs
On peut aussi "entrer" directement dans APEX avec seulement une geo et créer les joints dans APEX

---

Voilà une manière de rentrer dans APEX avec seulement la geo : 

![Pasted image 20260117211942.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260117211942.png)

- *2 codes couleurs de liaisons de nodes : violet (<font color="#8064a2">rig APEX</font>) et orange (<font color="#f79646">Anim APEX</font>)*

Le pack character vient initialiser le personnage pour "rentrer dans APEX" 
Ensuite ici la création des joints et des controles principaux se fait dans le autorigbuilder via drag and drop de components pré définis (ou définis nous même) -> [[3_GARDEN/Notes permanentes/APEX Autorig builder|APEX Autorig builder]]

Ensuite je viens ici skinner après coup avec le node <font color="#9bbb59">jointcapturebiharmonics</font> et corriger avec le <font color="#9bbb59">jointcapturepaint</font> (voir [[3_GARDEN/Notes permanentes/Skinning KineFX|Skinning KineFX]])

Je repack le personnage puis part en animation avec le node scene animate


# Structure

> [!info]+ Les notes littéraires
> 
>  | File                                                                                                                                                                                                   | creation-date      | tags                                               |
> | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | -------------------------------------------------- |
> | [[3_GARDEN/Notes littéraires/Note litt, playlist vidéos sur APEX Houdini|Note litt, playlist vidéos sur APEX Houdini]]                                                                             | February 08, 2026  | <ul><li>note_litteraire</li><li>en_cours</li></ul> |
> | [[3_GARDEN/Notes littéraires/Exploring facial rigging techniques in KineFXAPEX - Houdini 21 - Carlos Valcárcel|Exploring facial rigging techniques in KineFXAPEX - Houdini 21 - Carlos Valcárcel]] | September 27, 2026 | <ul><li>note_litteraire</li><li>en_cours</li></ul> |
> | [[3_GARDEN/Notes littéraires/RIG & ANIMATE A STYLIZED CRAB - Houdini learning course - APEX|RIG & ANIMATE A STYLIZED CRAB - Houdini learning course - APEX]]                                       | July 20, 2026      | <ul><li>note_litteraire</li></ul>                  |
> 
{ .block-language-dataview}
> 

---
### Kine FX 

[[3_GARDEN/Notes permanentes/KineFX|KineFX]] : le système de joints de Houdini
- [[3_GARDEN/Notes permanentes/Skeleton KineFX|Skeleton KineFX]] : Comment créer facilement et puissamment des skeleton complets avec KineFX
- [[3_GARDEN/Notes permanentes/Skinning KineFX|Skinning KineFX]] : Comment skinner une géo avec son skeleton dans Houdini


[[3_GARDEN/Notes permanentes/KineFX x Simulations|KineFX x Simulations]] : Cas intéressants d'utilisation de KineFX avec des simulations 

---
### APEX

Préparation pour APEX : 
- [[3_GARDEN/Notes permanentes/Préparer skeleton et geo pour APEX|Préparer skeleton et geo pour APEX]]
- [[3_GARDEN/Notes permanentes/APEX Tags|APEX Tags]]

Rigging Apex : 
[[3_GARDEN/Notes permanentes/APEX Autorig builder|APEX Autorig builder]] : La grosse fondation pour faire facilement 80% d'un rig
[[3_GARDEN/Notes permanentes/APEX Autorig component|APEX Autorig component]] : Fonctionnement plus procédural que le autorig builder, ils se configurent un node par composant 
- [[3_GARDEN/Notes permanentes/APEX - Création d'un Look At|APEX - Création d'un Look At]]
- [[3_GARDEN/Notes permanentes/APEX Blendshapes|APEX Blendshapes]] : Comment rigger des blendshapes dans APEX et les config dans KineFX au préalable
- [[3_GARDEN/Notes permanentes/Add Groom to APEX Rig|Add Groom to APEX Rig]]

[[3_GARDEN/Notes permanentes/APEX Graph|APEX Graph]]

[[3_GARDEN/Notes permanentes/APEX Ragdoll|APEX Ragdoll]]

Pour animer ensuite : 
- [[3_GARDEN/Notes permanentes/Animer avec APEX|Animer avec APEX]]
- [[3_GARDEN/Notes permanentes/APEX Ragdoll|APEX Ragdoll]]
- [[3_GARDEN/Notes permanentes/Houdini motion mixer|Houdini motion mixer]]

---

# Appropriation et réflexions 


#### Réflexions


#### Essais





# Ressources




#### Export Rig

<u><font color="#9bbb59">Export de tout le rig :</font></u> 
On peut exporter tout le rig entier, le personnage APEX, la geo etc dans un fichier **bgeo** (ce sera en plus très léger) -> utiliser le node ROP geometry output
-> *Cela ne marchera quand dans Houdini*

<u><font color="#4bacc6">Export Joint + Geo skinnée :</font></u> 
Export en **FBX** -> ROP Fbx output


---

## Références

[[3_GARDEN/Notes permanentes/APEX Autorig builder|APEX Autorig builder]]

Doc : 

[Character - Houdini documentation](https://www.sidefx.com/docs/houdini/character/index.html)
[Rigging a character using rig components](https://www.sidefx.com/docs/houdini/character/kinefx/rigcharacter.html)

Videos / playlists : 

[APEX Rigging - YouTube](https://youtube.com/playlist?list=PLF-ZemGAVNaLOB6IQZg1OBxJ2iq7mMc5-&si=XG_0IeNqzQAYlTt-)

[KineFX 101: Rigging a Face from Scratch - YouTube](https://youtu.be/5b0NjjXnENA?si=E23paaSV8vgyLcRL)

> [!example]- Flashcards
> ...




## Liens 




