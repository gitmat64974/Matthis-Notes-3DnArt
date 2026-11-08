---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Alembic Merge/","tags":["note_permanente","plante"],"dg-note-properties":{"MOC":["[[ANIMATION]]","[[Pipeline de production en animation]]"],"source":null,"Projets":["[[Projet fil rouge]]"],"tags":["note_permanente","plante"],"creation date":"2026-02-04","aliases":null}}
---

## La note 


![Pasted image 20260215222011.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260215222011.png)


[PIPELINE & CACHE - Google Docs](https://docs.google.com/document/d/1koZEXPR5BPJyV1j_J2mAHfWtscxvrqUK-6UkjUEcAm0/edit?tab=t.0)

On peut le faire depuis **des références animées**

**Attention aux naming, aux namespaces et aux numéros des vertex qui ne doivent pas changer par rapport à la scène de Lookdev de l'asset**

Propreté et naming : 
Idéalement l’artiste qui a fait la modé a créé un SET qui comprend toutes les géos de l’asset
pour que vous puissiez les sélectionner facilement, idéalement tous vos meshs sont nommées “..._geo”


##### Export alembic : 

- Réglez votre framerange. 
- Cochez UV Write si vous avez des UVs sur la modé à exporter. 
- Cochez “WORLD_SPACE” ou votre modé exportée ne prendra pas en compte le rig et donc votre .abc sera STATIQUE !
- Si vous avez animé la visibility de certains objets cochez-la aussi.


##### Import abc dans lookdev


Dans la scène de lighting à rendre (ou scène de confo, selon votre organisation et naming) : 

- Si besoin, Importez le fichier de lookdev avec les matériaux assignés (vous pouvez le faire en ref, car appliquer les alembics sur des références fonctionne)

Attention aux namespaces à l’import : lors de l’import de l’abc, il faut que les objets venant du lookdev sélectionnés aient le même nom et le même numéro de vertex que lors de la création du cache, ou bien ça ne marchera pas 

> [!success]+ Alembic merge : 
> - Sélectionnez les objets qui doivent être animés par votre cache à la même racine que lors de l’export abc. 
> - Attention, si vous cochez “Add non-matching…”, ça fait sauter les shaders ! Cette fonction n’est là que pour réparer des bugs ou des alembics douteux, faudra réassigner à la main vos shaders dans ce cas.
> - Importez l’alembic en cochant “merge”

    


## Références


> [!example]- Flashcards
> ...




## Liens 




