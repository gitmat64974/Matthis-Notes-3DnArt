---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Light Filters Solaris/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.871+01:00","mtime":"2026-11-06T08:30:08.777+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-21","aliases":null}}
---

## La note 

Les filtres de lumière servent à modifier les effets d'éclairage. Dans la réalité, on utilise souvent des pochoirs et des gélatines pour obtenir ce résultat en modifiant la couleur, la qualité et l'intensité de la lumière dans un plan.

### Karma

[Houdini - Karma CPU - procedural light filters 1 - YouTube](https://youtu.be/dmJbM7TcTXk?si=9F-bU04yk9DhC2vn)

### Renderman

Ajouter un des nodes renderman de light filter, celui qu'on veut utiliser : 

![](https://rmanwiki-27.pixar.com/download/attachments/544641289/lightFilterLOPs.png)

Then assign it to a light using one of the following methods:

- Use a PxrAssign LOP (or the PxrAssignLightFilter alias). You can use a single PxrAssign LOP to assign multiple light filters to multiple lights.
- Use a Light Edit LOP and fill the Light Filters parameter on the Base Properties tab
- Plase a Light Edit LOP after the light filter LOP and fill the Light Filters parameter on the Base Properties tab

Ce que chaque type de light filter fait : [Light Filters](https://rmanwiki-27.pixar.com/space/RU/628752397/Light+Filters)

![](https://rmanwiki-27.pixar.com/download/attachments/544641289/assignLighFilter.png)

To parent a light filter to a light (as shown above in the Scene Graph), simply set the Primitive Path parameter on the light filter LOP with the proper path (e.g. ``/lights/light1/$OS instead of the default '/lightFilters/$OS``).


## Références

[Light Filters in Solaris](https://rmanwiki-27.pixar.com/space/RFH27/544641289/Light+Filters+in+Solaris)

> [!example]- Flashcards
> ...




## Liens 




