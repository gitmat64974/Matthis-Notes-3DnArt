---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Compositing V Besse, prof de lighting comp Montpellier/","tags":["note_litteraire","en_cours"],"ctime":"2026-04-06T00:00:31.000+02:00","mtime":"2026-09-30T23:07:52.773+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":null,"Projets":null,"tags":["note_litteraire","en_cours"],"creation date":"2026-01-30"}}
---


Tout ici est tiré exactement du cours [@COURS COMPOSITING - Google Docs](https://docs.google.com/document/d/1C9gltGdEsmRq6XpDTFhBSG23Sn--Eov0xE8PlJMjbQY/edit?tab=t.0) de V Besse

---


Tutos et sites de compositing : 

- [Kenn Hedin Kalvik](http://www.keheka.com)

- [Comp Lair - YouTube](https://www.youtube.com/c/CompLair)
- [ThriveCart](https://benmcewan--complairvfx.thrivecart.com/the-next-level-program-nrml/)

- [Compositing Academy - YouTube](https://www.youtube.com/channel/UCzqFnIJVQ1hVI-WZ62Sir1Q)
- [NK606 Nuke Course: Advanced CG Compositing and Look Development — Compositing Academy](https://gumroad.com/a/401822835)

- [Split The Diff - YouTube](https://www.youtube.com/c/SplitTheDiff)
- [Compositing Mentor – For those striving to learn as much about compositing as possible](https://compositingmentor.com/)

- [Conrad Olson - YouTube](https://www.youtube.com/channel/UCkAEJhzjSN7LJMWVdJ_C1bA)
- [NUKE 301 - 포토샵 & CopyCat 활용 사례연구 - YouTube](https://www.youtube.com/watch?v=PIoUgkPYEY4&list=PLjsf__Fqrwayg5NdxusYWk66WqjmRtu4c&index=32&ab_channel=VFXEdu)



### Plugins et gizmos nuke

#### Liens

- [Nukepedia — Free tool downloads for Nuke](https://www.nukepedia.com/)
- [GitHub - CreativeLyons/NukeSurvivalToolkit\_publicRelease: public version of the nuke survival toolkit](https://github.com/CreativeLyons/NukeSurvivalToolkit_publicRelease)
- [Comp Academy](https://compacademy.gumroad.com/)
- [Useful Nuke Tools And Setups](https://www.keheka.com/useful-nuke-tools-and-setups/)

Je liste ici des nouds qui paraissent interessants mais que je n'ai pas encore testes. La plupart viennent de l'excellent Nuke Survival Toolkit. Je ne vous conseille pas de l'installer en entier (il y a énormément de nœuds dedans) mais plutot de prendre des nœuds précis qui pourraient vous intéresser.


COLOR
ColorCopy TL == > Author: Tony Lyons - www.CompositingMentor.com
GradeLayerPass TL == > Author: Tony Lyons - www.CompositingMentor.com
AP COLOR SAMPLER : peut remplacer le curve tool en live ? http://www.nukepedia.com/blink/colour/colorsampler

FILTERS & EDGE
Sharpen/soften super efficaces : http://www.nukepedia.com/blink/filter/x_sharpen-and-x_soften/
http://www.nukepedia.com/blink/filter/x_sharpen-and-x_soften/
EdgeDetectAlias TL : Author: Tony Lyons - www.CompositingMentor.com detecte les edges non-anti aliasees seulement
http://www.nukepedia.com/gizmos/filter/edge-rim-light create a quick mask for your Rim Light
Edge extend (+ leger que le colour edge ?) http://www.nukepedia.com/gizmos/filter/edge-extend-2

DISTORTS & deformation
Il faudrait tester voir lequel est le plus simple/plus rapide
X distort : http://www.nukepedia.com/gizmos/transform/x_distort
HeatWave NKPD http://www.nukepedia.com/gizmos/filter/realheatdistortion
Ildistort EL : http://www.nukepedia.com/blink/transform/iidistort. Celui-ci est en blinkscript.
ITransform FR http://www.nukepedia.com/gizmos/transform/itransform/

EFFETS DE GLITCH ET D'ECRANS
Moire : https://www.youtube.com/watch?v=gS4zXJ6sLs8&ab_channel=CompositingAcademy
le plugin gratuit "VHS Effect" dans Davinci !:

RELIGHT
Relight_Simple SPIN relight à partir de normales (avec specs etc)
apDirLight AP Author: Adrian Pueyo - www.adrianpueyo.com (mieux que mon noeud de relight ?)
apFresnel AP www.adrianpueyo.com == > faire du facing ratio/fresnel a partir des normales
chopper le nœud de relight des 3D4 ?


#### Installation

-> C:\Program Files\Nuke14.0v5\plugins

- !! FAITES TOUJOURS UNE SAVE DES DOSSIERS/FICHIERS AVANT MODIF, EN CAS D'ERREUR !!
N'oubliez pas que dans un studio, vous pouvez parfois installer des plugins en local (votre machine) ou pour tout le monde (sur le reseau). Attention ou vous les mettez.
= Quel que soit le type de plugin a installer, le dossier dans lequel il est range doit etre appele par le fichier "init.py". Donc :
- Si vous le rangez dans un dossier deja existant, pas besoin de rajouter une ligne à "init.py"
- Par contre si vous le mettez dans un dossier qui n'est pas liste, il faudra ajouter une ligne a "init.py".

> [!example] Exemple de .init :
> if nuke.NUKE_VERSION_MAJOR == 12: nuke.pluginAddPath('R:/Nuke/13.1v2/python')
> *cette ligne demande à Nuke d'importer tout ce qu'il y a dans "R:/Nuke/13.1v2/python" lors du lancement du
> programme.*

= Si il y a de l'UI ( boutons, fenetres .. ) associee au plugin, il faudra probablement ajouter des lignes a "menu.py"
Ces deux fichiers sont presents dans R:\Nuke\NUKE_PATH.
- Le "menu.py" peut aussi appeller des icones, en general elles sont rangees dans R:\Nukel*version*licons

= Pour installer un ToolSet dans Nuke :
Les ToolSet permettent d'exporter/importer un ensemble de nodes facilement (si vous voulez en créer, tuto ici).
- Lors de la creation, le toolset est ecrit en local dans U:\nuke\ToolSets.
-
Pour que tout le monde y ait acces, ils doivent etre ranges dans R:\Nuke\NUKE_PATH\ToolSets. Pas besoin d'appeler ce path dans le fichier init, car Nuke charge ce chemin a
l'ouverture par défaut.
Les plugins sont principalement ranges dans l'icone de "petite boîte" dans la toolbar. Si vous ne voyez pas le votre apparaître lorsque vous faites "tab" dans le nodegraph, cliquez sur
"Update" comme sur l'image ci-dessous. Il se peut que vous ayez a le faire deux fois.

### Relative path Nuke

S puis script directory : cela set votre projet 

Ensuite on peut enlever dans le file path de tous les read ce qui se trouve avant le nom du project directory


### Pipeline Comp

#### Arborescence



![Pasted image 20260130223350.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260130223350.png)



#### Organisation

*Source : [[3_GARDEN/Notes littéraires/Cours Compositing V Besse, prof de lighting comp Montpellier\|Cours Compositing V Besse, prof de lighting comp Montpellier]]*

1) KEYSHOT LIGHTING : Le lighting et le comp sont realises sur un keyshot.

2) CLEANING: Le look du keyshot est valide. LES CHANGEMENTS FAITS EN COMP DOIVENT ALORS ETRE LE PLUS POSSIBLE RAPATRIES DANS LA SCENE DE LIGHTING DU KEYSHOT. Cela evitera arbres de comp énormes, shifts de couleur salis et différences entre vos shots. On en profite pour virer les AOVs inutiles. Exemple : J'ai change l'exposure de ma light de 1 dans Nuke. Si le look du plan est valide =je fais de meme dans ma scène : je change l'exposure de ma light de 1 avant de re-rendre. Dans Nuke, je désactive ou supprime le [[3_GARDEN/Notes permanentes/Node\|Node]] d'exposure. J'ai desormais un lighting propre qui ne nécessite pas de changement en comp.

3) PROPAGATION : Le lighting du keyshot cleane est propage dans les shots de la sequence. On sort les frames en qualite basse/demi-rez d'abord.

4) SHOT LIGHTING : On peut desormais pousser le lighting, puis le comp de chaque shot de la sequence.

> [!tip]+ CONTINUITÉ :
> = A chaque rendu, pensez a comparer votre compo a votre pre-comp afin de vous assurer que vous n'avez pas perdu de choses essentielles entre ces 2 etapes
> = Regardez toujours un plan dans le contexte de sa sequence : dans vos compos, chargez dans un read le plan precedent et le plan suivant.
> = Lorsque vous bossez sur un Keyshot, comparez-le toujours avec vos art 2D. Servez-vous de la section "COMPARE" en bas de votre template
> = Lorsque vous bossez sur un childshot, comparez-le toujours avec son keyshot
> = Une fois que vous avez un rendu de lighting, aidez-vous en faisant des paintovers sur une frame fixe. Cela aide a diriger le comp et a respecter l'intention de depart.


![](https://i.imgur.com/gXKcETr.png)




### Concaténation

C'est une optim des nouds similaires lorsque plusieurs nouds de meme nature transforment votre image les uns après les autres. Chaque noud transmet ces operations de transformation au suivant, et seul le dernier noud de la ligne effectue alors toutes les transformations d'un coup. Groupez les nœuds de nature le plus possible afin de ne pas casser cette concatenation !

Exemple : au lieu d'effectuer chaque transformation separement et de filtrer l'image d'entree plusieurs fois, Nuke combine les transformations et ne filtre l'image
qu'une seule fois, à la fin. Si vous insérez un nœud entre, cela rompt la concaténation et l'image est filtrée plusieurs fois = mauvaise qualité


![Pasted image 20260130224923.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260130224923.png)








### Relight 


#### 2D Fake rim : 

[2D Rim Lights Look FAKE - But Not Anymore - YouTube](https://www.youtube.com/watch?v=WcB524Y32Io&ab_channel=CompositingAcademy)

#### 2D using normals : 

*Pour des relights simples et rapides, bien sur les ombres ne seront pas aussi logiques que de vraies lights dans Nuke ou dans un logiciel de 3D*

[[3_GARDEN/Notes permanentes/Normale\|Normale]]

Le process : 

![Pasted image 20260131002734.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260131002734.png)


1. Extraire la pass de **Worldnormal** (shuffle)

2. Ajouter un **constant** (le plus gros est ici) : 
	1. **Ajouter des paramètres** au [[3_GARDEN/Notes permanentes/Node\|Node]] (manage user knobs -> floating point slider) comme sur la capture d'écran plus haut
		1. equator_angle : 
			1. range : 0-360
		2. polar_height : 
			1. range : -90 - 90


3. Ajouter également la **color** dans le constant (pour cela : pick au lieu de add knob)
	- Rentrer ces **expressions** dans la color (voir [[3_GARDEN/Notes permanentes/Normale\|Normale]] pour des explications sur leurs significations) 
		- ![Pasted image 20260131003203.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260131003203.png)


> [!note]+ Gizmo
> Ensuite on peut en créer un gizmo : [[3_GARDEN/Notes permanentes/Creation de Gizmo Nuke\|Creation de Gizmo Nuke]]
> 
> > [!tip]- Ajouter un crop dans le group pour automatiquement crop à la résolution de l'image d'input : 
> > 
> > ![Pasted image 20260131004111.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260131004111.png)
> > 
> > Cliquer sur reformat ensuite
> 


[Nuke Tutorial \| Relighting using Normal Pass - YouTube](https://youtu.be/VZljzMID4So?si=5EpYtcvnGrl5YRfI)


#### Pos pass + 3D in nuke




