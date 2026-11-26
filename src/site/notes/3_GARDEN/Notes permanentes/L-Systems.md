---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/L-Systems/","tags":["note_permanente","plante"],"ctime":"2026-06-06T15:58:55.205+02:00","mtime":"2026-06-06T17:48:32.235+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/PROCEDURAL MODELING]]"],"source":null,"Projets":null,"tags":["note_permanente","plante"],"creation date":"2026-06-06","aliases":null}}
---

## La note 



> [!NOTE]+ Symboles principaux
> F : Aller en avant
> `+` : Angle à droite
> `-` : Angle à gauche
> [] : Branches
>  / : enroulement autour d'un axe
>  & : Courbure vers le haut
>  ^ : Angle vers le bat
> () : Valeur précise d'un paramètre. Par exemple après un + ou - ou / : dire précisément de manière absolue quelle est la valeur de l'angle en degrés. Après un F : longueur du segment
> ! : Baisser progressivement la thickness en tube mode
> ~ : Ajouter de l'aléatoire
>

Exemple : 

`FF[+(90)FF-(90)F]FF` 

![](https://i.imgur.com/Y9n0pvF.png)

Premise : là où on définit le pattern du L-System

#### Rules

Pour créer des systèmes plus complexes on peut utiliser des sortes de fonctions avec par exemple A,B ou C que l'on définit dans les rules: 

![Capture d'écran 2026-06-06 161105.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-06-06%20161105.png)

#### Generation

Un des concepts les plus puissants des L-System : permet de contrôler la "croissance" du L-System (si on crée une plante, la croissance de la plante)

On peut également appeler la variable dans la variable ce qui crée une boucle contrôlée par le paramètre generation (onglet geometry)
`A = F+F[+F]A` par exemple

#### Ajouter des feuilles, fleurs etc


Les 3 permières entrées du node permettent d'attribuer de la géo externe à des lettres dans le pattern L-System. 
Les lettres sont respectivement : J, K, M

#### Variables

b, c et d sont des variables qui peuvent prendre une valeur précise à définir dans l'onglet values
On peut par exemple remplacer un F(20) par F(b) et ainsi changer la valeur avec un slider dans l'onglet values
#### Exemples

Plante ultra basique : 

![](https://i.imgur.com/q1SQcDm.png)

Plante basique (mais plus complexe) : 

![Capture d'écran 2026-06-06 165415.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-06-06%20165415.png)

![Capture d'écran 2026-06-06 173819.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-06-06%20173819.png)


## Références

Doc : [L-System](https://www.sidefx.com/docs/houdini/nodes/sop/lsystem.html)

Vidéo de sideFX qui explique très bien : 

[Magic Market \| L-Systems \| Vidéos et films sur Vimeo](https://vimeo.com/485638368?fl=pl&fe=sh)

> [!example]- Flashcards
> ...




## Liens 




