---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 2/","tags":["note_litteraire","cours","A_traiter"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours","A_traiter"],"creation date":"2025-09-29"}}
---



CAM : 

Se mettre en vue cam : 
- Cadenas dans la toolbar à gauche dans le viewport 
- Sélectionner la caméra

-> En faisant ça changer la vue change les valeurs de trans et rot

Alt clic sur le nom ou le paramètre pour mettre une clé d’anim

---

Animation editor : 
Shift + Clic sur un paramètre


---

Voronoi : [[3_GARDEN/Notes permanentes/Voronoi|Voronoi]]

---

Créer des rochers : 
*Mettre capture écran du graph*

Isooffset : transformer une geo en volume
	Lui donner un nom pour le reconnaître ensuite (dans les parameters)

Scatter : node qui va scatter des points sur La geo donnée 

Ensuite Voronoi fracture
	Mettre un remesh juste après pour éviter les ngons et uniformiser

Ensuite Exploded view pour éloigner les uns des autres les blocs cassés

-

Node For each Named attribute : 

A noter par rapport à la doc. Après le bound ce n’est pas un transform mais un edit (le transform marche aussi enft)

Dans le Édit il faut sélectionner tous les points du bas de la box

---

Déplier les UVs : 

Ajouter à la doc : 
node UV Fuse après le UVflatten pour souder les trous dans les UVs
Mettre un UV Layout


---

Export pour texturer (à compléter avec le cours) : 
*Capture d’écran*

On met une grid 

On copy parameter le nombre de point dans le scatter puis racine carré paste relative référence dans les rows et columns : 

Node delete juste après pour enlever les faces : 
Mettre un * dans le group 
Cocher keep points

sqrt(paste relative reference)

Ensuite node delete : 

Explication du code du wrangle : 
Itoa : Integer to ascii -> Converti le point number qui est un integer en valeur string

Le 2e wrangle : 
On vient créer / remplacer 2 vecteurs : vecteur N et vecteur Up


---
Regrouper des nodes dans un subnet : Shift + C

Scattering rochers : 

Voir cours

---

Matrice : 
il faut seulement savoir que c’est une recette de transformation


## Mercredi

A la place du copytopoints : 

For each point

Mettre capture 

-> Permet d’avoir plus de contrôle 

-> Voir aussi wrangle rotation avec matrice (pas dans le cours) 
	- Baisser le global scale du random angle


---

Faire le profil : 

Cercle :
- ZX plane
- 3 divisions 

Transform : 
- Rotate -90 sur y 

Convert line : converti chaque edge en polygon

Subdivide : 
- Group : 1
- Depth 1 

Transform : 
- Group : 3 
- Points 
- Trans Z : 0,5 environ

Transform : scale (le profil est bcp trop grand)
- uniform scale : 0,025

Ensuite on le connecte avec un copy to points 

Polyframe : 
- Décocher Normal name 
- Tangent name : tangent

Wrangle : 

```C
v@perp = cross(v@dir,v@tangent);
v@perp = normalize(v@perp);

v@dir = cross(v@tangent,v@perp);
```

Enft le wrangle sert à rien : suffit de cocher Bitangent Name

Enfin : 
Dans le polyframe : 
- Tangent Name : up
- Bitangent Name : N
- Cocher Make frame orthogonal

Wrangle : 

```C
f@pscale = 1-f@curveu;
```

Alternative au wrangle : remap 

---

On repart dans le profil : 
Delete: 
- *
- Keep points 

Add : On vient reconstruire le polygon 
- Polygons
- polygon 0 : 0 1 3 2

Enfin : 

Après le dernier copy to points : 
Mettre node skin 






