---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Flipbook Houdini/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.207+01:00","mtime":"2026-09-26T19:30:53.742+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours Houdini semaine 3]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510132311,"aliases":null}}
---

## La note 

*Rappels : Pour créer une clé d’animation : Alt-LMB sur un paramètre*

##### 1. Calculer le filpbook

À l’aide d’un _RMB_ sur l’icône de carnet située en bas à gauche du _Viewport_, cliquer sur _Flipbook with New Settings_ pour ouvrir la fenêtre _Render Flipbook_. Dans celle-ci :
- Onglet _**Size**_ :
    - _Resolution_ = `1920` x `1080`
- Cliquer sur le bouton **`Start`** pour lancer le calcul d’un _Flip Book_ (équivalent à un _playblast_ de Maya).

Une nouvelle application s’ouvre, le _MPlay_, qui concatène les images. 

##### 2. Exporter le flipbook

Une fois le calcul terminé, ouvrir le menu _File_, et choisir _Export / FFmpeg_ :
- _Output File_ : Choisir un chemin et un nom de fichier, en conservant bien l’extension .mp4 à la fin.
- _Quality =_ 100
- Cliquer sur **`Save`**.

----

### Faire un Flipbook en max res 

Il ne faut pas passer par le viewport mais par le context out et là on crée un node flipbook. Tout fonctionne pareil avec des paramètres en plus et la résolution pourra ici enfin être au max

## Références


> [!example]- Flashcards
> ...




## Liens 
