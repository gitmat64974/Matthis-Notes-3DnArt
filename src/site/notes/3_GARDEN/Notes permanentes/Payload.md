---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Payload/","tags":["note_permanente"],"ctime":"2026-11-24T00:10:08.366+01:00","mtime":"2026-11-24T00:10:27.775+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-24","aliases":null}}
---

## La note 

**Qu'est-ce qu'un payload ?**
- Un type spécial de Référence qui peut être unloaded pour l'optimisation. C’est une reference normale, sauf qu’on contrôle la mémoire (si on veut la charger ou pas : “load only what you want !”
- Un Payload a une force plus faible qu'une Référence

**Unloading un Payload**
- Lorsque nous déchargeons un Payload, la scène ne chargera rien dans le fichier étant « payloadé ». On verra généralement juste une bounding box
- Nous pouvons écrire une description légère du contenu (AssetInfo, Variants, Bounding Box) afin de savoir ce qui n'est pas chargé dans la scène

#### Comment unload les payloads dans le viewport : 

Dans le scene graph de solaris, cliquer sur l'icone de mask de zoro et décocher load all payload in viewport -> ça désactive tous

Pour sauvergarder dans un node cet état de graph (très utile pour le désactiver, activer facilement) on clique sur l'icone de masque de zoro -> create configure stage node from load masks. La ça crée un node qu'on peut mettre à la suite de notre node graph

Si on veut ensuite en remettre individuellement : dans le scene graph à côté de la primitive il y a une colonne pour load le payload

#### Comment créer un payload

[USD Asset Building with Solaris 9 \| Creating a Payload \| Vidéos & films sur Vimeo](https://vimeo.com/814277163?fl=pl&fe=sh)


## Références


> [!example]- Flashcards
> ...




## Liens 




