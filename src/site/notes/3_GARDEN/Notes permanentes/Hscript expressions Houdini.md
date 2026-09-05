---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Hscript expressions Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-04","aliases":null}}
---

## La note 

Les incontournables : 

|Besoin|Expression|Exemple|
|---|---|---|
|Frame courante|`$F`|`$F * 0.1`|
|Frame avec sous-décimales|`$FF`|utile en motion blur|
|Temps en secondes|`$T`|`sin($T * 2)`|
|Nombre aléatoire 0-1|`rand(seed)`|`rand($F)`|
|Remapper une plage|`fit(val, old_min, old_max, new_min, new_max)`|`fit(rand($F),0,1,2,8)`|
|Remapper depuis 0-1|`fit01(val, new_min, new_max)`|`fit01(rand($PT),1,5)`|
|Lire un autre paramètre|`ch("chemin/param")`|`ch("../grid1/sizex")`|
|Lire un paramètre texte|`chs("chemin/param")`|`chs("../switch1/input")`|
|Lire une rampe|`chramp("nom", position)`|`chramp("colorramp", $PT/($NPT-1))`|
|Borner une valeur|`clamp(val, min, max)`|`clamp($F,1,100)`|
|Valeur d'un attribut de point|`point(surface, ptnum, "attrib", comp)`|`point(0,$PT,"P",1)`|


#### Bounding box

``bbox("../node", D_YSIZE)``

Il y a 9 types différents : X, Y, Z _ MIN, MAX, SIZE -> ex ``D_XMIN`` ou ``D_YMAX`` ou ``D_ZSIZE`` etc
-> Min et max sont des plans donc des positions et pas des calculs de longueur comme size

#### Variables globales de lecture

|Variable|Équivalent VEX (`@`)|Description|
|---|---|---|
|`$F`|—|Frame courante (entier). La plus utilisée, notamment pour numéroter des rendus.|
|`$FF`|`@Frame`|Frame courante en virgule flottante (précis, utile en sous-frame / motion blur).|
|`$T`|`@Time`|Temps courant en secondes = `($F-1)/$FPS`.|
|`$FPS`|—|Images par seconde définies dans la barre de lecture.|
|`$FSTART` / `$FEND`|—|Première / dernière frame de l'animation.|
|`$NFRAMES`|—|Nombre total de frames = `$FEND - $FSTART + 1`.|
|`$TSTART` / `$TEND` / `$TLENGTH`|

#### Référencement de canaux

- `ch()` → renvoie un nombre (int/float).
- `chs()` → renvoie une chaîne de caractères.
- `chramp()` → renvoie la valeur d'un paramètre rampe à une position donnée (0 à 1).

Clic droit sur le paramètre source → _Copy Parameter_, puis clic droit sur le paramètre cible → _Paste Relative Reference_ : Houdini écrit le `ch("...")` correct tout seul.

#### Nombres aléatoires et remapping 


```text
rand(seed)          # nombre pseudo-aléatoire entre 0 et 1
rand($F)            # change à chaque frame
rand($PT)           # change à chaque point (dans un Point SOP)
rand($PT * 10)      # une autre valeur aléatoire décorrélée de la précédente
```

`rand()` renvoie toujours le même nombre pour la même seed. Pour avoir des valeurs différentes par point/frame/canal, il faut varier la seed (multiplier, additionner un offset...).
```text
# Couleur aléatoire différente par primitive, stable dans le temps
rand($PR)            # Rouge
rand($PR * 10)        # Vert
rand($PR * 100)       # Bleu
```

Remapper une plage 0-1 vers autre chose :

```text
fit01(rand($F), 2, 8)          # aléatoire entre 2 et 8
fit10(0.3, 5, 20)               # inverse le sens : 15.5
fit(3, 1, 4, 5, 20)              # remapping général : 15
```

Pour une plage symétrique -X à X : `rand(seed) * (2*X) - X`.


## Références


> [!example]- Flashcards
> ...




## Liens 




