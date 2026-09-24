---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/VEX/","tags":["note_permanente","en_cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[INFORMATIQUE]]","[[PROGRAMMATION INFORMATIQUE]]"],"source":["https://tokeru.com/cgwiki/JoyOfVex.html"],"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2025-12-11","aliases":null}}
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


> [!NOTE] distance()
> Cette fonction mesure la distance entre le point et une valeur donnée : 
> ``distance(@P, {1,0,3} );``
> 
> *Remplacer lenght par distance dans l'exemple précédent des vagues permet donc donner un point d'origine précis aux vagues plutôt que l'origine du monde*


> [!NOTE]+ Fit
> C'est l'équivalent d'un remap
> You tell it the incoming min and max values ( -1 and 1 par exemple pour une fonction sin), and the new min and max values you want (0 and 1).
> Ex : ``@Cd = fit(sin(d),-1,1,0,1);``

#### Modulo et quantisation

[[3_GARDEN/Notes permanentes/Modulo|Modulo]] 

[[3_GARDEN/Notes permanentes/Quantisation|Quantisation]] 

#### Fonction point

`point()` 

Elle permet de ***récupérer un attribut situé sur les points d'une géo en entrée***
paramètres : (géométrie d'entrée (0 pour la première entrée, 1 pour la deuxième entrée etc), le nom de l'attribut ("orient" par exemple), le point sur lequel regarder l'attribut (0 pour seulement le point 0, ou ptnum pour tous les points))

### Attributs

#### Pseudo attributs 

Ce sont des attributs que Houdini connait de base
En voici la liste : 
- P
- N
- Cd
- pscale
- uv
- v
- up
- orient
- ptnum
- primnum
- vtxnum
- numpt
- numprim
- numvtx
- age
- id
- life
- Time
- Timelnc
- Frame


#### Créer ses propres attributs

> [!NOTE]+ En VEX
> Très simple : ``@monattribut = ...;``
> On peut aussi spécifier le type de data de l'attribut avant le @ (f pour float, v pour vecteur, s pour string etc) mais ce n'est pas obligatoire


---

## Références

[[0_INBOX/VEX - cas concrets utiles|VEX - cas concrets utiles]]

---

#### Ressources vidéos

[Houdini Vex - from Beginner to Intermediate - YouTube](https://youtube.com/playlist?list=PLPcRZ8V0tr-mYQXu30uelP50AMSMj7Ubt&si=hEgr8VfTwnkD0gyu)

> [!example]- Flashcards
> ...




## Liens 




