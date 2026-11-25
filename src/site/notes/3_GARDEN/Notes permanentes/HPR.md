---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/HPR/","tags":["note_permanente"],"ctime":"2026-11-25T15:37:45.221+01:00","mtime":"2026-11-25T17:22:13.092+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]","[[3_GARDEN/MOCs/SOLARIS|Solaris]]","[[3_GARDEN/MOCs/HOUDINI]]"],"source":["https://www.sidefx.com/docs/houdini/solaris/shotbuilder.html"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-25","aliases":["Houdini Path Resolver","HPR Asset Resolver","HPR Resolver"]}}
---

## La note 

**HPR** (*Houdini Path Resolver*) est le resolver d'assets intégrée de SideFX, introduit avec le [[3_GARDEN/Notes permanentes/Shot Builder - Houdini Solaris\|Shot Builder]] (Houdini 21, contexte Solaris). 
Un resolver est une « boîte noire » qui gère les chemins de fichiers : dans un projet Shot Builder, les layers USD s'écrivent sous la forme `hpr:shot/s0010/shot.usda`, et HPR résout le chemin vers la version la plus récente (v1, v2, v3…), versionne automatiquement les exports à chaque publication, et permet d'épingler une version précise (`?v=2`) quand on veut stabiliser un shot. 
C'est lui qui fait tourner le versioning en coulisses pendant que les artistes travaillent.




## Références

- Doc SideFX — [Shot Builder Tools](https://www.sidefx.com/docs/houdini/solaris/shotbuilder.html) (section *HPR Asset Resolver*)
- Usage détaillé en prod : [[1_PROJETS/FFE/02_PROD/PIPELINE/FFE - TAAL - Pipeline - Shot Builder Sequence Switcher\|FFE - TAAL - Pipeline - Shot Builder Sequence Switcher]]

> [!example]- Flashcards
> #domaine/houdini
>
> ---
> C'est quoi HPR, et avec quoi a-t-il été introduit ?
> ;;
> **Houdini Path Resolver** — la resolver d'assets USD de SideFX, introduite avec le Shot Builder (Houdini 21, Solaris) : résolution des chemins `hpr:` + versioning automatique des layers, épinglables avec `?v=2`.

## Liens

HPR automatise le versioning des [[3_GARDEN/Notes permanentes/USD Layers\|USD Layers]] — le même besoin commun à tout pipeline multi-shots (cf. [[3_GARDEN/Notes permanentes/Pipeline USD\|Pipeline USD]]), résolu « dans la boîte » par le Shot Builder.
