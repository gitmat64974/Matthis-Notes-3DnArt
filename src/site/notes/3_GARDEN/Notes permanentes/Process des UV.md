---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Process des UV/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.413+01:00","mtime":"2026-04-24T17:43:18.929+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/MODELISATION]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":["[[4e cours de lighting esma 3d1a]] / [[Cours lighting UV, esma 3d1a, Monsieur Rongeart]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2023-10-27","aliases":["De bons UVs"]}}
---


## La note

*UV editor : windows -> modeling editors* 

1. Supprimer les UVs existants puis UV toolkit (dans l’UV editor) -> create -> camera based
2. Sélectionner les edge loop (double clic sur une edge en mode edge)
3. Cut : Faire les découpes UV là où il y a des changements de direction, et pour avoir le moins de tensions possible (*on peut afficher les tensions en cliquant sur l'icone "UV distorsion", pour afficher les zones de compression en rouge et de dilatation en bleu*), essayer de faire en sorte que les cut soient aux endroits les moins visibles
4. Unfold : ctrl u en sélectionnant toutes les faces
5. Réorganiser selon les [[3_GARDEN/Notes permanentes/4 lois des UV\|4 lois des UV]] (par ex : Connecter dans les UV deux mêmes edge qui sont dépliées donc éloignées : stitch together), faire orient shells puis layout (layout automatique)
6. Delete history (alt +shift + D)
7. Appliquer une texture

#### Des bons UVs :

- globalement peu de déformation
- Limite les coutures et les cacher au maximum
- Éviter les overlap sauf si c’est voulu
- Éviter les UVs inverses : on aura des textures inversées comme bump (peut être la displace). On les voit si le texte est inversé ou si on est en shaded dans l’uv editor et que c’est rouge.
- On cut là où il y a changement de direction (par exemple la où il y a les étoiles)

## Références 

Voir aussi : [[3_GARDEN/Notes permanentes/UDIM's\|UDIM's]]

## Liens 