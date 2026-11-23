---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Anim bases général/","tags":["note_litteraire"],"ctime":"2026-03-21T20:44:11.681+01:00","mtime":"2026-04-24T17:43:19.072+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/ANIMATION]]"],"source":["#cours [[Cours d'animation ESMA]] 3D1"],"Projets":null,"tags":["note_litteraire"],"creation date":"2024-09-15"}}
---


# Chapitre 1, introduction

## Planning d’animation


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Planning d’animation/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note

1. **Visualisation** : fermer les yeux et visualiser l’anim qu’on veut faire, le perso bouger etc
2. **Idée Générale formulée**: rechercher des idées, avoir conscience que la première idée est souvent un cliché et pas souvent à retenir
3. **Concevoir et tester plus précisément chaque plan** avec la [[3_GARDEN/Notes permanentes/Méthodologie générale de création\|Méthodologie générale de création]]
4. **Concevoir et tester les mouvements** (de persos, de caméra), **puis les détails**
5. **Commencer le [[3_GARDEN/Notes permanentes/Process d'animation\|Process d'animation]]** avec des **Références** vidéos : on Anim toujours avec des références. On peut bien sûr et c’est le mieux, faire les refs soi même → se filmer (ce que font énormément d’animateurs pro), sinon sur internet. On peut chercher aussi sur internet des décompositions de mouvement, ça aide beacoup et il y en a bcp. *Observation habituelle : s’appuyer sur ce qu’on voit dans la rue etc. Pk pas avoir un carnet tjrs sur soi pour noter des idées des observations etc*
6. **Retours** : demander des retours sur l’anim → aux connaisseurs et non connaisseurs (c eux qui vont voir l’anim au final)



</div></div>
 

## Blocking (animation)


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Process d'animation/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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


</div></div>
 

## Keyframe


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Keyframe/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note

1. En [[3_GARDEN/MOCs/ANIMATION\|ANIMATION]] les **keys**, les clés sont les poses principales qui permettent de lire l’action ou l’intention avec le moins d’informations possibles.*Par exemple une balle qui rebondit : les keys sont les moments où elle touche le sol et où elle est le plus haut en l’air.* Les keys sont ce sur quoi on se concentre en premier en [[3_GARDEN/Notes permanentes/Process d'animation\|Process d'animation]]. 

2. Ensuite vient les **breakdowns** : images secondaires qui sont les plus importantes après les keys. Elles sont entre les keys.

3. Ensuite vient les **inbetween** : images de transitions entre toutes les images précédentes. En [[3_GARDEN/MOCs/ANIMATION\|ANIMATION]] 2D c’est l’inbetweeneur qui dessine les dessins entre les poses, et en [[3_GARDEN/MOCs/ANIMATION\|ANIMATION]] 3D c’est l’ordinateur qui fait les interpolations.

Grossomodo, on pense posing puis [[3_GARDEN/Notes permanentes/Timing\|Timing]], puis [[3_GARDEN/Notes permanentes/Spacing\|Spacing]]

</div></div>
 

## Timing et spacing


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Timing/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note


<iframe width="560" height="315" src="https://www.youtube.com/embed/BarOk2p38LQ?si=cpZ6RTlt-ShPbrpr" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> 


Le [[3_GARDEN/Notes permanentes/Timing\|Timing]] comme le [[3_GARDEN/Notes permanentes/Spacing\|Spacing]] désignent tous les deux le comportement des keyframes dans le temps.

Le timing c’est le rythme (rapidité de l’enchaînement des keys) : plutôt à l'étape du blocking : [[3_GARDEN/Notes permanentes/Process d'animation\|Blocking d'animation]]
La plupart des vidéos en animation sont en 24 images par seconde. Plus l’on dessinera d’images pour une même action, plus cette dernière sera longue. A contrario, moins il y aura d’images et plus l’action sera rapide. La durée d’une action lui confère du sens. 

**Ce qui est bien c'est d'alterner entre deux temps rapides et lents**.


</div></div>
 