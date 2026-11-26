---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/TOPs Rendering - Solaris/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:47.883+01:00","mtime":"2026-11-20T21:49:54.141+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["https://youtu.be/qg3OFz4JZs4?si=cYVfmzxMe7woh0qC"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-30","aliases":null}}
---

## La note 


Un Topnet va permettre de rendre en même temps plusieurs usdrender rop du contexte solaris

### Rendre plusieurs ROP en même temps

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


Pour lancer le rendu (sélectionner tous les nodes): 

![Pasted image 20251130103758.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251130103758.png)



> [!important]+ Nombre de coeurs engagés
> Par défaut, le nombre de coeurs engagés dans un cook topnet est d'1/4 le nb de coeurs total, soit très bas. C'est volontaire
> Si on veut l'augmenter, il faut augmenter le nb de coeurs engagés dans le node localscheduler du topnet (onglet Scheduling)
> 
> Toujours dans le local scheduler, onglet Job parms : Activer le mode single pour rendre à pleine puissance sans conflit de cœurs CPU (ce qui peut causer un nombre de cœurs engagés fluctuant)


---
#### En boucle : tout rendre avec un seul ROP Fetch (motif "for each")


Besoin uniquement de ces deux nodes : 

![Capture d'écran 2026-11-10 003117.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-10%20003117.png)

Le script python : 
```python
import hou

ropnet = hou.node("/stage")
# Direct children only : évite les doublons internes (sous-lopnets, componentoutput)
rops = [child for child in ropnet.children()
        if child.type().name() == "usdrender_rop"]
if not rops:
    raise Exception("Aucun usdrender_rop trouvé")
for rop in rops:
    item = item_holder.addWorkItem()
    item.setStringAttrib("rop", rop.path())
    item.setStringAttrib("ropname", rop.name())
```

⚠️ H22 : `addAttrib()` n'accepte **pas** de valeur (TypeError) — utiliser `setStringAttrib(name, value)`, qui crée l'attribut s'il n'existe pas.

> [!NOTE] Paramètres du seul ROP Fetch (validés en H22.0.487) :
> - ROP Path : `` `@rop` ``
> - Frames and Batching > Evaluate Using : `ROP Node Configuration` → 1 work item par ROP amont, le nombre de frames est déterminé par le ROP lui-même
> - Generate When : **All Upstream Items are Generated** → sinon le ROP Fetch reste dynamique et ne génère rien avant d'être lui-même cookté
> - Work Item Label (on) + Label Expression : `` `@ropname` ``

Un seul play sur ce ROP Fetch → tous les rendus partent **en parallèle** (borné par les slots du Local Scheduler). Ajouter un usdrender_rop dans le lopnet = rendu automatiquement au prochain cook, zéro maintenance.

**Variantes d'emplacement — le setup suit le LOPnet conteneur** :

- Le **script du scan** : seule la ligne chemin change — le reste (direct children du conteneur) est inchangé :
  - dans `lopnet1` : `ropnet = hou.node("/stage/lopnet1")` (3 ROPs Karma)


## Références


> [!example]- Flashcards
> ...




## Liens 




