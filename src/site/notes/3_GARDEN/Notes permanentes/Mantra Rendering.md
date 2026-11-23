---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Mantra Rendering/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:37.912+01:00","mtime":"2026-03-30T20:32:07.373+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":["https://irendering.net/render-quality-and-speed-in-houdini-with-mantra-renderer/","https://www.sidefx.com/docs/houdini/render/render.html"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-12-22","aliases":null}}
---


---

## La note 

[How to render using Mantra](https://www.sidefx.com/docs/houdini/render/render.html)

Mantra est le moteur de rendu avancé intégré à Houdini qui peut utiliser différentes technologie de rendu comme le raytracing, le scanline, le micropolygon rendering (voir plus bas dans références) ou le PBR (c'est celui ci qui est priorisé).
Il permet notamment un rendu efficace des primitives packées et des volumes

tips : *Vous pouvez ajouter des propriétés d'échantillonnage à un objet pour obtenir des réglages de pixels distincts par objet*

---
### Paramètres de sampling : définir la précision


L'onglet **Rendering ▸ Sampling** est le centre de contrôle principal pour équilibrer la qualité d'image et le temps de calcul.

##### Pixel Samples : La base globale

Le paramètre `Pixel Samples` définit la qualité de base de toute l'image. C'est le nombre minimal de rayons lancés pour rendre chaque pixel.

- **Valeurs recommandées :** 
    - $3 \times 3$ à $4 \times 4$ : Tests et prévisualisations.
	- $5 \times 5$ à $6 \times 6$ : Standard pour la plupart des rendus.
	- $12 \times 12$ : Limite max pour les scènes très complexes (flou de mouvement intense, profondeur de champ, beaucoup de [[3_GARDEN/Notes permanentes/Displace\|Displace]] etc).

tips : *Exporter un [[3_GARDEN/Notes permanentes/AOV\|AOV]] qui montre la quantité de rayons lancés pour chaque pixel*

##### Ray Variance Anti-Aliasing (RVAA)

Une fois les Pixel Samples définis  on utilise l'échantillonnage adaptatif pour traiter les zones problématiques.

**Le principe :** Mantra boucle et lance des rayons supplémentaires jusqu'à ce que le **Noise Level** (seuil de bruit) soit atteint ou que le nombre **Max Ray Samples** soit épuisé.

**Rendering ▸ Dicing ▸ Shading quality multiplier** contrôle le niveau de raffinement. En PBR et en _raytracing_, cela peut augmenter la fidélité des détails géométriques très fins

Tips : *Lumière indirecte : ajoutez une Indirect light et augmentez la Diffuse limit (mais pas au dessus de 4)*

---

### Réduire le noise

Le bruit varie grandement selon la résolution : La même quantité de bruit qui semble mauvaise en 640×400 ne sera probablement pas perceptible en 2K
*Notez que le grain d'un film analogique correspond probablement à un niveau de bruit d'environ 0,08*

**Le paramètre principal est le ***Noise level***

Attention diminuer le niveau de bruit rend le rendu beaucoup plus lent

Tip : *Si vous avez des points brillants (speckles) dans vos rendus PBR, essayez de diminuer le **Color limit** dans l'onglet Rendering ▸ Limits. Cela réduit la quantité maximale de lumière autorisée dans le système.*

---

### Gestion de la mémoire

Utilisez des shaders procéduraux tels que le _Delayed Load_ de Mantra et la géométrie _Alembic_ pour remplacer la géométrie proxy par une géométrie plus complexe au moment du rendu. Effectuez le rendu de la géométrie en pleine résolution au format d'archive Mantra ou au format Alembic pour permettre à Mantra de charger à la demande de petites parties du fichier géométrique à la fois

---

### Divers tips d'optimisation

Par défaut, Houdini utilise tous les processeurs pour accélérer le temps de rendu. Si vous ne souhaitez pas utiliser la totalité des processeurs, vous pouvez décocher la case **Use Max Processors** dans le sous-onglet **Render** de l'onglet **Rendering** du nœud de rendu. Une fois cette option désactivée, vous pouvez régler le **Thread Count** pour spécifier le nombre de processeurs à utiliser.

Réduire le **Volume Step Rate** (situé dans le sous-onglet **Rendering ▸ Sampling** du nœud Mantra) accélère le rendu mais diminue la capacité de Mantra à résoudre les détails fins dans les volumes.

De plus, réduire le nombre de lumières qui génèrent et utilisent des cartes d'ombres profondes (_deep shadow maps_) accélérera également le rendu. Les ombres profondes apportent de la profondeur, il est donc conseillé de n'avoir qu'une ou deux lumières avec cette option activée, et de désactiver les ombres pour le reste des lumières.

L'utilisation de l'**Environment Light** avec vos objets volumétriques ralentira votre rendu de volume, car chaque micropolygone ombré générera un nombre très important de rayons à cause de l'occlusion ambiante calculée par lancer de rayons (_raytraced AO_). Contrôler manuellement les lumières vous offrira plus de contrôle et sera moins coûteux.

Pour les lumières qui n'affectent qu'une partie de la scène, il est possible d'accélérer les rendus en activant le paramètre **Active Radius** sur l'objet lumière et en le réglant sur le rayon d'effet maximum de cette source. Lorsque les shaders sont exécutés en dehors de ce rayon actif, ils ignorent entièrement cette lumière, ce qui améliore les performances. Cette option est particulièrement utile pour les scènes comportant de nombreuses petites sources lumineuses, comme une rue avec de nombreux lampadaires.

Lorsque vous effectuez le rendu d'une géométrie avec une certaine transparence, vous pouvez utiliser la limite d'opacité pour arrêter le rayon actuel si le seuil d'opacité est atteint. Le paramètre **Opacity Limit** est situé dans le sous-onglet **Limits** de l'onglet **Rendering** du nœud de sortie Mantra.
En modifiant l'**Opacity Limit**, vous n'obtiendrez qu'une diminution de 1 à 5 % du temps de rendu. La valeur par défaut est déjà assez agressive, soyez donc prudent pour éviter l'apparition d'artefacts indésirables.

Mantra optimise spécifiquement les performances de rendu (tant en lancer de rayons qu'en rendu par micropolygones) pour les shaders qu'il sait être totalement opaques. Pour améliorer les performances, assurez-vous que les shaders opaques attribuent soit une constante `{1,1,1}` à la variable VEX d'opacité (**Of**), soit que tous les paramètres du shader ou du matériau qui pourraient rendre le shader transparent soient désactivés.

Utilisez le flou de mouvement par vélocité (_velocity motion blur_) au lieu du flou de déformation pour réduire le temps de génération et la taille du fichier IFD.

---


## Références

**Micropolygon Rendering :** Divise la géométrie en minuscules polygones au moment du rendu. Historiquement utilisé pour les Displace massives et les effets de cheveux/fourrure anciens.

> [!example]- Flashcards
> ...




## Liens 




