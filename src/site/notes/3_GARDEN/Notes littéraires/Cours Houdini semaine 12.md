---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 12/","tags":["note_litteraire","cours","A_traiter"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours","A_traiter"],"creation date":"2026-01-12"}}
---



### Rig et anim procedural de l'arbre 

2 grosses notions : 

- Structure propre de curves utilisables pour un rig : Il faut que tout soit une structure type parent - enfant sans cycle (un enfant ne peut pas être le parent de son parent)
- Skinning par tetrahedre : 
	- Permet de skinner par correspondance intérieur et pas selon la surface. Par exemple un point sur la jambe droite n'aura aucun risque d'être influencé par un joint de la jambe gauche car le chemin intérieur est très long (contrairement à un skinning qui ne prend en compte que la surface)

Un tétraèdre est un polyèdre à quatre faces triangulaires, six arêtes et quatre sommets. C’est la forme tridimensionnelle la plus simple, appartenant à la famille des pyramides.

---

La generation de l'arbre sort des curves (2e sortie des nodes generator), que l'on va utiliser comme base pour le rig

DAG : veut dire directed acyclic graph
-> En gros c'est une structure hiérarchique d'objets

C’est un outil très utilisé en informatique pour représenter des dépendances ou des flux d’opérations qui vont toujours dans le sens « avant », par exemple des étapes de calcul ou de rendu

Cette représentation évite les boucles infinies dans les dépendances (par exemple un objet A dépendant de B qui dépendrait lui-même de A), ce qui permet un calcul plus prévisible et plus performant

## Rig

Un joint c'est un point identifiable avec une direction (une matrice de transformation)


### Skinning

Utiliser le bone capture biharmonic

tetrahedrons : tetrahedres qui viennent remplir l'espace à l'intérieur de l'objet
C'est un très bon moyen pour avoir un skin de base assez propre et logique 

![Arbre_Skinning.png](/img/user/Pi%C3%A8ces%20jointes/Arbre_Skinning.png)


### Point deform

Il permet d'avoir une animation propre d'un objet : on vient appliquer uniquement la déformation tout en préservant tout le reste. 
C'est indispensable dans un pipeline d'alembic pour travailler proprement : on s'assure que la version animée soit identique à la version statique. 

L'utiliser concrètement : 

![point_deform.png](/img/user/Pi%C3%A8ces%20jointes/point_deform.png)

Ici on deforme un skeleton avec une simulation vellum
Avec le point deform on vient uniquement récupérer la position animée des points et l'appliquer sur le skeleton de base sans garder tout ce qui peut être parasite du à la simulation
1ere entrée : 
Skeleton de base
2e entrée : 
skeleton juste avant deformation
3e entrée : 
skeleton deformé 

### Alembic merge dans Solaris

On va le faire avec de l'usd mais c'est pareil :

Avoir un asset reference avec l'asset usd static
Puis un node reference avec l'usd animé de la geo de cet usd. Mettre dans ce node : 
- primitive path : la primitive exacte de l'asset usd static
- reference primitive : reference specific primitive 
	- reference primitive path : la primitive exacte de la geo animée en usd

#### Pour des animations type keepalive

Après ça on peut mettre un usd render Rop et sauvegarder dans le fichier de l'asset usd une version animée keepalive, pour ne pas avoir à resetup le "merge" à chaque fois


