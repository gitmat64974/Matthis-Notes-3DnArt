---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX - Animation - Houdini/","tags":["note_permanente","en_cours"],"ctime":"2026-03-21T20:44:45.572+01:00","mtime":"2026-11-24T21:40:26.169+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/ANIMATION]]"],"source":null,"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2026-02-12","aliases":["APEX Animation Houdini"]}}
---

## La note 


Le [[3_GARDEN/Notes permanentes/Node\|Node]] principal d'animation d'un rig APEX est le APEX scene animate. Il permet à lui tout seul d'animer un rig APEX


> [!abstract] Le setup le plus basique : 
> 
> ![](https://i.imgur.com/lNsgrvo.png)
> 
> ***Scene add character*** : Ajouter le perso à la scene APEX d'animation. Nommer le node pour nommer le perso : important pour la propreté et la clarté
> ***Scene animate*** : pour animer le perso dans le framework APEX 


### Bases

![](https://i.imgur.com/ebvfhHz.png)

Lorsqu'on est sur un scene animate, on peut appuyer sur entrée et mettre le viewport en full screen (ctrl + B) car on n'a besoin de rien d'autre pour animer.

***Poser une clé d'anim : K***

Interface : 
- En bas à gauche sont les **paramètres globaux d'animation** (FPS, audio etc)
- L'icone avec des sliders à gauche de la timeline : Ouvre la toolbar contenant la **tweenmachine** et bien d'autres sliders utiles à l'anim. La doc de l'animation toolbar : [Animation toolbar](https://www.sidefx.com/docs/houdini/anim/animationtoolbar.html)
- l'Icone avec des curves à droite de la timeline : ouvre le "**graph editor**" (appelé animation editor dans Houdini)
- La fenêtre à droite dans le viewport : **fenêtre principale** pour tout ce qui va être sélection, layers, paramètres, valeurs etc etc
	- en bas de cette fenêtre : un bouton pour ouvrir le **picker**


> [!tips]+ Tips généraux : 
> - Sélection de controles : en appuyant sur ctrl lors d'une translation ou rotate ou scale de plusieurs controles, c'est le pivot du dernier controle sélectionné qui gère la transformation. Super pratique pour faire du posing complexe sans setup de contraintes
> 
> -> [Working in the animate state](https://www.sidefx.com/docs/houdini/character/kinefx/animatestate.html) 


#### Copier coller des poses

Ctrl C / Ctrl V : copier coller la world position d'un controleur sur un autre
Ctrl C / Ctrl Shift V : copier coller la relative position d'un controleur sur un autre

---

### Mirror mode

Petite icone en haut du viewport

- **Shift clic dessus** : mirror le controleur opposé au controleur sélectionné
- **Clic dessus** : Mode mirror où bouger le controleur sélectionné fait bouger son opposé. Echap pour appliquer le mirror


---
### Sélection et layers

- [[3_GARDEN/Notes permanentes/Houdini Apex Selection Sets\|Houdini Apex Selection Sets]]
- [[3_GARDEN/Notes permanentes/Houdini Apex animation layers\|Houdini Apex animation layers]]



---
### Constraints

Selectionner l'enfant puis le parent et appuyer sur H 
Cela créée une contrainte
Tous les paramètres de la contraintes (blend, update etc) Sont dans les constraints parameters (G dans le viewport) ou les Animate settings (Ctrl G dans le viewport)

Ctrl H pour enlever une constraint

Pas oublier de bake les keys sinon on va perdre l'anim

-> [Constraints](https://www.sidefx.com/docs/houdini/character/kinefx/animatestateconstraints.html)

---
### Motion path

Ctrl + G dans le viewport pour avoir la petite fenetre des Animate settings
-> Motion path -> Bind (unbind pour l'enlever)

Là on peut voir le motion path du controleur sélectionné et bouger n'importe quelle clé sur le motion path, meme si on est pas à la position de cette clé dans la timeline. 


---
---

### Pose Tools


Apex dispose de plusieurs modes de poses et d'anim qui permettent différents traitement en fonction des besoins
Par défaut, on est sur le mode de base, le mode animate

> [!success]+ Mais il en existe plusieurs autres : 
> - **Locator** : un espace entier pour faire du posing et de l'anim avec des locators
> - **Dynamic motion** : pour appliquer un mouvement dynamique réaliste à l'animation
> - **Ragdoll et Ragdoll pose** : pour utiliser les outils de RBD temps réel en animation (simulation physique du mouvement, forces de vent, attraction etc, ou posing ou les collisions entre les objets sont prises en compte)
> - **Full body IK** : un homme pour faire du posing et de l'édition d'anim rapide avec le solver Full body IK, ou tout le corps devient un IK
> - **Secondary motion** : pour appliquer des mouvement secondaires (overlap par exemple) à des controleurs en fonction d'un controleur "driver"

#### Locators

Dans le mode locator, on peut créer des locators en venir transformer en FK les controleurs que l'on veut en fonction de ces locators

1. Placer la souris là où on veut que le locator soit puis appuyer sur H. Le locator est créé. On peut le bouger en cliquant dessus ensuite
2. Sélectionner les contrôleurs qu'on veut bouger puis le locator puis Ctrl Shift en rotation

On peut également parenter des locators ou faire d'autres opérations plus complexes : [Posing in the animate state](https://www.sidefx.com/docs/houdini/character/kinefx/animatestateposing.html)

---
#### Dynamic motion

Ajoute une trajectoire physique automatiquement à un objet qui possède seulement des poses clés : 

on donne quelques poses clés, H pour définir d'abord le centre de masse (généralement le controleur), puis H pour définir le début de la trajectoire, H pour la fin, etc entre toutes les poses clés


----

#### Secondary Motion

Permet d'ajouter automatiquement des overlaps, lags etc, tout ce qui est mouvement secondaire

![Capture d'écran 2026-09-26 230227.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-26%20230227.png)

Etapes : (*très simple et intuitif*)
1. Etre dans un scene animate et aller dans le menu de secondary motion (dernier icone en haut à gauche)
2. Aller dans les settings des secondary motion à gauche
	1. Setup le driver control : le controleur qui va driver le mouvement
	2. Setup les driven controls : Selectionner les controleurs dans le viewport et appuyer sur H (ou sur la fleche à côté de driven controls)
	3. Maintenant l'effet fonctionne. régler : 
		1. ***Extract transform*** (quels types de transforms sont affectés par l'effet, si c'est que de la trans, que de la rotate, que du scale, deux des trois, les trois etc)
		2. ***Transform mode*** : Uniform ou dynamic
		3. ***Effect*** : le type d'effet
		4. etc
	4. Selectionner les controleurs affectés un par un pour régler individuellement si besoin la force de l'effet via la fenêtre de secondary motion parameters
	5. Bake les keys sur un nouveau layer (onglet bake dans la même fenêtre) puis sortir du mode secondary motion



---

### Apex dans Solaris

Pour animer directement dans Solaris, on peut utiliser le node sopimportapexcharacter qui va importer le character puis le node Apex Animate tout simplement. 

![](https://i.imgur.com/rqHoRiM.png)

Il y a également le node sopimportapexscene qui permet d'importer une scène apex entière crée dans SOP
Ensuite mettre un apex animate pour récupérer et continuer l'animation (faire reset animation dans le node)

---
## Références

- [[3_GARDEN/Notes permanentes/APEX Ragdoll\|APEX Ragdoll]]
- [[3_GARDEN/Notes permanentes/Houdini motion mixer\|Houdini motion mixer]]

Tips utiles d'anim : 
- [[3_GARDEN/Notes permanentes/Animation stepping Houdini\|Animation stepping Houdini]]

#### Ressources

Workshop complet APEX : [Animation Workshop \| Houdini HIVE Horizon - YouTube](https://youtube.com/playlist?list=PLXNFA1EysfYlYURsnOoPTD1cknWE8VjiQ&si=apPbxlauYDrK2Bef)

Vidéo de 30mn qui présente un workflow complet APEX (layers, ragdoll, dynamic motion etc) : [Character Animation Workflow \| Warren Leathem \| Houdini 20.5 HIVE Paris - YouTube](https://youtu.be/k46yhndKZtY?si=Qj98hUNN_FFYdrPe)


---

[[3_GARDEN/Notes permanentes/APEX Ragdoll\|APEX Ragdoll]] 

> [!example]- Flashcards
> ...




## Liens 








