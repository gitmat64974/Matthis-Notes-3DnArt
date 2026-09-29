---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Préparer skeleton et geo pour APEX/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[RIG]]","[[RIG HOUDINI]]","[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 

#### Skeleton

Quelques nodes à la fin du skeleton : 

1. Rig doctor SOP à la fin du skeleton avec initialize transform : sécurité pour être sur que la hiérarchie fonctionne et est clean
2. Rig stash pose : créer l'attribut de rest pose
3. Visrig pour vérifier l'orient et le parentage des joints visuellement dans le viewport


#### Geo

- Elle doit être dans la direction z positif

---


##### Packing final avant APEX

On a tout simplement le node APEX pack character qui fait ça automatiquement

Mais si on veut le faire à la main : 

![Pasted image 20260208152025.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260208152025.png)

voilà ce qu'on met dans le pack folder : 
![Pasted image 20260208152059.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260208152059.png)

ce n'est qu'une histoire de naming et d'assemblage de tout ce qui va constituer le rig (geo, joints et guides optionnellement)



## Références


> [!example]- Flashcards
> ...




## Liens 




