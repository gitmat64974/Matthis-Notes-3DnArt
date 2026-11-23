---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Importation dans Solaris/","tags":["note_permanente"],"ctime":"2026-11-23T23:32:44.724+01:00","mtime":"2026-11-23T23:33:01.805+01:00","dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":null,"aliases":null}}
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

## Références


> [!example]- Flashcards
> ...




## Liens 




