---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Component Builder/","tags":["note_permanente"],"ctime":"2026-11-03T20:08:01.964+01:00","mtime":"2026-11-24T00:10:55.158+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/SOLARIS|Solaris]]","[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/Cours Houdini semaine 3]]","[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510132311,"aliases":["Asset USD"]}}
---

## La note 

Le component builder créée un ensemble de nodes nécessaires à la création simple et complète d'un asset USD : 
- référencer la géo
- créer et assigner des shaders
- exporter l'asset USD

![Capture d'écran 2026-11-01 213928.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20213928.png)

La hiérarchie des fichiers exportés par le component builder : 

![Capture d'écran 2026-11-01 214439.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20214439.png)

*-> [[3_GARDEN/Notes permanentes/Payload\|Payload]]*

---
#### Component geometry

3 modes pour importer la géo : 
- **Internal SOP** : Entrer à l'intérieur pour setup la geo de render, et si on veut la geo proxy et la geo simproxy. ->*Le mode préférable*
- **File** : fichier référencé
- **External SOP** : chemin dans un SOPNet externe

La géo va être nommée en fonction du nom qu'on donne au node 

On va donc avoir la possibilité de setup 3 "versions" de la géo en mode internal SOP (*le plus simple est d'entrer à l'intérieur du node*) : 
- **default / render** (*Obligatoire*) : Geo de rendu
- **Proxy** (*Optionnelle*) : Geo allégée pour la rapidité du viewport
- **SimProxy** (*Optionnelle*) : Si on veut avoir le contrôle sur la géo de proxy utilisée dans les outils de physics de solaris (comme l'edit LOP, le layout LOP etc)

---

#### Component material

Construire le shader dans le material library (Souvent un [[3_GARDEN/Notes permanentes/Mtlx Shader\|Mtlx Shader]])

Puis le component material va assigner automatiquement le shader qui vient de la deuxième entrée à la géo qui vient de la première
Le matériau va être nommée en fonction du nom qu'on donne au node 

Mode manuel : 
*S'il y a plusieurs shaders, ou des variants etc on va devoir les assigner à la main*

---
#### Component output

Assez simple, gère tout l'output de l'asset
- Root prim : nom de la primitive qui contiendra la geo et les shaders
- Location dans caching : l'endroit où l'asset sera sauvegardé sur le disque
- Cliquer sur save to disk

Thumbnail : permet de générer une image thumbnail de présentation de l'asset (super utile pour les bibliothèques d'asset etc)


> [!info]+ Hiérarchie des fichiers d'un asset usd : (par exemple ici un pig_head.usd)
> - Le pig_head.usd vient charger le payload.usd
> - Le payload.usd vient charger ensuite le geo.usd et mtl.usd

*A noter qu'on peut rentrer dans le component output pour mettre des nodes spéciaux de traitement comme un rendergeometrysettings pour gérer la subdivision au rendu par exemple*

---

## Références

Comment créer des variants : [[3_GARDEN/Notes permanentes/Créer des variants avec le component builder\|Créer des variants avec le component builder]]

#### Ressources


- [USD Asset Workflow in Solaris \| Gingerbread House - YouTube](https://youtu.be/tbzIABrViYg)
- [Creating USD Assets with Component Builder](https://vimeo.com/639704886?fl=pl&fe=sh)
- [Creating USD Assets with Component Builder \| Chris Rydalch \| Solaris Workshop](https://vimeo.com/639704886?fl=pl&fe=sh)


> [!example]- Flashcards
> ...




## Liens 




