---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Gestion des rotations - Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[MODELISATION]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-22","aliases":null}}
---

## La note 

#### Normales

Les normales sont le premier attribut qui permet de gérer les rotations dans Houdini. Elles sont très utiles car elles sont par défaut perpendiculaires à la surface

Quand on instance des points (par exemple copy to points), ***l'axe z*** des objets instancés sera aligné aux ***normales de la surface*** 

Donc les normales définissent comment l'axe z des instances va s'orienter

==Normales = Axe Z orientation==

#### Up vector

Le vecteur up (à créer généralement) va aligner l'axe y des instances à son orientation

==Up = Axe Y orientation==

L'un des problèmes qu'on va rencontrer si on utilise seulement ces des vecteurs (N et up) pour gérer les rotations est le [[3_GARDEN/Notes permanentes/Gimbal lock|Gimbal lock]]

#### Quaternion orient

L'attribut orient est l'attribut par excellence qui Houdini priorise pour gérer toutes les rotations (*Si N, up et orient existent, N et up seront ignorés*)

C'est un [[3_GARDEN/Notes permanentes/Quaternion|quaternion]], c'est à dire un vecteur à 4 dimensions


> [!success]+ Créer l'attribut orient à partir de N et up
> C'est en réalité très simple : 
> On "combine" N et up en une matrice de transformation puis on "converti" cette matrice en un quaternion, l'orient : 
> 
> ```C
> matrix3 m = maketransform(v@N,v@up);
> p@orient = quaternion(m);
> ```
> 

#### Rotate l'orient selon un de ses axes

Comment maintenant rotate pour que les instances rotatent selon un de leurs axes locaux ? 

Etapes : 
1. On définit une valeur de rotation (de combien on rotate): float entre 0 et 360
2. On crée un quaternion. La fonction quaternion nécessite 2 paramètres : un angle (en radians) et un axe (vecteur 3 -> x,y,z). Donc l'angle va être la valeur de rotation convertie en radians et l'axe va être un axe définit (*{0,1,0} par exemple -> le quaternion tournera selon son axe local y*)
3. On multiplie l'orient par ce quaternion avec la fonction `qmultiply`

Le code : 

```C
float rotation = chf('rotation');
vector4 rotation_quaternion = quaternion(radians(rotation), chv('axe_de_rotation'));

@orient = qmultiply(@orient, rotation_quaternion);
```

Code custom que j'ai déduit pour gérer les rotations sur les 3 axes à la fois : 

```C
vector rotation = chv('rotation');

vector4 rotation_quaternion_x = quaternion(radians(rotation.x), {1,0,0});
vector4 rotation_quaternion_y = quaternion(radians(rotation.y), {0,1,0});
vector4 rotation_quaternion_z = quaternion(radians(rotation.z), {0,0,1});

@orient = qmultiply(@orient, rotation_quaternion_x);
@orient = qmultiply(@orient, rotation_quaternion_y);
@orient = qmultiply(@orient, rotation_quaternion_z);
```

#### Blend entre 2 quaternions

Imaginons que l'on a 2 rotations différentes d'un quaternion et qu'on veut blend entre les 2 

Branchement des wrangles : 

![Capture d'écran 2026-09-22 233935.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-22%20233935.png)

Donc on va récupérer l'orient de la deuxième entrée, puis on va utiliser la fonction `slerp`, faite pour blend entre des quaternions : 

```C
vector4 second_rotation = point(1, "orient", @ptnum);
p@orient = slerp(@orient, second_rotation, chf('blend'));
```

Le blend ici est uniforme, mais on peut très bien le remplacer par un autre attribut custom (en float)
Imaginons qu'on ait défini un attribut custom appelé intensity qui vaut un sur une partie de la géo et 0 sur l'autre. Si on remplace le `chf('blend)` par cet attribut intensity, le blend se fera uniquement là où l'intensity est à 1


## Références


#### Ressources


[Particle rotations in Houdini (how to rotate orient) - YouTube](https://youtu.be/gmN76ZeObsA?si=o1rh87rESv2IICIC)



> [!example]- Flashcards
> ...




## Liens 




