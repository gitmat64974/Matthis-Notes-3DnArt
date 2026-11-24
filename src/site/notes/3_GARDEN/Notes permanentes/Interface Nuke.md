---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Interface Nuke/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.420+01:00","mtime":"2026-04-24T17:43:18.742+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/2e cours compositing esma 3d2a]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


## La note

![Capture d'écran 2024-11-07 104733.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-07%20104733.png)


> [!tip]
> <aside> 💡 Placer son Curseur sur un Panel & Appuyer sur “Espace” permet d’entrer/sortir du mode “FullView” du Panel! </aside>
> 💡Laisser son Curseur sur un élément permet de visualiser le Tooltip (explications sur l’élément)!

#### Viewer

Il y a plusieurs manières de charger un Input:
- **Drag & Drop du fichier dans le Viewer:** — ⚠️ NE FONCTIONNE PAS POUR CHARGER UNE SEQUENCE D’IMAGE EN UN INPUT ⚠️
- **“Tab”, Création d’un node Read & Chargement du fichier via l’Explorateur:**
- **“R” & Chargement du fichier via l’Exporateur (cocher sequence pour importer une séquence d'images)**

mettre une image en chemin relatif : faire un pick directory dans le project window enlever la partie absolue du chemin de l'image

![Pasted image 20241107105328.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107105328.png)

Export : mettre un node write juste avant le viewer, et régler les propriétés du noeud en fonction des besoins. 

Crop render (render région) : on peut appuyer sur ctrl en déformant les côtés du carré pour la déformation du carre de rendu pour qu’il se déforme de manière symétrique
Pixel read crop : ctrl shift

Assigner à un viewer : appuyer sur 1 sur le Node pour l’assigner au viewer 1. Sans node sélectionné, appuyer sur 1 fait basculer la vue sur le viewer 1 (idem pour le 2, 3 etc).

> [!NOTE] raccourcis channels : Se mettre dans le viewport
> - R : channel rouge
> - G : channel vert
> - B : channel bleu
> - A : channel alpha
> - Y : channel luminance

Mettre le projet en aces : 
s dans le node graph → aller sur les project settings, onglet color, ocio config → aces 1.2 

#### Properties

![Pasted image 20241107105617.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107105617.png)

Ctrl clic : réinitialiser une tirette.

S dans le node graph : project window
#### Tool Bar

![Pasted image 20241107111747.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107111747.png)

#### Timeline

![Pasted image 20241107111922.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107111922.png)

Time Line : molette pour zoomer dans la Time Line. Clic molette pour réinitialiser le zoom.


## Références 

## Liens 
