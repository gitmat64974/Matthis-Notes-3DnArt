---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Process de Groom Houdini/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:35.687+01:00","mtime":"2026-09-26T20:26:22.175+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/GROOM]]","[[3_GARDEN/MOCs/CFX]]"],"source":["[[3_GARDEN/Notes littéraires/7e Cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":202512121733,"aliases":null}}
---

## La note 

---
![](https://www.sidefx.com/docs/houdini/images/fur/nodes.jpg)

[Hair and fur](https://www.sidefx.com/docs/houdini/fur/index.html)

Au scene level : 
En ayant la geo selectionnée, dans le shelf Hair Utils cliquer sur **create guides** (ou add fur, qui va créer les 2 nodes )

![](https://i.imgur.com/V9SiC3s.png)

![](https://i.imgur.com/pOyYqKQ.png)


La création de masques se fait par des [[3_GARDEN/Notes permanentes/Attribute paint\|Attribute paint]] dans la geo (Ce qui permet de peindre les masks sur des points (et pas des UVs comme sur Maya))


> [!abstract]+ Gérer la density
> ---
> 
> Créer un [[3_GARDEN/Notes permanentes/Attribute paint\|Attribute paint]] dans la geo et peindre là où on veut que les poils soient
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


## Références

Pour le shading et rendu du groom : [[3_GARDEN/Notes permanentes/Groom rendering Houdini\|Groom rendering Houdini]]
Pour la simulation du groom : [[3_GARDEN/Notes permanentes/Groom simulation workflow Houdini\|Groom simulation workflow Houdini]]

Vidéo YT de référence pour les cheveux : 
<div class="rich-link-card-container"><a class="rich-link-card" href="https://youtu.be/rVogGr7f0Cg?si=A_NqSR36d732re_L" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://i.ytimg.com/vi/rVogGr7f0Cg/hqdefault.jpg')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">The Only HAIR GROOMING Tutorial You Need! (Houdini for Artists)</h1>
		<p class="rich-link-card-description">
		Enjoy the videos and music you love, upload original content, and share it all with friends, family, and the world on YouTube.
		</p>
		<p class="rich-link-href">
		https://youtu.be/rVogGr7f0Cg?si=A_NqSR36d732re_L
		</p>
	</div>
</a></div>
<div class="rich-link-card-container"><a class="rich-link-card" href="https://youtu.be/PHBWAqlODAU?si=ZanxQwD5Q_ZfXlid" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://i.ytimg.com/vi/PHBWAqlODAU/hqdefault.jpg')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Houdini Hair Tutorial</h1>
		<p class="rich-link-card-description">
		Enjoy the videos and music you love, upload original content, and share it all with friends, family, and the world on YouTube.
		</p>
		<p class="rich-link-href">
		https://youtu.be/PHBWAqlODAU?si=ZanxQwD5Q_ZfXlid
		</p>
	</div>
</a></div>

---

- [[3_GARDEN/Notes permanentes/Queue de cheval groom houdini\|Queue de cheval groom houdini]]


> [!example]- Flashcards
> ...




## Liens 
