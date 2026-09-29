---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX Graph/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[RIG]]","[[RIG HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 

Pour voir le graph APEX on peut mettre un node apex graph après tout le setup d'autorig builder et ou components et ouvrir le APEX Network view panel

Nous voilà dans le node editor de MAYA ! 

#### Exemple : faire un lookat custom 

Le lookat custom qu'on va faire est un ajout par dessus le component lookat de base
On va ajouter un controleur lookat qui influence les deux yeux et un blend entre ce lookat et les deux autres individuels 

Le graph : 

![Capture d'écran 2026-09-26 140408.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-26%20140408.png)

- Both eyes target : Le controleur de lookat 
- Both eyes look blend : Le controleur de blend

*On branch le t et le x des controleurs au gros node parameters pour qu'ils soient considérés comme de nouveaux controls sur le rig*

#### Fuse graph

Comment appliquer au rig les changements que l'on a fait dans le graph ? 

Dans le graph selectionner tous les nodes que l'on a pas touché -> clic droit -> edit tags -> ajouter un tag et l'appeler REFERENCE

Ensuite dans le node graph SOP ajouter un autorig component en mode fuse graph et brancher le graph dans la 2e entrée

![Capture d'écran 2026-09-26 140028.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-26%20140028.png)





## Références


> [!example]- Flashcards
> ...




## Liens 




