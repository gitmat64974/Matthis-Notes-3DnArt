---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Primitive USD/","tags":["note_permanente"],"ctime":"2026-11-23T23:11:45.118+01:00","mtime":"2026-11-23T23:12:37.522+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-23","aliases":null}}
---

## La note 

Presque tous les objets ajoutés à notre scène USD sont considérés comme des « primitives ». Il peut s'agir notamment d'objets tels que : des lumières, des géométries, des caméras, des shaders et des paramètres de rendu. En bref, tout ce que nous ajoutons à notre scène.

#### Types de Primitives

Les types de primitives définissent ce qu'est une primitive. Cette définition donne au logiciel USD une idée concrète de l'utilisation qui sera faite de cette primitive. Quelques exemples : `Mesh` (Maillage), `Light` (Lumière), `OpenVDB`, `Render Settings` (Paramètres de rendu) et `Point Instancer` (Instanceur de points).
#### Primitive Feuille (_Leaf Primitive_)

Une primitive feuille est l'extrémité d'une branche dans l'arbre du graphe de scène. Une autre façon de le décrire est qu'elle ne possède aucune primitive enfant.
#### `Kind` (Catégorie) de Primitive

Le `Kind` est une méthode permettant de définir la hiérarchie des primitives.

- **Assembly** (Assemblage)
    - Un groupe important.
    - Généralement un _asset_ (ressource) publié ou une référence à celui-ci.
    - Peut contenir des composants, des groupes ou des assemblages.
- **Group** (Groupe)
    - Peut contenir des composants, des groupes ou des assemblages.
- **Component** (Composant)
    - Ne peut pas contenir de groupes ou d'assemblages.
    - Peut uniquement contenir des sous-composants.
- **Subcomponent** (Sous-composant)
    - Une primitive « importante » à l'intérieur d'un composant (ex. : un pivot de porte).

##### Exemple de hiérarchie

Une hiérarchie dans l'arbre du graphe de scène pourrait ressembler à ce qui suit :

```
/Models ← group
  /Characters ← group
    /Lady ← assembly
      /Skin ← component
        /mesh
      /Purse ← component
        /mesh
    /Dog ← assembly
      /Skin ← component
        /mesh
      /Collar ← component
        /mesh
/Props ← group
```

  

## Références


> [!example]- Flashcards
> ...




## Liens 




