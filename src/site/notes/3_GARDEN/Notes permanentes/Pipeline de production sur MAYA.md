---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Pipeline de production sur MAYA/","tags":["note_permanente","en_cours"],"dg-note-properties":{"MOC":["[[3D]]"],"source":"https://docs.google.com/document/d/1koZEXPR5BPJyV1j_J2mAHfWtscxvrqUK-6UkjUEcAm0/edit?tab=t.0","Projets":["[[Projet fil rouge]]"],"tags":["note_permanente","en_cours"],"creation date":"2026-02-10","aliases":null}}
---

## La note 

----

#### Nomenclature

<font color="#c0504d">Camel_Case</font> pour Tout ! 

> [!abstract]+ En règle générale :    
> - s’il faut **nommer un asset** :   *TypeDeLasset_NomDeLasset_Departement_version.extension* Exemple : char_mickey_lookdev_003.ma
> - s’il faut **nommer un objet dans une scène 3D**:  *TypeDeLasset_NomDeLasset_TypeDobjet3D* Exemple : char_mickey_geo

---

#### Publish

Quel que soit le département, on travaille notre asset dans un dossier Edit (ou des scenes du projet maya). Lorsqu'on doit le "passer" à un autre département, on ne passe jamais les scènes telles quelles, on créé une version **pbh** propre (entièrement cleanée) que l'on viendra écraser au fur et à mesure de notre avancée

Attention : ==son nom et son emplacement ne changent jamais==. A chaque nouvelle version, il faut écraser le fichier sans jamais changer le nom !

<font color="#9bbb59">Pourquoi :</font> **Vous évitez au département suivant d’avoir à chercher votre dernière version. Le département suivant n’a jamais à modifier ses refs. Si vous modifiez le nom d'un publish en cours de prod, vous allez faire perdre son travail à quelqu'un**


> [!tip]+ <font color="#f79646">Comment publier :</font>
> 
> 1. ***CLEAN*** : Lorsqu’il est prêt à être exporté, cleanez la version wip de votre asset (delete history, nomenclature, cleanup, freeze...). <font color="#c0504d">Assurez-vous qu’il n’y ait aucune référence dans ce que vous allez publier</font> (importez vos refs en dur si besoin en évitant les namespaces).
> 2. ***EXPORT*** : Exportez votre asset en-dehors de votre dossier “WIP” en le sélectionnant et en faisant File => Export selection, dans un dossier “publish”. Si vous publiez un .ma, vous pouvez faire encore plus le ménage dans la scène avec l’outil “File => OptimizeSceneSize.
> 
> *Source: Cours Pipeline V Besse, prof de lighting comp Montpellier : [PIPELINE & CACHE - Google Docs](https://docs.google.com/document/d/1koZEXPR5BPJyV1j_J2mAHfWtscxvrqUK-6UkjUEcAm0/edit?tab=t.0)*


---

#### Références

> [!abstract] Pourquoi des références
> Utiliser des refs permet de les updater sans ré-importer un asset et de garder les modifs faites
> Permettent de travailler dans des grandes scènes composées de plusieurs assets

##### Importer un fichier en référence : 

==On n'importe que des publishs !==

![](https://i.imgur.com/Ln3fK8D.png)

*Ou create reference*

##### Mettre à jour une reference

On met à jour une ref à chaque fois qu'un nouveau publish de l'asset est publié

![](https://i.imgur.com/FFSQgyg.png)


---

### Alembic merge

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

    








---


### Pipeline


> [!tip]+ Schéma version très simplifiée
> 
> ![pipe_prod_schema_par_sofia_fuentes_3d4.jpg](/img/user/Pi%C3%A8ces%20jointes/pipe_prod_schema_par_sofia_fuentes_3d4.jpg)
> 
> *Schéma par Sofia Fuentes*


Pipeline type de projets 3D3 (Zapping) : 

![Pasted image 20260210150909.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260210150909.png)

*Source: Cours Pipeline V Besse, prof de lighting comp Montpellier : [PIPELINE & CACHE - Google Docs](https://docs.google.com/document/d/1koZEXPR5BPJyV1j_J2mAHfWtscxvrqUK-6UkjUEcAm0/edit?tab=t.0)*



## Références


> [!example]- Flashcards
> ...




## Liens 




