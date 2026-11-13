---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Freeze une frame spécifique - KineFX - Houdini/","tags":["note_permanente"],"ctime":"2026-11-13T12:50:11.462+01:00","mtime":"2026-11-13T12:50:42.188+01:00","dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-13","aliases":null}}
---

## La note 


- Ajoutez un nœud **Retime** après votre animation.
    
- Dans le paramètre **Condition**, choisissez **By Frame**.
    
- Allez à la **frame 1** sur votre timeline, mettez la valeur `1` dans le paramètre _Frame_ du Retime, et faites **Alt + Clic gauche** dessus pour poser une clé (le fond devient vert).
    
- Allez à la **frame 30**, entrez la valeur `30` et posez une clé (Alt + Clic).
    
- Allez à la **frame 40**, laissez la valeur à `30` et posez une clé.
    
- Allez à la **frame 41**, mettez la valeur à `31` et posez une clé.
    
- Faites un **Shift + Clic gauche** sur le paramètre _Frame_ pour ouvrir l'Animation Editor (Graph). Sélectionnez toutes vos clés et passez-les en interpolation **Linear** (l'icône de ligne droite en haut) pour que la vitesse de lecture soit constante avant et après la pause.

## Références


> [!example]- Flashcards
> ...




## Liens 




