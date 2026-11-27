---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Importer une caméra - Houdini/","tags":["note_permanente"],"ctime":"2026-11-03T23:49:26.071+01:00","mtime":"2026-11-10T21:12:10.194+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/SOLARIS|Solaris]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-03","aliases":null}}
---

## La note 

Pour importer une cam dans le context obj : 
File -> Import -> FilmBox FBX 

#### Workflow usd maya to houdini Solaris

1. Exporter la cam de maya en usd
2. Dans Solaris, créer une primitive qui sera la parente de toutes les cams, comme par exemple `/cameras`
3. Ensuite mettre un transform en uniform scale 0.01 sur cette primitive
4. Ensuite référencer la cam avec un reference LOP et la ranger dans la primitive parente -> la cam sera ainsi à la bonne scale



## Références

- [Houdini \| Import Animated FBX Camera with Proper Transforms (for simple camera movement) - YouTube](https://youtu.be/sDk2JBDoXi4)

> [!example]- Flashcards
> ...




## Liens 




