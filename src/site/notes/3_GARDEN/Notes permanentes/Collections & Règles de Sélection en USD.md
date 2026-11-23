---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Collections & Règles de Sélection en USD/","tags":["note_permanente"],"ctime":"2026-11-23T23:12:52.315+01:00","mtime":"2026-11-23T23:20:45.407+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-23","aliases":null}}
---

## La note 

#### Collections

C'est en gros l'équivalent des selections sets de MAYA : ça permet de regrouper des primitives ensemble sans forcément les regrouper hiérarchiquement. Ca peut donc être très utile pour par exemple assigner des shaders à tous les objets d'un type, créer des layers etc etc
Il faut le node collection pour pouvoir en créer

Les collections sont créées en tant que primitives dans le graphe de scène afin que vous puissiez les enregistrer sur le disque dans un fichier `.usd`, puis les rappeler facilement plus tard dans votre scène ou par un autre artiste/département. De cette façon, vous pouvez considérer les « Collections » comme une version USD des « Groupes » de Houdini.

Les collections peuvent être enregistrées dans la primitive `/collections` (par défaut), ou dans toute autre primitive du graphe de scène.

Pour rechercher dans le scene graph ou utiliser des collections comme sélections : `%collection:NomDeVotreCollection` (par exemple `%collection:Verre`) -> voir plus bas pour le detail

#### Règles de Sélection (_Selection Rules_)

Une règle de sélection (appelée _Primitive Matching Pattern_ dans Solaris), c'est **la phrase ou la formule** qu'on écrit pour trouver des objets dans notre scène. Elles sont uniques à Houdini, ne sont enregistrées que dans le fichier `.hip` et ne peuvent pas être exportées dans des fichiers `.usd`.

##### Motifs de Chemin (_Path Patterns_)

- Faire correspondre la primitive avec le chemin `/Kitchen/Table/Leg1` : `/Kitchen/Table/Leg1`
- Faire correspondre tous les enfants de `/Kitchen` : `/Kitchen/*`
- Faire correspondre tout enfant de `/Kitchen` dont le nom commence par `Chair` : `/Kitchen/Chair*`
- Faire correspondre tous les descendants de `/Kitchen` dont les noms sont `Handle1`, `Handle2`, `Handle3` ou `Handle4` : `/Kitchen/**/Handle[1234]`
- Faire correspondre tout enfant de `/House` dont le nom est `Room` suivi d'un seul caractère (comme `RoomA`) : `/House/Room?`

##### Syntaxe de Collection (_Collection Syntax_)

- Faire correspondre toute primitive spécifiée par la collection `KeyLights` sur la primitive `/collections` : `%KeyLights`
- Faire correspondre toute primitive spécifiée par la collection `KeyLights` sur la primitive `/House/LivingRoom` : `/House/LivingRoom.collection:KeyLights` ou `%*/House/LivingRoom/KeyLights`

##### Syntaxe de Règle de Sélection (_Selection Rule Syntax_)

- Pour faire correspondre toutes les primitives spécifiées par la règle de sélection `/rules/Characters` : `%rule:/rules/Characters` ou `%rule(/rules/Characters)`



## Références


> [!example]- Flashcards
> ...




## Liens 




