---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Skin texturing MARI/","tags":["note_permanente"],"dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2025-10-24","aliases":null}}
---

## La note 

Tout d'abord voir comment faire de la [[3_GARDEN/Notes permanentes/Projection dans Mari|Projection dans Mari]]

---

la base de la base : 

2 couleurs, un merge et un mask : 

![Pasted image 20260113175705.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260113175705.png)


---
### Couleur

Pour commencer : 

On peut commencer par exemple avec des mask pour chaque partie (nez, oeil, oreilles etc), mettre des teleport node pour les utiliser partout ensuite

#### Projection 

![](https://i.imgur.com/GAEMOgH.png)

On va utiliser la [[3_GARDEN/Notes permanentes/Projection dans Mari|Projection dans Mari]] pour faire soit une base rapide, soit si de bonnes maps sont utilisées (type texturing xyz), un texturing complet et détaillé


On peut également utiliser des maps triplanar et des tiles (*grunges, dirt, textures type marbre etc*) pour ajouter de la variété



[[3_GARDEN/Notes permanentes/MARI - Procedural Skin Imperfection|MARI - Procedural Skin Imperfection]]


### Roughness


Le process est d'utiliser ses masks créés au début pour assigner différentes valeurs de roughness en fonction des zones de la peau : 

![Pasted image 20260113181736.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260113181736.png)

*A voir avec le feedback du lookdev bien sur*

Après cela on peut ajouter la map de colo en la désaturant (attention avec cette méthode, à bien valider en lookdev) et la map de displace : 

![Pasted image 20260113181929.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260113181929.png)

### SSS amout map

![Pasted image 20260113182049.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260113182049.png)


Réfléchir en fonction de l'épaisseur de la surface et de la présence ou non d'os en dessous



## Références


- [Painting realistic skin displacement in Mari with XYZ Textures - YouTube](https://youtu.be/FqsyL1HKywU?si=eWeWs08MB0vuVkop)
- [Advanced Character Texturing in Mari: Studio Techniques - YouTube](https://youtu.be/ZWH2RY0eRv8?si=te2_lUCZ8-c19u88)



> [!example]- Flashcards
> ...




## Liens 




