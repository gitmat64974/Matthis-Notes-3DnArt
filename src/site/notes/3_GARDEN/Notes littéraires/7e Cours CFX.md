---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/7e Cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[CFX]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-12-12"}}
---



## Process de Groom Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Process de Groom Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

---
![](https://www.sidefx.com/docs/houdini/images/fur/nodes.jpg)

[Hair and fur](https://www.sidefx.com/docs/houdini/fur/index.html)

Au scene level : 
En ayant la geo selectionnée, dans le shelf Hair Utils cliquer sur **create guides** (ou add fur, qui va créer les 2 nodes )

![](https://i.imgur.com/V9SiC3s.png)

![](https://i.imgur.com/pOyYqKQ.png)


La création de masques se fait par des [[3_GARDEN/Notes permanentes/Attribute paint|Attribute paint]] dans la geo (Ce qui permet de peindre les masks sur des points (et pas des UVs comme sur Maya))


> [!abstract]+ Gérer la density
> ---
> 
> Créer un [[3_GARDEN/Notes permanentes/Attribute paint|Attribute paint]] dans la geo et peindre là où on veut que les poils soient
Bien rename l'attribute (qui s'appelle *mask* de base) en *density*
> 
> ---
> Dans la parameter window du node guide groom : 
> - Density
> 	- No override -> Skin attribute
> 		- *density*
> 

---

### Manipulation des guides 



> [!abstract]+ Le process que l'on va suivre : 
> 
> ![](https://i.imgur.com/ILFok2L.png)
> 
> 1. Définir la longueur des poils avec le guide process set lenght
> 2. Gérer la direction avec guide advect
> 3. Relever les guides
> 4. Ajouter du noise etc


#### Guide process set length

Entrer dans le node groom et créer un guide process set lengh et le placer au milieu, tout va se connecter : 

![](https://i.imgur.com/BwcH588.png)

Dans ce node on peut venir gérer la longueur des guides

Avoir différentes longeurs : 

> [!NOTE] Masque
> On peut mettre un masque dans l'onglet masking pour attribuer un masque fait avec un attribute paint par exemple

> [!NOTE] Répétition
> Et répéter cette opération avec plusieurs node guide process avec différents masques

#### Guide advect

Dans le shelf Guide process cliquer sur Curve advect 

ça va créer toute une suite de nodes : 

![Pasted image 20251212160939.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251212160939.png)

Le node draw curve permet de dessiner la direction des poils (le sélectionner et avoir le handle tool d'activé)

#### Guide process lift : 
 
On peut ajouter un guide process lift pour relever les guides 
*On peut aussi définir un ramp dans le paramètre lift*
Bien sur on peut masquer ce lift, etc etc

#### Guide groom 

Node pour "coiffer" (faire toutes sortes d'opérations à l'aide d'un brush) : 
- Draw : pour dessiner des guides à la main
- Sculpt
- Clump
- Cut : Cut
- etc etc

Par contre ce node est destructif


#### Guide process freeze

C'est un noise de poil 


#### Simulate guide

Appeler le node : 
Retourner au scene level, cliquer sur le node guide groom et cliquer sur simulate guide dans le shelf Hair Utils

Dans ce node, tout est rassemblé pour la simulation : vellum solver, constraints, physiques, forces etc

On peut également cache directement dans ce node dans l'onglet caching

---

### Hair generation


Revenir au scene level, selectionner le guide groom et cliquer sur generate hair dans le shelf Hair Utils

![](https://i.imgur.com/AQQGX8m.png)


En rentrant dans le node hair generate, on peut gérer à nouveau les noises, lenght etc avec les guide process, et le guide groom, en commençant notamment par le clump avec le Hair Clump : 

![](https://i.imgur.com/42aL6aC.png)

#### Hair Clump

Entrer dans le Groom Hair_gen et brancher un node hair clump comme cela : 

![Pasted image 20251212164124.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251212164124.png)

là on peut gérer tout ce dont on a besoin pour les clump

#### Guide mask

Permet de créer un masque sur le fur et non sur les points ou les UVs

> [!example]+ Exemple pour créer des "cheveux fous"
> Additionnal Masks : 
> Cocher random mask, et choisir une petite fraction
> 
> Rajouter un frizz qui n'agit que sur ce mask pour faire des "cheveux fous" qui partent dans tous les sens

---



</div></div>
 

