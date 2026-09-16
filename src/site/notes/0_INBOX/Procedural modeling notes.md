---
{"dg-publish":true,"permalink":"/0_INBOX/Procedural modeling notes/","dg-note-properties":{"aliases":["notes modelisation procedural"]}}
---


Différents types d'opérations de la modélisation procédurale : 
- Transformations
- Opérations géométriques basiques : bevel, extrude etc
- Création de masks, suppressions et groups
- Booléens
- Scattering


# Transformations procédurales


## Match size

Modifier les transformation d'un objet par rapport à sa propre bounding box ou par rapport à un autre objet


# Gestion des rotations

## Node orient along curve

Permet d'automatiquement aligner les normals d'une curve selon sa direction

## Rotation de normales

Node transform avec dans attributes N au lieu de * permet de rotate uniquement les normales

# Opérations géométriques de base

### PolyBevel

Créer des bevels

A noter qu'on peut contrôler les bevels avec un ramp (super pour ajouter du détail facilement)

### Node Bend

Permet de faire plusieurs déformations basiques de manière procedurales : 
- Bend
- Twist
- Lenght Scale (peut etre utilisé pour du squash and stretch)
- Taper

### Split 

Points split : permet de séparer les faces d'une géo


# Création de masks

Créer des masks selon : 
- une direction -> node mask by feature
- ambiant occlusion -> node mask by feature
- Curvature : node measure
- shadows -> node mask by feature

## Node group

Permet de créer des groups selon divers paramètres : 
- nom précis des éléments
- bounding box
- normals
- edges
- random

## Node Group by range

Super utile
Permet de sélectionner 1 sur 2 ou sur 3 ou sur 4 etc éléments

## Suppressions

Le node delete (a globalement les même paramètres que le node group)
Le node blast (pour garder que des edges par exemple)


# Manipulation de curves


## Carve node

Permet de "cut" une curve pour n'en garder qu'un bout

## Resample

Changer le nombre de points de la curve

paramètres : 
- by polygon edge : le resample se fait en fonction de chaque edge et pas en fonction de la curve globalement

## Add node

Permet de créer une curve à partir de points

## Sweep node

Permet de générer des surfaces le long d'une ou plusieurs curves 

Paramètres importants : 
- Surface shape : La forme de la surface
- Surface type : Le type de surface générée (triangle, quads, curves avec le mode column etc)
- Scale along curve : gérer l'épaisseur le long de la curve avec un ramp

La deuxième entrée permet de gérer le profil avec une geo custom 

# Scattering

## Extract centroid

Node qui permet d'extraire un point à partir du centre de quelque chose
Par exemple un point à partir du centre de l'objet ou plusieurs points à partir de chaque face de l'objet

## Chain node

Permet de faire répéter une géométrie le long d'une curve en gérant l'espacement, la taille, l'orientation, la rotation, le scale along curve etc

# Booleans

A noter qu'on peut faire des booleans en mode seam pour extraire uniquement une curve de l'intersection des géométries


---



# Tips plus advanced

### Randomiser dans un foreach

Il faut créer un attribute randomize "rand" avant le foreach

Puis dans la seed d'un node qui la comporte (un point jitter par exemple), rentrer cette expression qui va randomize la seed en fonction des itérations du foreach : 

```C
point("../foreach_begin4/", 0, "rand", 0)
```


