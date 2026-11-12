---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Renderman render passes - Houdini Solaris/","tags":["note_permanente","plante"],"ctime":"2026-11-08T18:21:59.279+01:00","mtime":"2026-11-12T22:29:17.484+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SOLARIS]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":null,"Projets":null,"tags":["note_permanente","plante"],"creation date":"2026-11-08","aliases":null}}
---

## La note 

---

### AOVs

Node ``renderman render settings`` section rendervars : là on peut setup tous les AOVS "classiques" 

Si besoin d'AOVs custom, de LPEs etc, on peut mettre un node avant celui là : Node ``Render Vars`` ou le Node ``Additionnal Render Vars``
*A noter qu'on peut rendre comme AOV custom n'importe quelle primvar donc n'importe quel attribut houdini converti dans le système USD. Par exemple ajouter une rendervar en mode primvar appelée st va ajouter la map d'uv de toute la scene, la st map*

#### Cas particulier : AOV shadow

La doc Solaris (Houdini 27) décrit ce setup avec un objet qui reçoit l’ombre, ici un sol :

1. **Marquer le sol en holdout.** Avec un Render Geometry Settings LOP, dans l’onglet RenderMan / Trace, activez Holdout. Le sol doit avoir son propre shader, idéalement texturé comme le vrai sol de votre plate. [atlassian](https://renderman.atlassian.net/wiki/spaces/RFH27/pages/567312445/Holdout+Workflow)
2. **Créer les AOV.** Ajoutez un RenderMan Render Settings LOP, onglet RenderVars, et activez les 3 AOV dans le menu déroulant Holdouts. Ce sont `occluded`, `unoccluded` et `shadow`. [atlassian](https://renderman.atlassian.net/wiki/spaces/RFH27/pages/567312445/Holdout+Workflow)

#### Cas particulier : AOV AO

![Capture d'écran 2026-11-12 211511.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-12%20211511.png)


---

### Light Groups

1. Dans chacune des light (onglet renderman -> advanced) définir le nom du light group
2. Avant le node ``renderman render settings``, ajouter un node ``additionnal render vars``. Ajouter autant de rendervars que nécessaire. Exemple d'un LPE pour récupérer la beauty entière mais seulement du light group key : `C[DS]*<L.'Key'>`

Références : 
- [[3_GARDEN/Notes permanentes/LPE\|LPE]]
- [Setting up LPEs in Solaris](https://rmanwiki-27.pixar.com/space/RFH27/544641953/Setting+up+LPEs+in+Solaris)

---

### Render Layers

Il suffit simplement de séparer le network : 

![](https://i.imgur.com/eleD8Q5.png)

Pour que des objets en dehors du layer projettent leurs ombres sur les objets du layer : mettre un `rendergeometrysettings` avant les rendersettings et activer le holdout sur ces objets projeteurs d'ombres

Pour rendre tous les USD Render ROP en même temps : [[3_GARDEN/Notes permanentes/TOPs Rendering - Solaris\|TOPs Rendering - Solaris]]

---

### Cryptomatte

[Cryptomatte in Solaris](https://rmanwiki-27.pixar.com/space/RFH27/544642079/Cryptomatte+in+Solaris)

Le setup est assez simple : 

![](https://i.imgur.com/7PjmbrK.png)

Dans le ``usdrender_rop`` se mettre en mode render delegate ``XPU - CPU``. Le RIS ne fonctionne pas avec ce système

---

### Exporter un Raw Lighting : 

Simplement faire un layer supplémentaire avec un overide de matériau gris sur toute la scène

*On peut aussi en comp diviser la diffuse par l'albedo et on obtiendra le raw lighting. Mais Pixar déconseille la multiplication et la division au niveau pixel : artefacts sur les bords antialiasés, et à un résultat approximatif sur l’indirect*

---
## Références


> [!example]- Flashcards
> ...




## Liens 




