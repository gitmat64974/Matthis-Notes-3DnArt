---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Houdini rendering/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.353+01:00","mtime":"2025-11-30T10:38:16.368+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["https://youtu.be/qg3OFz4JZs4?si=cYVfmzxMe7woh0qC"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-30","aliases":null}}
---

## La note 


#### Rendre plusieurs ROP en même temps

On utilise un topnet (task operator) : 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qg3OFz4JZs4?si=TuTVGrnQoJI99RX5" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Le process : 

Créer plusieurs ROP fetch à la suite pour chaque ROP

> [!NOTE] Paramètres de chaque ROP Fetch :
> - ROP Configuration
> 	- ROP Cook order : ``node by node``
> 	- ROP Path : ``/stage/$OS``
> - Frames and Batching
> 	- Evaluate using : ``Rop Node Configuration``

![](https://i.imgur.com/pOZRzzM.png)


Pour lancer le rendu : 

![Pasted image 20251130103758.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251130103758.png)

## Références


> [!example]- Flashcards
> ...




## Liens 




