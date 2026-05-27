---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 14/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2026-01-23"}}
---



## Node Sort


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Node Sort/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Permet de trier / ranger des éléments

Exemple :

Par exemple ici on vient sauvegarder un ordre de primitive dans un wrangle actif sur les primitives (i@numero_prim = i@primnum;)

Et réappliquer l’ordre via l’attribut qu’on a créé avec le sort ensuite

![sort_node_image.png](/img/user/Pi%C3%A8ces%20jointes/sort_node_image.png)



</div></div>
 



## Boolean Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Boolean Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Les faces originelles gardent leurs attributs mais les faces crées prennent les attributs de la geo B

C’est donc un objet un peu “hybride”, où la geometrie n’est pas très propre

#### Resolve selft intersection :

En cochant cela le boolean vient fusionner les intersections, ce qui souvent n’est pas souhaitable

#### Rendre un boolean plus propre :

On peut utiliser un foreach pour traiter chaque primitive séparément

##### Node connectivity : 

Il vient créer un attribut class de type entier qui prendra des valeurs (0,1,2 etc) pour chaque geometrie connectée

---



</div></div>
 

## RBD configure


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/RBD configure/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

==-> Initialiser la configuration de l’objet RBD==

On va pouvoir définir la **densité**, **masse**, etc propre à la physique de l’objet

→ *Trouver ces infos précises pour les matériaux sur des gros sites de constructeurs ou des ressources scientifiques*

#### Régler plusieurs matériaux :
###### Méthode 1 : 

![rbd_configure_regler_plusieurs_mat.png](/img/user/Pi%C3%A8ces%20jointes/rbd_configure_regler_plusieurs_mat.png)

On peut sélectionner un groupe en particulier et créer plusieurs attributs (un pour chaque objet)

Mais cela va s’afficher seulement sous forme d’onglets avec des numéros et pas le nom des groups → pas très lisible

###### Méthode 2 


Donc on peut sinon stacker plusieurs RBD Configure à la suite :

![rbd_configure_stacking.png](/img/user/Pi%C3%A8ces%20jointes/rbd_configure_stacking.png)

_Ici le rbd config defaut configure l’ensemble de l’objet avec des paramètres généraux (par exemple un bois pour une cabane), pour être sur d’avoir toujours l’ensemble de la geo configurée pour la simu. Les configurations qu’on mettra après viendront prendre la priorité sur celle là bien sur_

#### Régler les volumes de collisions :

En les visualisant temporairement :
- visualize : collision padding
- collision shape : règler le collision padding

---



</div></div>
 


## RBD, Régler les comportements des éléments


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/RBD, Régler les comportements des éléments/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

![rbd_constraint_nodes.png](/img/user/Pi%C3%A8ces%20jointes/rbd_constraint_nodes.png)

#### RBD Configure

La première étape de configuration se trouve dans le [[3_GARDEN/Notes permanentes/RBD configure|RBD configure]] (voir la note)

#### RBD Constraint from rules :

Node pour créer des contraintes entre les RBD objects

<u><font color="#9bbb59">ll y a plusieurs types de contraintes de connections :</font></u>
- centres de gravité (par défaut)
- Surface points (tous les points de la surface)
- Hinges

On va pouvoir attribuer ces contraintes seulement à un groupe (identifié par le path ou le name par exemple) pour régler des éléments différentes comme le bois, puis le métal etc

<u><font color="#9bbb59">On va pouvoir donc avec ce node créer un groupe de constraint :</font></u>
- group type : primitive group
- group name : le nommer
- Autres paramètres :
	- Constraints per pieces :
		- -1 : autant que nécessaire
	- nombre défini : nombres de contraintes de connections entre les pièces
	- Search radius :
		- Permet d’éviter que des points trop loin entre eux soient connectés


##### RBD Constraint properties :

Créer les attributs nécessaires et régler les contraintes entre objet :

Par niveau de difficulté à briser : <font color="#c0504d">glue</font> (très dur) - <font color="#de7802">hard</font> (assez dur) - <font color="#9bbb59">soft</font> (facile)

En dessous se trouvent les paramètres propes à chaque type de contraintes (stiffness, etc)

-> On va pouvoir appliquer ces propriétés de contraintes uniquement sur le group créé au node précédent



> [!example] On va pouvoir donc régler tout cela pour chaque type d’élément :
> 
> ![rbd_constraint_general_view_multiple_objects.png](/img/user/Pi%C3%A8ces%20jointes/rbd_constraint_general_view_multiple_objects.png)
> 

---



</div></div>
 

## Récupérer les hard edges dans Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Récupérer les hard edges dans Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Dans un group (ou delete etc)
- include by edges :
	- cocher min edge angle

C'est très utile notamment pour faire des UVs procéduraux, pour gérer la déformation que provoque un remesh (cocher hard edges dans le remesh)



</div></div>
 