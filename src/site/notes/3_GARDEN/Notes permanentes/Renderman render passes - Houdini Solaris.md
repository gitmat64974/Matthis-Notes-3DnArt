---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Renderman render passes - Houdini Solaris/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[SOLARIS]]","[[LIGHTING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":null,"aliases":null}}
---

## La note 

---

### AOVs

Node ``renderman render settings`` section rendervars : là on peut setup tous les AOVS "classiques" 

Si besoin d'AOVs custom, de LPEs etc, on peut mettre un node avant celui là : Node ``Render Vars`` ou le Node ``Additionnal Render Vars``

---

### Light Groups

1. Dans chacune des light (onglet renderman -> advanced) définir le nom du light group
2. Avant le node ``renderman render settings``, ajouter un node ``additionnal render vars``. Ajouter autant de rendervars que nécessaire. Exemple d'un LPE pour récupérer la beauty entière mais seulement du light group key : `C[DS]*<L.'Key'>`

Références : 
- [[3_GARDEN/Notes permanentes/LPE|LPE]]
- [Setting up LPEs in Solaris](https://rmanwiki-27.pixar.com/space/RFH27/544641953/Setting+up+LPEs+in+Solaris)

---

### Render Layers

Il suffit simplement de séparer le network : 

![](https://i.imgur.com/eleD8Q5.png)

Pour rendre tous les USD Render ROP en même temps : [[3_GARDEN/Notes permanentes/TOPs Rendering - Solaris|TOPs Rendering - Solaris]]

---

### Cryptomatte



---
## Références


> [!example]- Flashcards
> ...




## Liens 




