---
{"dg-publish":true,"permalink":"/0_INBOX/Procedural modeling notes/","ctime":"2026-09-18T10:17:49.306+02:00","mtime":"2026-10-20T22:49:40.194+02:00","dg-note-properties":{"aliases":["notes modelisation procedural"]}}
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

## Gestion des normales

Node polyframe permet de définir les attributs de repères de coordonnées (normales, tangent etc)

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

### Clip

Permet de cut une géo 

Pour qu'il cut en fonction d'un pourcentage de la bounding box : 
Expression suivante dans le origin Y(ici ça cut à 70%) : ``bbox(0, D_YMIN) + (bbox(0, D_YSIZE) * 0.7)``

#### Sub D modeling specific

##### Crease node

Permet de crease les edges selectionnées ou le group sélectionné

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

