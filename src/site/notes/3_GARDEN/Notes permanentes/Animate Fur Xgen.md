---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Animate Fur Xgen/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:33.483+01:00","mtime":"2025-09-13T23:16:49.764+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/GROOM]]","https://youtu.be/7IS_tnkO_oU?si=EOOO_jAPudF1GEDW"],"source":null,"tags":["note_permanente"],"creation date":"2025-02-07"}}
---

## La note 
---

### Version simple

Select guides + mode 
nHair -> Make selected curves dynamic : 

![Capture d'écran 2025-02-10 171025.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-10%20171025.png)

et après gérer les paramètres nHair genre gravité etc comme le nCloth

---

### Version workflow ESMA

etape1 : exporter ton groom en .mb dans une scène groom_pbh 

etape2 : export sclaps en alb 

etape3 : import scalps dans scene rig en root donc tu as des scapls qui apparaissent dans ta scene si tu veux modifier tes scalps tu les modifie dans une scene a part et tu viens ecraser les scalps dans ta scene de rig une fois les modifs faites 

etape4 :wrap tes scalps sur ta géo de base une fois ton anim de faite tu exporte ton grp geo en alb (riggé avc l'anim) tu ouvres ta scene groom pbh tu importes en alb merge ta geo posée dans ta scene groom pbh.

---

### Version complexe 
#### Générer linear wires

Add modifier : LinearWire
Input Wire : Create (ou use selected curves) 

*On peut ajouter des curves avec le place brush dans le transform du linearwire*

Ensuite : 
Selectionner le inguide du linearWire -> Interactive editor -> Description -> cache -> export cache en alembic 
**Cocher dans les advanced options : Multiple transforms et write final width**. Et se mettre en current frame
Ouvrir dans une nouvelle scène pour réexport en fbx 

Ensuite il y a 2 façons de faire différentes : 


#### Pour une anim du fur à la main (joints qui skin le fur etc)
###### Importer les curves dans le fichier de rig 

Importer les curves dans le fichier de rig
Wrap les curves à la géo primitive du fur (s'il y en a) pour que le skin influence les curves comme la modé

Ensuite faire l'anim comme ça puis export les curves avec l'anim en alembic pour mnt avoir l'anim. 

###### Convert curveToSpline

Dans le lookdev du groom, ajouter dans le inguide du linearwire un modifier curveToSpline. 
Décocher aligne to normal. 
Input : cache, importer les curves animées
Reference state (modifier LinearWire) : Update

Dans le modifier linearWire, mettre le graph de magnitude scale le début à 0 et la end à fond


#### Pour une nHair simulation

Dans la scène de rig, import les curves du linearwire. 
Attach les curves au scalp (wrap select mode puis groupe des curves par exemple + constraint parent pour le transform) 
Ensuite faire toutes l'anim. Les curves ne bougent pas mais suivent le skin. 
Export cache des curves avec l'anim puis autre scène pour la simulation

Import curves avec l'anim en abc ou fbx
nHair -> Make selected curves Dynamic 
Setup le nHair

Le hair system crée un group output curves 
Export ces curves en abc avec l'anim
###### Convert curveToSpline

Dans le lookdev du groom, ajouter dans le inguide du linearwire un modifier curveToSpline. 
Décocher aligne to normal. 
Input : cache, importer les curves animées
Reference state : Update

Dans le modifier linearWire, mettre le graph de magnitude scale le début à 0 et la end à fond

---

> [!abstract] Récap des scènes pour l'anim avec nHair (ce que j'en ai compris)
> - Lookdev fur fini 
> - Lookdev fur baked + linearWire
> - Rig 
> - Anim juste mode sans aucun poil
> - Anim mode baked + import linearWire abc -> Constraint parent + wrap à la modé -> Export alembic linearWire avec anim 
> - Anim mode baked + import linearWire animés en abc -> nHair sur linearWires -> export output curves du nHair 
> - Shot : Anim mode baked + nHair baked dans le linearWire du groom baked en référence
> 


## Références



## Liens 




