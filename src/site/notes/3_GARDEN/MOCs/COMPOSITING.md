---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/COMPOSITING/","tags":["MOC"],"ctime":"2026-04-25T23:16:42.405+02:00","mtime":"2026-04-06T00:00:58.000+02:00","dg-note-properties":{"aliases":["Compositing"],"banner":"https://images.unsplash.com/photo-1597423244036-ef5020e83f3c?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D","tags":["MOC"]}}
---

---

# Définition

![_- visual selection (3).png](/img/user/Pi%C3%A8ces%20jointes/_-%20visual%20selection%20(3).png)

==**Le Digital Compositing (en français: ‘Composition’) est un ensemble de méthodes numériques consistant à mélanger plusieurs sources d’images pour produire un plan unique -(Wiki)**== 

Cela peut consister par exemple à: 
- Remplacer un nuage par un autre dans un ciel afin de correspondre à ceux présents dans les shots précédents, tournés quelques jours auparavant dans des conditions météorologiques différentes; 
- Faire du Keying pour ajouter un acteur sur la Lune; 
- La destruction totale d’une ville par une armée d’aliens provenant d’une autre galaxie; 

![Pasted image 20241104200110.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241104200110.png)

Le Compositing est applicable à toute production quelle que soit son genre; de la comédie au drame, en passant par le film catastrophe, la science-fiction ou l’horreur. Il y aura toujours quelque-chose à ajouter dans l’image afin d’en raconter l’histoire.

le Compositing permet: 
- De produire certains effets qui ne peuvent être réalisés par le moteur de rendu uniquement; 
- De produire tous les effets qui ne peuvent être intégrés au budget de production, qui coûteraient trop cher à réaliser dans les départements en amont; 
- De gagner en flexibilité sur le visuel final. 

Exemple avec le film les éternels : [Eternals | VFX Breakdown Reel | Scanline VFX](https://vimeo.com/670018679)

Nuke vs After effects : Nuke est bien plus puissant, c'est lui qui est utilisé dans toutes les superproductions. After effects est tout de même bon pour les motion graphics. 

> [!tip]+ Nodes vs Layers : 
> 
> | Advantages of Nodes                                                                            | Limitations of Layers                                                                             |
> | :--------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
> | **Flexibility**: Insert effects anywhere, any time without disrupting your entire composition. | **Inflexibility**: Inserting new effects often requires redoing work or re-arranging many layers. |
> | **Clarity**: See your entire workflow at a glance, like a flowchart of your shot.              | **Visibility Issues**: It's easy to lose track of what's happening in a stack of many layers.     |
> | **Reusability**: Easily copy and paste parts of your comp across multiple shots.               | **Repetition**: Applying the same effects across multiple shots is time-consuming.                |
> 
> 

# Ressources

La doc super de foundry : [Nuke User Guides](https://learn.foundry.com/nuke/content/user_guide.html)

Le site notion du prof : (*Une très grande partie des notes de comp de ce site sont basées dessus*) [louasrongeart.notion.site](https://loucasrongeart.notion.site/12e3aa0145a64580bf8fb41189c8bc3e?v=875b0b623e804a738220355d1c9f7a46)

Installer Nuke : [NUKE—INTRO-001— NUKE INSTALLATION](https://loucasrongeart.notion.site/NUKE-INTRO-001-NUKE-INSTALLATION-cb175e3fc68d44088777ecd4857c233d) 

YT : 
- [VFX SHOWDOWN](https://www.youtube.com/@VFXSHOWDOWN/playlists)
- Playlist complète : 
	- [CG Compositing Series](https://www.youtube.com/playlist?list=PLt2Nu4KGXJ2gjJn2eaF08UZdYUFp8xfwU)
	- [Nuke Compositing](https://youtube.com/playlist?list=PLw7TZXbFAyfdHFSt5KTZf5zbMNavdYBVQ&si=yw3VWSjenmxeOwXz)
- [VFX and Filmmaking](https://youtube.com/playlist?list=PLXUYqoxqIDrWIeH8STzqoOq_J_AANMNVU&si=ygnfs14I1JXX4kVW)
- [Advanced Compositing for VFX | Week 1 Lessons for Nuke Artists - YouTube](https://youtu.be/zD6ZGhfSFdI?si=VlNu3G1j6TU1UPY5)

Stocks shots : 
- [Vecteezy](https://www.vecteezy.com/)

---
# MOC

- [[3_GARDEN/Notes permanentes/Histoire des VFX\|Histoire des VFX]]

#### Les bases : 
- [[3_GARDEN/Notes permanentes/Pixel\|Pixel]]
- [[3_GARDEN/Notes permanentes/Couches d'une image numérique\|Couches d'une image numérique]]
- [[3_GARDEN/Notes permanentes/Nuke\|Nuke]]
	- [[3_GARDEN/Notes permanentes/Interface Nuke\|Interface Nuke]]
	- [[3_GARDEN/Notes permanentes/Raccourcis Nuke\|Raccourcis Nuke]]
	- [[3_GARDEN/Notes permanentes/Configurer l'UI Nuke comme à l'ESMA\|Configurer l'UI Nuke comme à l'ESMA]]
	- [[3_GARDEN/Notes permanentes/Node graph Nuke\|Node graph Nuke]]

#### Matte et Roto :
- [[3_GARDEN/Notes permanentes/Matte\|Matte]]
- [[3_GARDEN/Notes permanentes/Rotoscopie\|Rotoscopie]]

#### Comp 2.5D et Camera mapping

- [[3_GARDEN/Notes permanentes/2.5D Compositing\|2.5D Compositing]]
- [[3_GARDEN/Notes permanentes/Camera mapping\|Camera mapping]]

#### CG Render Setup (AOVs, renderlayers etc)

- [[3_GARDEN/Notes permanentes/OpenEXR\|OpenEXR]]
- [[3_GARDEN/Notes permanentes/AOV\|AOV]]
	- [[3_GARDEN/Notes permanentes/Shader Lobes\|Shader Lobes]]
	- [[3_GARDEN/Notes permanentes/AOVs Utilitaires\|AOVs Utilitaires]]
	- [[3_GARDEN/Notes permanentes/Cryptomatte\|Cryptomatte]]
- [[3_GARDEN/Notes permanentes/LPE\|LPE]] 

- [[3_GARDEN/Notes permanentes/Render Layers\|Render Layers]]
	- [[3_GARDEN/Notes permanentes/Render passes unreal\|Render passes unreal]]

-> Voir aussi la partie Rendering du [[3_GARDEN/MOCs/LIGHTING\|3_GARDEN/MOCs/LIGHTING]]
#### Rebuild

Ensuite dans NUKE : [[3_GARDEN/Notes permanentes/Rebuild NUKE\|Rebuild NUKE]]

Avec entres autres : 
- [[3_GARDEN/Notes permanentes/Defocus Nuke\|Defocus Nuke]]
- [[3_GARDEN/Notes permanentes/Lens flares Nuke\|Lens flares Nuke]] 

- [[3_GARDEN/Notes permanentes/Glow\|Glow]] 
- [[3_GARDEN/Notes permanentes/Stockshots en comp\|Stockshots en comp]] 
- [[3_GARDEN/Notes permanentes/Fog CG\|Fog CG]] 

- [[3_GARDEN/Notes permanentes/Balance des blancs\|Balance des blancs]] 

#### Autres

[[3_GARDEN/Notes permanentes/Creation de Gizmo Nuke\|Creation de Gizmo Nuke]]

---

*Voir aussi*
- *[[3_GARDEN/Notes permanentes/Gamma\|Gamma]]*

