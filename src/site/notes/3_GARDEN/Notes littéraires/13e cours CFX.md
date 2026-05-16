---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/13e cours CFX/","tags":["note_litteraire","cours","en_cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[CFX]]"],"source":"[[Cours CFX ESMA]]","Projets":null,"tags":["note_litteraire","cours","en_cours"],"creation date":"2026-02-13"}}
---



Find shortest path : 
Node qui va trouver le chemin le  plus court et rapide entre 2 points
Ou entres plusieurs selon le mode de ``output path``

Node super pratique pour faire des éclairs, des veines, des branches d'arbres etc


---

#### Préparation du maillage : 

On vient remesh pour avoir une geo en tris assez dense, sinon le find shortest path va trop suivre la topo de base, topo qui va donc se faire trop sentir. 

Ensuite on vient créer des variations dans le maillage pour que le findshortestpath crée des ondulations : 

![Pasted image 20260213143755.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260213143755.png)

On fait ça avec 2 nodes : 
Un attribute noise où on crée un attribut delete_map en float. Ce sera un noise sur la géo dans un attribut
Delete pour supprimer des points en fonction de cet attribut : 
- operation : delete by expression
	- `@delete_map > 0.5`


---
#### Définir le start point et le end point

Ensuite un group avec un point, pour le départ de la simu : sélectionner un point dans la nuque par exemple

###### Pour les end points : 

On veut pouvoir sélectionner un pourcentage donné de points aléatoirement : 

![Pasted image 20260213144235.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260213144235.png)

La VEXpression : 
`rand(@ptnum) > ch("point_nb")`


#### Find shortest path

![Pasted image 20260213151105.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260213151105.png)

Start points : start_points
End points : end_points

output path : from each start to each end

Ce node crée plusieurs attributs très utiles : 
- Cost : distance entre start et end
- path cost : (*Lui il faut specifier son activation*) Il permet de venir séparer toutes les curves générées, tout en attribuant une valeur à chaque curve qui correspond à sa longueur


##### Animer ces veines

On va utiliser le node carve, qui sert à découper, slicer etc des primitives
- first U : 0
- second U : c'est là qu'on vient gérer la progression, le growing

Donc on peut mettre des clés d'anim sur le second U

On peut aussi mettre un resample après pour smoother un peu les curves :
- baisser la lengh
- mettre en subdivision curve
- cocher curveu attribute

Curveu c'est comme le path cost, mais en normalisé, c'est à dire que toutes les curves ont un curveu qui va de 0 à 1 quelle que soit sa longeur

#### Noiser le pscale


Créer l'attribut pscale avec un attribut create et lui donner un valeur de 1

Puis on va gérer le pscale avec un attribut vop pour avoir beaucoup de controle sur l'évolution du pscale en fonction des veines

##### Pscale_randomize : 

![Pasted image 20260213151956.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260213151956.png)

Fit : comme un remap
Certains paramètres du noise et fit sont promote

On va animer le flow du noise : 
$F/35
35 : valeur arbitraire pour la rapidité du noise

#### Sweep

Scale along ramp : 
En preset hill



