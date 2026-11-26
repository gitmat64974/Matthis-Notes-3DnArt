---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/ASWF/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.672+01:00","mtime":"2026-11-26T11:01:24.332+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

[assets/docs/asset-structure-guidelines.md at main · usd-wg/assets · GitHub](https://github.com/usd-wg/assets/blob/main/docs/asset-structure-guidelines.md)

#### Terminologie des assets USD

- Les assets sont appelés **models** dans USD
- Les **Components** sont des assets publiables qui gardent leur géométrie derrière un payload
- Les **Assembly** sont des assets publiables qui référencent des composants ou d'autres assets d'assemblage
- *Les components et assembly publiés doivent hériter d'une primitive de class*

#### USD Component primitive

- Un component est l'asset le plus basique publié dans un pipeline USD
    - Le type (kind) de component sur la primitive racine ("xform") du modèle, est définie comme defaultPrim du fichier racine de l'asset
    - Le payload rend la géométrie différable
    - Autonome/Portable, aucune référence à une géométrie ou des modèles externes
    - Hérite d'au moins une primitive class 

Component : 

![Capture d'écran 2026-10-22 155416.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-22%20155416.png)

#### USD Assembly primitive

- un asset publié qui référence d'autres components ou assembly
- les xforms intermédiaires utilisent le type groupe (group kind)
- Les payload n'offrent pas d'avantages lorsqu'ils existent au sein des composants
    - cela peut compliquer le chargement/déchargement des scènes, et ajouter une surcharge supplémentaire

Assembly simple : 

![Capture d'écran 2026-10-22 172844.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-22%20172844.png)

Assembly simple avec matériaux et nouvelle géométrie : 

- On peut remplacer les matériaux sur des components par des matériaux dans le scope "mtl"
- lorsqu'une nouvelle géométrie est nécessaire, la stocker derrière un payload et lui attribuer le type (kind) composant

Variant Layers : 

![](https://i.imgur.com/5xfyZLY.png)

### Recommended asset structure - Geo Setup

Hiérarchie : 

```
- HiRes_Pig (component)
  - geo (scope)
	- render (scope)
    - proxy (scope)
  - simproxy (scope)
```

Ensuite setup le usd purpose pour chaque géo (voir [[3_GARDEN/Notes permanentes/USD Purpose\|USD Purpose]]) 

### Recommended asset structure - Material Setup

Nodes : 
1. **Layer break** avant d'assign un matériau pour éviter qu'il y ait de la géo dans le layer du matériau
2. **Material library** : on crée les matériaux
3. **Assign Material** : On assigne les matériaux 
4. **Configure layer** : si besoin d'exporter proprement uniquement les matériaux en usd

Où le placer dans le stage : ``<nom-de-l'asset>/mtl/<shader-name>``

*A noter que par défaut le mat library crée aussi pour chaque shader un shader de preview appelé usd preview surface. Ce shader sera celui utilisé dans le viewport*




## Références


> [!example]- Flashcards
> ...




## Liens 




