---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Importation dans Solaris/","tags":["note_permanente"],"ctime":"2026-11-24T08:32:51.178+01:00","mtime":"2026-11-23T23:35:42.809+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-23","aliases":null}}
---

## La note 

### Sublayer node

Le node sublayer vient importer une scene usd complete (fichier usd d'un set par exemple) avec toute la hiérarchie du scene graph etc
On peut en importer plusieurs avec un seul node sublayer

---
### Reference node

Permet de mieux controler l'import que le noeud sublayer, en permettant de spécifier ce qu'on veut importer. Mais attention si on veut importer tout un set et pas juste une partie il faudra importer plusieurs sous parties et il y aura très certainement des problèmes de hiérarchie.

Si on veut donc importer tout un set avec sa hiérarchie et tous ses éléments, à privilégier le node sublayer

Il permet donc de référencer une partie seulement d'un fichier usd (une partie d'un set, juste le terrain ou juste les lights par exemple etc)

Par défaut il import l'objet principal du fichier usd (s'il n'y a qu'un type il importera celui là et s'il y en a plusieurs il choisira automatiquement)
Il faut se mettre en mode reference specific primitive pour choisir précisément

---
### Asset reference

Similaire au node reference mais il peut load en plus les variants d'un asset usd

---

### Importer dans Solaris depuis SOPs

3 façons : 
- Scene import : façon rapide d'importer tout le context obj. On peut bien entendu filtrer (un objet, uniquement les lights ou les cameras ou les matériaux etc)
- Sop import : importe une géo depuis un endroit spécifique dans le context obj. Généralement depuis un null ou un output
- Sop create : permet de créer un réseau géométrique SOP directement dans le stage

---

## Références


> [!example]- Flashcards
> ...




## Liens 




