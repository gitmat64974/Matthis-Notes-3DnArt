---
{"dg-publish":true,"permalink":"/0_INBOX/VEX - cas concrets utiles/","dg-note-properties":{}}
---


## Récupérer la position d'un point du deuxième input


```C
vector pos_input2 = point(1, "P", @ptnum);
```

**Détail des arguments de la fonction `point(input, attribut, numéro_du_point)` :**

- `1` : L'index du deuxième input.
- `"P"` : Le nom de l'attribut à récupérer (la position). Il faut toujours le mettre entre guillemets.
- `@ptnum` : Le numéro du point.


## Faire des vagues simples

Sur une grid : 
```C
 float d = length(@P);
 d *= ch('v_scale');
 d += @Time;
 @P.y = sin(d);
```

Pour que ça marche sur tout autre objet : 
*Le principe est d'ajouter à la position la normale des points : exactement ce que fait le peak sop, ça gonfle* 

```C
@P += @N * ch('push');
```

Donc pour les vagues : 

```C
 float d = length(@P);
 d *= ch('v_scale');
 d += @Time;
 @P += @N*sin(d) *ch('wave_height');
```