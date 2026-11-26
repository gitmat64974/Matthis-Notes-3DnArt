---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 6/","tags":["note_litteraire","cours","A_traiter"],"ctime":"2026-03-21T20:44:14.006+01:00","mtime":"2025-11-07T17:16:45.661+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours","A_traiter"],"creation date":"2025-11-03"}}
---


# Lundi

## Curves dans Houdini

L’exemple avec un bol : 

node Curve
- Primitive Type : Bezier Curve
- Activer le snapping à la grille (*maintenir touche x dans le viewport*)

![IMG_4046.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4046.jpeg)


Ensuite, touche F pour passer en mode Édition.

Utiliser Ctrl pour ajouter des points, afin de "contraindre" la courbe

Puis rabattre les deux tangentes verticales des points supérieurs :

![IMG_4047.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4047.jpeg)

Même principe pour ajouter 4 points en bas et en plaquer deux au sol : 

![IMG_4048.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4048.jpeg)

Avec le bouton droit sur un ou plusieurs points, l'option Make Corner permet de désolidariser les tangentes

Toujours avec tes points sélectionnés, l'outil Create Round Corners permet de générer des chanfreins propres :

![IMG_4049.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4049.jpeg)


Dans la parameter window de la curve : bake selected rounded corners

(Attention, penser à verrouiller les portions à conserver en ajoutant des points de contrôle au préalable !)

Ces quelques techniques permettent d'obtenir des formes propres et régulières :


![IMG_4050.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4050.jpeg)

(Dernier tip : après le Curve, un Resample permet de contrôler la topologie. Il faut cocher l'option Resample by Polygon Edge, afin de bien conserver les points généres. La distance entre les points (Length) est arbitraire et dépend de l'échelle de ta scène)



## Créer un proxy pour la simulation


> [!Abstract] Noeud ConvexHull
> On utilise principalement le node convexhull

Mais il faut séparer en plusieurs parties l’objet s’il a des zones concaves (des creux)

On split donc avec un wrangle qui vient séparer la mode selon la hauteur, avec le paramètre seuil : 

![IMG_4045.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_4045.jpeg)

On met un group promote ensuite : 
- Convert from points to primitives
- Group Name : base

Ensuite un node split pour effectivement séparer la géométrie

Puis des convexhull sur chacune des sorties du split
Puis un merge pour tout merge
On finit proprement avec un null : OUT_PROXY

---

# Mercredi


Pour prendre en compte la transformation d’un objet dans le objet merge : 
Node object merge -> Transform -> into this object

---
Étapes d’anim pour la simu de la vaisselle : 

1. Anim du ballon
2. Influence sur l’étagère 
3. Anim de la vaisselle en fonction de l’étagère

---

Afficher et modifier les Motion path des objets animés : 

Ctrl R dans le viewport (ou icône juste au dessus du handle tool) et cocher dans la barre qui vient d’apparaître en haut dans le viewport

Faire ctrl + clic sur un intervalle sur le Motion path pour créer une clé et pouvoir la bouger directement 

---

Simulation du ballon, étagère et pièce : 

Rbd configure : définir le comportement physique de l’objet (dur, mou, lourd, léger etc)
Pièce en rigid body 

Mettre le collision padding à 0.002 pour plus de précision

Rbd pack : 
- name : bien nommer (par exemple Rbd_etagere)

Pour rendre le ballon animé dans la simu : 
Cocher dans le Rbd configure : 
- dans bullet data : cocher deforming ou animated (si on est sur la v21) 

