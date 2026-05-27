---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/10e cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[CFX]]","[[HOUDINI]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2026-01-16"}}
---



## Crowd


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

<iframe width="560" height="315" src="https://www.youtube.com/embed/65Zg0VECsGg?si=e4myBL_yhBCP5VMi" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

-> Foule au cinéma de manière générale

Exemple avec star wars dans la menace fantome ils ont utilisé des cotons tiges avec une soufflerie en dessous pour les animer un peu

---

Le principe de boids : 

Craig Reynolds ([Craig Reynolds — Wikipédia](https://fr.wikipedia.org/wiki/Craig_Reynolds)) a extrait un principe mathématique qui régit le comportement des foules en observant le vol des oiseaux

Ce principe contient 3 règles 
- séparation : chaque entité à sa propre zone
- cohésion : rester proche du groupe
- alignement : aligner le comportement de chaque entité sur le groupe


Expérimenter ludiquement avec  ce principe : [Boids Simulation](https://boids.dan.onl)

Et c'est exactement comme cela que Houdini gère les simulations de foule

[VFX - Breakdown "Why V&B" Crowds - YouTube](https://www.youtube.com/watch?v=7fyfAz7lVqg)
[amazing starlings murmuration (full HD) -www.keepturningleft.co.uk - YouTube](https://www.youtube.com/watch?v=eakKfY5aHmY)


---

Premier film qui a utilisé le principe de boids : 
Jurassic Park (1993) -> breakdown : [ILM Before and After Jurassic Park - YouTube](https://www.youtube.com/watch?v=DuMlHcCunGA)

Et le seigneur des anneaux l'a appliqué à des foules immenses : [Visual Effects Demonstration The Mumakil Battle The Lord of the Rings: The Return of the King - YouTube](https://www.youtube.com/watch?v=xNMZ0-Yl1uU)

#### Ragdoll

C'est un état d'une entité dans une crowd simulée et non animée
Souvent on switch entre anim et sim ragdoll dans les crowds 

---

Dans Houdini : [[3_GARDEN/Notes permanentes/Crowd Houdini|Crowd Houdini]]


---



</div></div>
 

## Crowd Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Crowd Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Le setup de crowd de base complet est décrit ici

#### Agent

C'est la base du système de crowd de Houdini
Un agent est une entité qui peut contenir un personnage, une geo etc mais qui est traitée comme un seul point, comme une particule, et spécialement setupé pour le système de crowd.

---

On va donc créer un agent et importer un fbx

![](https://i.imgur.com/bfTxYlR.png)

Ensuite on ajoute une animation avec un agent clip : on vient renseigner le fbx animé et on nomme le clip

On peut cocher le clip preview et mettre l'anim qu'on vient de créer pour preview

![](https://i.imgur.com/KB4czQ5.png)

> [!node]+ Locomotion
> Dans l'onglet locomotion : 
> 
> On vient ici définir quel est le joint de locomotion : les hanches généralement (hips)
> Après avoir défini les hanches dans l'onglet locomotion, Cocher convert to in-place animation pour que l'anim soit sur place
> 
> Ensuite quand on coche dans clip preview "apply clip locomotion" l'animation ne boucle plus et il avance constamment

---

On peut venir ajouter d'autres anims dans ce node en ajoutant des clips 
Et on définit le set current clip sur l'anim qu'on veut avoir

![](https://i.imgur.com/4CYqZo8.png)

#### Agent clip properties 

node pour gérer le comportement d'un (ou plusieurs) clip d'animation
Par exemple enlever une boucle sur une anim qui boucle : décocher enable looping

==Attention il faut utiliser la sortie de droite et pas celle de gauche !==
#### Agent Layer


(*Attention il change en fonction des versions*)

Node qui permet d'ajouter des props / objets etc aux agents

##### Le process : 

![Pasted image 20260116160913.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260116160913.png)

Merge packed : on nomme les primitives packées 

Dans le Agent Layer : 
- Use existing shapes : cocher Source Layer "defaut" 
- Agent un shape bindings avec le nom de la primitive packée 
- On peut ajouter un layer par objet : 

*Attention le binding vient automatiquement diviser la taille de l'objet par 100, le transform après le merge packed vient le prévoir en multipliant par 100*



#### Crowd Source

Node qui vient dupliquer un agent pour en faire une crowd

On a 2 modes de layout : random et formation (alignés / rangés)

L'onglet randomize : 
- Randomize primitive : randomize des agents
- Randomize current layer : pour randomize les layers créés
- Randomize clip time : randomize le décalage des animations
- Randomize scale

Le crowd source à une deuxième entrée qui permet d'utiliser un terrain custom


#### Crowd motion path


Le node crowd motion path vient initialiser les motion paths

Puis on a toute une série de nodes pour gérer les motion paths et leurs influences : 

Crowd motion path follow : 
On branche les 2 sorties du crowd motion path dans les 2 premières entrées puis une curve custom dans la 3e entrée

Crowd motion path avoid : 
Eviter un objet sur le chemin 
-> 3e entrée : geo à avoid
Dans ce node il y a un paramètre pour gérer les "collisions" entre agent (-> neighbors)

Crowd motion path trigger : 
Permet de trigger un attribute en fonction d'une collision à un objet
- En combinant avec le crowd motion path transition on va pouvoir par exemple trigger une anim différente lors de la collision 
	- type : object distance
	- Cocher time dependant si la geo de collision est animée
	- Dans le node crowd motion path transition
		- Mettre le trigger group et le clipname de la nouvelle animation


![Pasted image 20260116164715.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260116164715.png)

Crowd motion path evaluate : viens "bake" les actions du motion path

#### Agent terrain adaptation


Node permettant de faire suivre les agents au terrain (adapter les pieds automatiquement etc)

On peut régler l'étirement des genoux et plein d'autres choses pour adapter le mouvement au terrain 
##### Préparer le node terrain adaptation

Ce node doit être couplé à un node agent prep (préparation de l'agent, à mettre donc avant toutes les simu de crowd etc, on travaille sur la préparation de l'agent) : 

On va définir dans ce nodes les Lower Limbs et le torso pour que le node d'adaptation au terrain puisse savoir quel joint est le pied, le genou etc

(On peut déplacer dans le viewport l'emplacement des leg, ankle etc pour ajuster la déformation si besoin : par exemple le talon des rigs mixamo est trop haut ce qui cause des problèmes à l'adaptation au terrain)


![Pasted image 20260123144349.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260123144349.png)

Ensuite manip pour la plant des pieds avec le chop network : 
additionnal channels -> Create foot plant chop network 

Chop Network : 
En gros il va "bake" l'anim d'une simu : convertir la position en informations de courbes d'anim etc pour pouvoir retoucher à la main les anims

Enfin, si besoin de "corriger" le placement des joints sélectionnés on peut le faire à la main simplement en les selectionnant et en les bougeant

---

### Export Crowd

On va venir exporter en alembic les différentes couches grace à l'attribut name généré automatiquement

Par exemple : unpack -> split -> rop alembic





</div></div>
 

