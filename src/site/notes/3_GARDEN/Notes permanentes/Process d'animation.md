---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Process d'animation/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.410+01:00","mtime":"2026-04-24T17:43:18.928+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/ANIMATION]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":null,"aliases":["Blocking d'animation"]}}
---


- [[3_GARDEN/Notes littéraires/Cours Anim bases général\|Cours Anim bases général]] 
- [[3_GARDEN/Notes littéraires/1er Cours d'animation esma 3d2\|1er Cours d'animation esma 3d2]]
- #video [How to Keyframe Like a Pro! (Animation process for any software) - YouTube](https://www.youtube.com/watch?v=E-sF_1FgpJw)
Projet : 
Tags : #note_permanente
Date : 2024-09-15

## La note

### Blocking

(Dans les anim plus importantes et complexes on peut avoir un layout avant : Par exemple en CG on anime le contrôleur général pour avoir une idée de l’anim, le timing, et le blocking de la caméra, puis on vient supprimer les clés sur le général pour commencer le blocking)

**Première étape de l’anim → base de l’anim, première anim qui permet de faire passer l’intention, de mettre en place l'action et de comprendre le déplacement**

3 méthodes de blocking (Qu’on peut utiliser en même temps) :
1. Layering : faire une anim basique puis rajouter des détails en layer -> [[3_GARDEN/Notes permanentes/Keyframe\|Hiérarchie des keyframes]]
2. Pose to pose : faire que les poses principales, les Keys (voir [[3_GARDEN/Notes permanentes/Keyframe\|Keyframe]])
3. Straight ahead : anim faite frame par frame → chiante pour planifier etc mais bien pour animer des éléments secondaires (cheveux etc) qui se rajoute à un blocking pose to pose en layering par exemple

#### Méthodologiquement

La méthode du **layering** : 
Suivre la [[3_GARDEN/Notes permanentes/Keyframe\|Hiérarchie des keyframes]]
1. Poser les **keys** (les poses clefs, essentielles au story telling, c a dire qu'en regardant seulement ces poses on comprend l'histoire ou l'action) 
	1. Ces Posings doivent être précis et soignés car le reste de l animation découle de ces derniers. 
	2. A noter que on va souvent tenir ces poses (2 ou 3 frames) 
	3. On peut ensuite créer ces amortis (tenir un peu les poses clés) (à la tween machine en CG).
2. Poser les **extrêmes** (poses essentielles à l'action mais non essentielle à la compréhension de l'histoire), comme l'anticipation ou l'overshoot
3. Poser les **breakdowns** (C’est la pose centrale qui relie deux poses clefs) pour avoir un sens du [[3_GARDEN/Notes permanentes/Timing\|Timing]] (bouger les breakdowns pour expérimenter avec le [[3_GARDEN/Notes permanentes/Timing\|Timing]] et la base du [[3_GARDEN/Notes permanentes/Spacing\|Spacing]]). *Chercher à donner le maximum d'informations de mouvement dans les breakdown* (poids, changements de jambe d'appui, [[3_GARDEN/Notes permanentes/Motion blur\|Motion blur]] ou smear, exagération etc)

### La suite (in between)

On s'occupe ici des intervalles (toutes les poses entre les poses clés, extremes et breakdowns), poses qui vont gérer essentiellement le spacing

En 3D, c'est là où on commence à toucher au graph editor : L'étape de **Spline** -> 
2ème étape de construction du plan. Les courbes d’anim passent de Step à Spline. Il faut généralement re-dynamiser l action (Timing) qui a perdue en énergie. C’est le moment d ajouter toutes les clefs d’anim pour finaliser l action

En 2D, ce sont les poses en plus pour finir l'animation. Là on est plutôt dans le spacing (voir [[3_GARDEN/Notes permanentes/Timing\|Timing]]) 
- Toujours penser à aller du plus gros au plus petit, des poses les plus importantes aux moins importantes 
- Toujours penser à transmettre l'impression de mouvement 
- On peut planifier ces poses avec un [[3_GARDEN/Notes permanentes/Timing\|Timing]] chart si il y a besoin

On peut animer les fx, si on en veut, en straigh ahead, c'est bien plus simple et fluide


> [!abstract] **Methodo générale d’anim en CG:**
> - Layout : On anime le contrôleur général pour avoir une idée de l’anim, le timing, et le blocking de la caméra puis on vient supprimer les clés sur le général pour commencer le blocking
> - Blocking (Courbes dans le graph en step) 
> 	- Block 1 : poses clés (pré block si l'anim est vraiment complexe), poses les plus dynamiques, intéressantes et travaillées possible
> 	- Block 2 : extrêmes et breakdowns
> - Spline : courbes dans le graph en spline
> 	- Spline 1 : timing bon etc
> 	- Spline 2 : 
> 		- la on peut bouger les clés et en mettre partout prcq le timing est bon, vérifie au Spline 1
> 		- on cherche à avoir toujours du mouvement, à équilibrer entre dynamisme et flottement dans les poses assez statiques.
> 		- On va chercher aussi beaucoup à désynchroniser, à [[3_GARDEN/Notes permanentes/Overlap\|Overlap]] avec du retard etc.
> - Polish : clean ultime puis rendu de la scène au lighteur. C’est l étape finale du plan. Avant de transmettre notre animation aux autres départements (lighting, vfx …), on vérifie les glissements, pénétrations, arcs, spacing etc…

## Références 

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/E-sF_1FgpJw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

- Noter qu’on doit dans les anim d’actions alterner entre des actions dynamiques et des respirations.
## Liens 

