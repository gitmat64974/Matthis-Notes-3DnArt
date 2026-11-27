---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Différence Renderman Maya Batch ou RIB Spool type/","tags":["note_permanente"],"ctime":"2026-04-06T00:00:55.000+02:00","mtime":"2026-04-24T17:43:18.668+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/Cours compositing Rebuild Shot (insecte 3D2)]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-01","aliases":null}}
---


## La note

![Capture d'écran 2025-04-30 231447.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-30%20231447.png)

Dans les “Preferences/RenderMan” — Quelle est la différence entre les valeurs “MayaBatch” et “RIB” du paramètre de “SpoolType”?

- **“Maya Batch”** va enregistrer sur votre session toutes les informations associées au rendu de votre séquence d’images. Une fois ce processus terminé, une requête va être envoyée au LocalQueue (ou soft de Dispatching) pour rendre vos séquences. Ce SpoolType permet d’être plus léger pour les espaces disques et vous force à troubleshoot des problématiques de Rendering directement dans votre scène.
- **“RIB”** va écrire localement dans le dossier “/renderman/rib/” un fichier .rib pour chacune des frames de votre display. Si le processus est plus long et consomme de l’espace disque, il permet de relancer vos rendus à partir de ces RIBs. Ce SpoolType est davantage utilisé en studio afin de troubleshoot des jobs de rendu, ou de relancer une séquence de rendus sans avoir à ré-ouvrir la scène.

Plus d'infos : [rmanwiki-26.pixar.com/display/RFM23/Batch+Rendering+in+Maya](https://rmanwiki.pixar.com/display/RFM23/Batch+Rendering+in+Maya)


## Références 

## Liens 
