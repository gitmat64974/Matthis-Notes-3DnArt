---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/9e cours CFX/","tags":["note_litteraire","cours"],"ctime":"2026-03-22T12:15:21.089+01:00","mtime":"2026-07-17T16:36:12.932+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/CFX]]","[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2026-01-09"}}
---



## Queue de cheval groom houdini



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

Le workflow est de créer une curve qui sera la forme de base, de lui donner de la geometrie avec un sweep, de créer des curves supplémentaires

Sweep : 
- Cocher apply scale along curve et dessiner la shape

![](https://i.imgur.com/BZFTipM.png)

Changer ensuite le surface type en points 

Ensuite wrangle : 
Le but est de créer un attribut par "futurs" guides

On va utiliser le modulo (formule mathématique qui renvoi le reste d'une division) : %

```C
i@class = @ptnum % 8;
```

Ce petit code va donc créer des classes pour chaque curve

Ensuite foreach avec comme entrée l'attribut class créé avec le wrangle
Dans le foreach faire un add pour créer une curve avec les points
- by group
- On peut ajouter un resample ensuite en treat polygon as subdiv


![](https://i.imgur.com/Dgj1aAK.png)


Enfin ajouter un guideskinattriblookup : 
Ce node va donner tous les attributs nécessaires pour que les curves soient considérées comme guides
Mettre en 2e input une geo qui sera la base des cheveux, le scalp



</div></div>
  





