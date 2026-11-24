---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/SOLARIS/","tags":["note_permanente","MOC"],"ctime":"2026-11-06T12:41:57.054+01:00","mtime":"2026-11-23T23:41:00.397+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["Houdini learning"],"Projets":null,"tags":["note_permanente","MOC"],"creation date":"2026-11-05","aliases":["Solaris"]}}
---

# Définition

*Texte de Yann Pannetier*

Solaris est un module d’Houdini basé sur l’USD, développé par SideFx en collaboration étroite avec Pixar/Renderman. Il peut servir à faire du layout, du lookdev, du lighting…

- **SOLARIS** est l’ensemble du système USD implémenté dans Houdini.
- Il y a plusieurs contexts ( = networks ) dans Houdini. Nous on bosse dans le context stage (ou “LOP network”) prévu pour l’USD. Le Stage est la résultante visuelle d’une composition (empilement) de sublayers.
- **LOP** (= lighting operator) est le type de noeuds qui traite des layers USD dans Solaris (dans le stage context). Il permet de créer des layers dans le stage. SOP
(Surface Operators) est le type de noeud qui permet de modifier de la géométrie dans Houdini (dans le Tools context entre autres). On peut passer d’un systeme à l’autre avec des noeuds dédiés

#### Premiers pas avec Solaris

Créer un lopnet ou aller dans le stage

SOP Import : pour référencer des géos qui sont déjà dans le projet
Asset reference : importer un asset usd
reference : importer un fichier type alembic etc


> [!example]+ Un setup basic
> 
![](https://i.imgur.com/jkT7A3G.png)

#### Lighting tools

On a plusieurs outils en sélectionnant une light pour placer la light rapidement et facilement : ce sont les placement mode (toolbar en haut du viewport)


![](https://i.imgur.com/V3LDOb3.png)


En diffuse : 
On peut cliquer sur n'importe quelle geo à n'importe quelle endroit et la light s'alignera avec la normale précise du points où l'on a cliqué

En shadow : 
Clic dans le viewport pour définir le pivot
shift + clic pour définir l'orientation et la position des ombres sur le sol 


# Structure

### Importation d'éléments

[[3_GARDEN/Notes permanentes/Importation dans Solaris\|Importation dans Solaris]]


Caméras : 
- [[3_GARDEN/Notes permanentes/Importer une caméra - Houdini\|Importer une caméra - Houdini]]


#### L'USD

-> [[3_GARDEN/MOCs/USD\|USD]]

- [[3_GARDEN/Notes permanentes/Component Builder\|Component Builder]]

#### Set dressing

- [[3_GARDEN/Notes permanentes/Construction d’un Set dans Houdini\|Construction d’un Set dans Houdini]]
- [[3_GARDEN/Notes permanentes/Layout Node Solaris\|Layout Node Solaris]]

#### Shading

[[3_GARDEN/Notes permanentes/Auto assign materials Solaris\|Auto assign materials Solaris]]

#### Généralités

[[3_GARDEN/Notes permanentes/Kernel\|Kernel]]

[[3_GARDEN/Notes permanentes/Export camera Houdini\|Export camera Houdini]]

[[3_GARDEN/Notes permanentes/ACES Dans Houdini\|ACES Dans Houdini]]

[[3_GARDEN/Notes permanentes/Light Filters Solaris\|Light Filters Solaris]] 

#### Rendering

[[3_GARDEN/Notes permanentes/Hydra - Solaris\|Hydra - Solaris]]
- [[3_GARDEN/Notes permanentes/TOPs Rendering - Solaris\|TOPs Rendering - Solaris]]
- [[3_GARDEN/Notes permanentes/USD Render ROP Node\|USD Render ROP Node]]

[[3_GARDEN/Notes permanentes/Render threads optimization Karma\|Render threads optimization Karma]]


# Ressources

Video d'intro : 
[Master Lighting in Houdini Solaris - YouTube](https://youtu.be/qdXiGmFbZeE)


Video très complète : [Cinematic Lighting In Houdini \| Week1 Lessons With Nick Chamberlain (Pro VFX Course) - YouTube](https://youtu.be/bDaD7OBfV7s?si=psn8MvcjtPzGv59i)




