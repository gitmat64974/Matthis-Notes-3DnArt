---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Boolean Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours Houdini semaine 14]]"],"Projets":null,"tags":["note_permanente"],"creation date":202601230907,"aliases":null}}
---

## La note 

Les faces originelles gardent leurs attributs mais les faces crées prennent les attributs de la geo B

C’est donc un objet un peu “hybride”, où la geometrie n’est pas très propre

#### Resolve selft intersection :

En cochant cela le boolean vient fusionner les intersections, ce qui souvent n’est pas souhaitable

#### Rendre un boolean plus propre :

On peut utiliser un foreach pour traiter chaque primitive séparément

##### Node connectivity : 

Il vient créer un attribut class de type entier qui prendra des valeurs (0,1,2 etc) pour chaque geometrie connectée

---


## Références


> [!example]- Flashcards
> ...




## Liens 
