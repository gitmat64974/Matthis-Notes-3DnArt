---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Setup une géo pour l'USD avec Solaris/","tags":["note_permanente"],"ctime":"2026-11-25T23:23:29.039+01:00","mtime":"2026-11-25T23:36:03.728+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-25","aliases":null}}
---

## La note 

![Capture d'écran 2026-11-25 232458.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-25%20232458.png)

Ici 3 cas d'import sont montrés : géo qui vient d'un usd, d'un fbx ou d'un alembic

Les choses les plus importantes à faire attention : 
- Scale et placement de l'objet dans la scène
- Naming

#### Détail

Scale confo : 
- Transform en uniform scale à 0.01

Attribute delete : 
- Delete non selected : P, N, uv, name, path

Match size : 
- Justify Y : Min

#### Détail des wrangles

Pour l'usd : 

*On vient juste enlever la dernière partie du path, car elle correspond au name, pour ne pas faire de doublons*

```C
string parts[] = split(s@path, "/");

if (len(parts) > 0)
{
    pop(parts);
    s@path = "/" + join(parts, "/");
}
```

Pour le FBX : 

*On vient faire correspondre le path au name puis on garde uniquement la dernière partie du path pour le name*

```C
s@path = "/" + s@name;

string parts[] = split(s@path, "/");
if (len(parts) > 0)
{
    s@name = parts[-1];
}
s@path = re_replace(r"/[^/]+$", "", s@path);
```


## Références


> [!example]- Flashcards
> ...




## Liens 




