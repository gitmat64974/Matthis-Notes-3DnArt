---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/VEX/","tags":["note_permanente","en_cours"],"ctime":"2026-03-21T20:44:26.967+01:00","mtime":"2026-11-15T00:33:08.661+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/INFORMATIQUE]]","[[3_GARDEN/MOCs/PROGRAMMATION INFORMATIQUE]]"],"source":["https://tokeru.com/cgwiki/JoyOfVex.html"],"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2025-12-11","aliases":null}}
---

## La note 

Le VEX est le langage de programmation d'Houdini, dérivé du langage C. 

Source principale : [Joy of Vex - Houdini and CG tips](https://tokeru.com/cgwiki/JoyOfVex.html)

### Les bases

Manipuler la couleur : 

```C
@Cd = @N;
```

```c 
 @Cd = @P.x;
```

> [!tip]+ Afficher un ramp en fonction du numéro des points 
> 
> *on définit un float pour pouvoir gérer les nombres à virgules et on divise par 100 (ou par le nb total de points : @numpt) par avoir des valeurs comprises entre 0 et 1*
> 
> ```C
>  @Cd = float(@ptnum)/100;
> ```
> 

Ecrire les coordonnées d'un vecteur simple : {0,1,0}

### Variables et attributs : 

- Les attributs (données stockées sur la géométrie) sont précédés d'un @
- Variables : elle existent uniquement dans le wrangle, on dit qu'elles sont locales

#### Manipulation de variables 

Définir une variable locale : "type de valeur" "nom variable" = 
Par exemple : float attraction =

Souvent on utilise une variable en locale lors du développement du code, puis une fois que le code est validée, la variable est "transférée" sur un attribut pour "fixer" les changements dans la géométrie

Par exemple 

```C
float foo = @P.x/ch('scale');
@Cd = sin(foo);
```


### Channels

La fonction channel permet de créer une variable locale dont la valeur peut être modifiée par une tirette dans le node wrangle 
La fonction : `ch('');`

![](https://tokeru.com/cgwiki/assets/Joyofvex1_ch.65aff369.gif)

```C
 @Cd = float(@ptnum)/ch('scale');
```

A noter qu'ajouter une lettre après ch permet de définir un channel d'un certain type de valeur : 
- chf : channel float
- chv : channel vector
- chi : channel integer
- etc

#### Chramp

Ce sont des channels mais en ramp : 

![](https://tokeru.com/cgwiki/assets/Ramp_default.CCBcMdnV.gif)

Comment ça s'utilise dans le code :
```C
@P.y = chramp('myramp',d);
```
-> *Comme un channel sauf qu'on spécifie en plus ce qui va être utilisé pour l'axe x (ici `d`)*

---
### Fonctions VEX

#### Fonctions basiques 

> [!node] Sin
> `sin()` : mouvement sinusoïdale qui oscille entre -1 et 1 
> Pour changer la vitesse d'oscillation, mettre un ch (ou un nombre fixe) en multiplication ou division dans la fonction sin

*Comme vex est destiné aux geeks, sin utilise des radians, ce qui signifie qu'il effectue un cycle de 0 à 1, puis de 0 à -1, puis de -1 à 0 toutes les pi2 unités.*

Une liste de toutes les fonctions en VEX : [VEX Functions](https://www.sidefx.com/docs/houdini/vex/functions/index.html) (Il y en a beaucoup !)

> [!length()]
> Cette fonction retourne la longueur d'un vecteur (ou autre)
> ` float d = length(@P);` (-> Appliqué à P cela va donner la distance de chaque point à l'origine). 

Exemple avec la position pour faire des vagues : 

> [!multi-column]
> 
> > [!blank]
> > ![](https://tokeru.com/cgwiki/assets/Joyofvex2_sin1.43315e06.gif)
> 
> > [!blank]
> > 
> > ```C
> >  float d = length(@P);
> >  d *= ch('scale');
> >  @Cd = sin(d);
> > ```
> > 
> > 
> 
> 


> [!node] distance()
> Cette fonction mesure la distance entre un point et une position donnée : 
> ``distance(@P, {1,0,3} );``
> 
> *Remplacer lenght par distance dans l'exemple précédent des vagues permet donc donner un point d'origine précis aux vagues plutôt que l'origine du monde*


> [!NOTE]+ Fit
> C'est l'équivalent d'un remap
> You tell it the incoming min and max values ( -1 and 1 par exemple pour une fonction sin), and the new min and max values you want (0 and 1).
> Ex : ``@Cd = fit(sin(d),-1,1,0,1);``

#### Modulo et quantisation

[[3_GARDEN/Notes permanentes/Modulo\|Modulo]] 

[[3_GARDEN/Notes permanentes/Quantisation\|Quantisation]] 


### Attributs

[[3_GARDEN/Notes permanentes/Attributs Houdini\|Attributs Houdini]]

### Utiliser d'autres géos pour modifier celle qu'on traite

C'est l'utilité des autres input dans un wrangle

#### Fonction minpos

C'est l'équivalent d'un ray : on donne une position du monde et une géo et ça retourne la position sur la géo la plus proche de la position du monde

Donc on donne à la fonction la géo d'influence et sur quel point on veut calculer cette distance (si on veut sur tous : @P)
Donc en général si la géo d'influence est le second input, la fonction s'utilise comme ça : ``vector pos = minpos(1, @P); ``

On l'utilise souvent avec la fonction distance qui permettra de créer une sorte de falloff autour de la "projection" de l'objet

```C
vector pos = minpos(1, @P);
@dist = distance(@P, pos) * chf('falloff');
```

![](https://i.imgur.com/o6VjW9p.png)

#### Fonction nearpoint

[[3_GARDEN/Notes permanentes/Fonction nearpoint VEX\|Fonction nearpoint VEX]]

#### Fonction point

`point()` 

Elle permet de ***récupérer un attribut situé sur les points d'une géo en entrée***
paramètres : (géométrie d'entrée (0 pour la première entrée, 1 pour la deuxième entrée etc), le nom de l'attribut ("orient" par exemple), le point sur lequel regarder l'attribut (0 pour seulement le point 0, ou ptnum pour tous les points))


> [!tip] raccourci fonction point
> A noter que si les deux géos en entrée du wrangle on exactement le même ptnum, on peut remplacer la fonction point() par @opinput1_P (-> *input 1 et on récupère la position*)


> [!example]+ Example : pluie en utilsant les fonction nearpoint, point et distance
> 
> ![](https://tokeru.com/cgwiki/assets/Ripples.d_jIud9b.gif)
> 
> Scatter 8 points en second input du wrangle
> 
> ```C
>  int pt = nearpoint(1,@P);
>  vector pos = point(1,'P',pt);
>  float d = distance(@P, pos);
>  d *= ch('scale');
>  d += rand(pt);
>  d -= @Time;
>  d %= 1;
>  @P.y = chramp('pulse',d)*ch('amp');
> ```
> 

### Noises

```C
 @Cd = noise(@P);
```

To change the scale of noise, multiply @P by a factor:

```C
 @Cd = noise(@P*ch('scale'));
```

Or if you want non-linear noise, multiply it by a vector:

```C
 @Cd = noise(@P*chv('fancyscale'));
```

If you want to move noise around, add an offset:

```C
 @Cd = noise(@P+chv('offset'));
```

Or if you want it animated, give it an animating value, like @Time:

```C
 @Cd = noise(@P+@Time);
```

Or combine all those things:

```C
  @Cd = noise(chv('offset')+@P*chv('fancyscale')+@Time);
```

![](https://tokeru.com/cgwiki/assets/Joyofvex8_noise.i3TwuznC.gif)

Houdini offers quite a few types of noise, a common alternative is curlnoise:

```C
  @Cd = curlnoise(@P*chv('fancyscale')+@Time);
```

While most formats of noise will be happy with a single input, the more advanced noise types take lots of inputs to control their behavior. Eg, this is the help definition for pnoise:

```C
 pnoise(vector4 xyzt, int px, int py, int pz, int pt);
```

Dans ces situations, surtout si vous souhaitez tester rapidement différents types de bruit, les vops peuvent constituer l’option la plus rapide. Vous pourriez vouloir combiner du bruit avec des motifs, ou mener des expériences plus libres avec les attributs de noise

---
### Dot product 

*Produit scalaire*

Il compare les directions des vecteurs : s'ils pointent dans la même direction (c'est-à-dire s'ils sont parallèles), elle renvoie 1 ; s'ils sont perpendiculaires, 0 ; s'ils pointent exactement dans des directions opposées, -1 ; et pour les angles situés entre ces positions extrêmes, la valeur varie progressivement entre 1, 0 et -1.

> [!example]+ Exemple : le lighting 
> 
> ```C
>  @Cd = @N.y;
> ```
> 
> Ce petit code va donner l'impression que la géo est lightée depuis le haut
> Maintenant si on utilise un angle qu'on définit nous même, on va pouvoir utiliser le dot product : 
> 
> ```C
>  @Cd = dot(@N, chv('angle'));
> ```
> Si on veut controler la "light" depuis un point, c'est très simple, on branche un point (add sop) dans la deuxième entrée d'un wrangle et on récupère sa position. Cette position sera le point de comparaison du dot product avec la normal. On n'oublie pas de normalizer la position car la normale est bien normalizée :
> 
> ```C
>  vector pos = point(1,'P',0);
>  pos = normalize(pos);
>  @Cd = dot(@N, pos);
> ```
> 

### Cross product

*Produit vectoriel*

Le produit vectoriel prend deux vecteurs et génère un troisième vecteur perpendiculaire. Le plus simple est de visualiser cela avec la règle de la main droite : 

![Vector_hand.Y7K_2L7i.png](/img/user/Pi%C3%A8ces%20jointes/Vector_hand.Y7K_2L7i.png)

> [!example]+ Exemples
> Exemple simple : faire pointer les normales vers une direction donnée : 
> 
> ```C
>  @N = cross(@N, {0,1,0});
> ```
> Exemple simple : grooming direction de base
> *Beaucoup de grooming tools utilisent ça*
> 
> On vient faire un double cross product pour d'abord donner une direction aux normales, puis les faire suivre la topo : 
> 
> ```C
> vector tmp = cross(@N, chv('vector'));
> @N = cross(@N, tmp);
> ```

### Opérations mathématiques de vecteurs

#### Addition de vecteurs : 

```C
vector a = chv('a');
vector b = chv('b');
@N = a+b;
```

![](https://www.tokeru.com/cgwiki/assets/Jov9_addvector_simple.CKO7mP-B.gif)

#### Soustraction de vecteurs : 

```C
vector a = point(0,'P',0);
vector b = point(1,'P',0);

@N = b-a;
```

![](https://www.tokeru.com/cgwiki/assets/Jov9_subtract_vectors.VD62G4ew.gif)


Exemple : Définir une velocité initale pour une simu d'explosion par exemple

```C
vector origin = point(1,'P',0);
@v = @P-origin;
```

![](https://www.tokeru.com/cgwiki/assets/Jov9_rbd_example.BQXWBlqS.gif)


#### Multiplication de vecteurs

```C
@N *= chv('scalevec');
```

![](https://www.tokeru.com/cgwiki/assets/Jov9_mult_sphere2.BciO6NDH.gif)


### Fonction relpointbbox

Cette fonction trace une bounding box autour de votre forme, définit le coin inférieur gauche à 0,0,0 et le coin supérieur droit à 1,1,1, puis renvoie la position de chaque point par rapport à ce rectangle

Mappé sur la couleur c'est assez visuel, c'est une sorte d'attribut de position relative (`@Cd = relpointbbox(0, @P);`)

Si on veut avoir des gradients top - bottom, ou front - back : 

```C
 vector bbox = relpointbbox(0,@P);
 @Cd = bbox.y;
```

### Conditions





---

## Références

[[0_INBOX/VEX - cas concrets utiles\|VEX - cas concrets utiles]]

---

#### Ressources vidéos

[Houdini Vex - from Beginner to Intermediate - YouTube](https://youtube.com/playlist?list=PLPcRZ8V0tr-mYQXu30uelP50AMSMj7Ubt&si=hEgr8VfTwnkD0gyu)

> [!example]- Flashcards
> ...




## Liens 




