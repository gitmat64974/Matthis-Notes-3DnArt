---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX - Animation - Houdini/","tags":["note_permanente","en_cours"],"ctime":"2026-03-21T20:44:45.572+01:00","mtime":"2026-11-22T22:07:56.109+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/ANIMATION]]"],"source":null,"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2026-02-12","aliases":["APEX Animation Houdini"]}}
---

## La note 


Le [[3_GARDEN/Notes permanentes/Node\|Node]] principal d'animation d'un rig APEX est le APEX scene animate. Il permet à lui tout seul d'animer un rig APEX


> [!abstract] Le setup le plus basique : 
> 
> ![](https://i.imgur.com/lNsgrvo.png)
> 
> ***Scene add character*** : Ajouter le perso à la scene APEX d'animation. Nommer le node pour nommer le perso : important pour la propreté et la clarté
> ***Scene animate*** : pour animer le perso dans le framework APEX 

---
### Sélection sets


Ouvrir le paneau APEX selection sets, ou utiliser le petit widget dans le viewport appelé selection sets

<u><font color="#8064a2">Créer un set :</font></u> 
selectionner des controleurs dans le viewport, clic droit -> set from selection
Il y a plusieurs icones sur le set : désactiver la visibilité du perso, du set, etc

On peut aussi créer des folders, avec des empty layers, et on drag and drop d'autres sets dedans

<u><font color="#9bbb59">Mirror les sets</font> : </u>
toolbar du panneau de selection sets -> mirror -> mirror selected sets (on a également les 2 outils d'edit pour editer le naming et les patterns)

<u><font color="#d99694">Export sets : </font></u>
file -> export sets to file 
Cela va permettre de pouvoir les réutiliser et pas avoir à les refaire from scratch à chaque fois

Pinner un set va permettre de toujours mettre des clés sur ses controleurs, meme s'il ne sont pas sélectionnés. Très utile lorsqu'on est au blocking et que l'on veut être sur que chaque pose clé soit bien keyée. 

---
### Motion path

Ctrl + G dans le viewport pour avoir la petite fenetre des Animate settings
-> Motion path -> Bind (unbind pour l'enlever)

Là on peut voir le motion path du controleur sélectionné et bouger n'importe quelle clé sur le motion path, meme si on est pas à la position de cette clé dans la timeline. 

---
### Constraints

Selectionner l'enfant puis le parent et appuyer sur H 
Cela créée une contrainte
Tous les paramètres de la contraintes (blend, update etc) Sont dans les constraints parameters (G dans le viewport) ou les Animate settings (Ctrl G dans le viewport)

Ctrl H pour enlever une constraint

Pas oublier de bake les keys sinon on va perdre l'anim

---

### Mirror mode

Petite icone en haut du viewport

- **Shift clic dessus** : mirror le controleur opposé au controleur sélectionné
- **Clic dessus** : Mode mirror où bouger le controleur sélectionné fait bouger son opposé. Echap pour appliquer le mirror


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

Workshop complet APEX : [Animation Workshop \| Houdini HIVE Horizon - YouTube](https://youtube.com/playlist?list=PLXNFA1EysfYlYURsnOoPTD1cknWE8VjiQ&si=apPbxlauYDrK2Bef)

Vidéo de 30mn qui présente un workflow complet APEX (layers, ragdoll, dynamic motion etc) : [Character Animation Workflow \| Warren Leathem \| Houdini 20.5 HIVE Paris - YouTube](https://youtu.be/k46yhndKZtY?si=Qj98hUNN_FFYdrPe)


---

[[3_GARDEN/Notes permanentes/APEX Ragdoll\|APEX Ragdoll]] 

> [!example]- Flashcards
> ...




## Liens 








