---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Rain dans houdini/","tags":["note_permanente","en_cours"],"ctime":"2026-03-21T20:44:44.183+01:00","mtime":"2026-11-26T22:14:04.891+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["Vidéo yt"],"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2025-11-21","aliases":["Houdini, pluie","Pluie dans houdini"]}}
---

## La note 

### Emettre depuis une grid

![Capture.png](/img/user/Pi%C3%A8ces%20jointes/Capture.png)

Créer une grid (c'est l'emetteur) et mettre un popnet juste après (c'est le node pour simuler les particules)

Rentrer dans le [[3_GARDEN/Notes permanentes/POP Network\|POP Network]]

Ajouter un node gravity juste avant l'output

Dans le POP source :

dans la partie Attributes :

![Pasted image 20251121204900.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251121204900.png)

Dans la partie birth :
baisser la life expectancy et monter la life variance


---
#### POP Collision

Pour la mode de collision :

![Pasted image 20251121204916.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251121204916.png)

Baisser le voxel size dans le collision source

---
Dans le popnetwork : 

Node popcollisionbehavior après le pop source : 
Group name : hit
response : die

Ensuite autre branche où on vient récupérer ce group dans un pop stream

#### POP Streams


POP Collision behavior : 
Ce node permet d'assigner un group au particules qui entrent en collision
Il permet également de leur assigner un comportement de base (die, stick etc)
-> A mettre après le POP Source

![Pasted image 20260127143906.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260127143906.png)

Pop Stream : permet de récupérer le group (ou en créer un directement)
Pop replicate : permet de duppliquer les particules et de gérer leur comportement
- Birth : tous les paramètres de birth comme dans le POP Source
- Shape : gérer la forme que la duplication suit
	- Uniform scale : permet de rapprocher ou éloigner les particules dupliquées de leur particule d'origine (sur la capture d'écran le uniform scale est à 0.1)



## Références

[Practical VOPS #1 - Rain Splashes - Houdini Beginner Tutorial - YouTube](https://youtu.be/KHbyvFRZhxU?si=JoIVKJo0exwPi-Iz)

[Rain Effect in houdini \| Houdini Tutorial - YouTube](https://youtu.be/Yi0ATGFthqk)



> [!example]- Flashcards
> ...




## Liens 




