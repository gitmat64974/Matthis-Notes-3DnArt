---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Stylisation dans Nuke/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[COMPOSITING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-10-03","aliases":null}}
---

## La note 

#### Toon shading

**Pourquoi :** L'objectif de cette technique est de diviser l'image en trois zones d'exposition distinctes (l'ombre, la lumière et les zones intermédiaires) afin de pouvoir casser les gradients de lumière et donner un effet stylisé (*ghibli par exemple*)

**Comment (Pas à pas) :**

- Récupérez la passe de diffuse et la passe de couleur de base de l'objet, appelée albedo.
- Combinez les avec un nœud **Merge** réglé sur l'opération `divide` pour isoler l'éclairage pur et ne récupérer que les ombres -> On crée la map d'irradiance
- Utilisez un nœud **Shuffle** pour ne garder que la couche bleue de ce résultat.
- Ajoutez un nœud **Grade** pour écraser le contraste des ombres afin d'aplatir l'image.
- Générez trois masques en utilisant des nœuds **Keyer** :
    - **Keyer 1** : Poussez fortement le contraste pour créer un masque qui isole uniquement les zones d'ombres.
    - **Keyer 2** : Faites l'inverse du premier pour isoler uniquement les zones de haute lumière.
    - **Keyer 3** : Créez un masque pour les valeurs intermédiaires (les demi-teintes).

- Rassemblez ces trois masques dans une seule image à l'aide de nœuds **Shuffle** : envoyez l'alpha du masque 1 dans la couche Rouge, l'alpha du masque 2 dans la couche Verte, et l'alpha du masque 3 dans la couche Bleue.
- Le but est d'obtenir un dégradé de température (bleu, vert, rouge) bien défini, en évitant d'avoir du jaune ou du noir, ce qui indiquerait que vos masques se chevauchent de manière indésirable.

Ensuite on va venir grader l'albedo avec ces 3 masques (et des cryptomatte très certainement) : 

**Comment (Pas à pas) :**
- **Ajustement de la couleur** : Placez un nœud **Grade** directement sous votre passe d'Albedo pour pouvoir modifier facilement la couleur de base des objets.
- Dans Nuke, utilisez les données [[3_GARDEN/Notes permanentes/Cryptomatte|Cryptomatte]] associées aux matériaux des objets (via un clic gauche sur "Crypto Material").
- Utilisez un nœud **Shuffle** pour récupérer la couleur spécifique générée par le [[3_GARDEN/Notes permanentes/Cryptomatte|Cryptomatte]] pour l'objet voulu, et envoyez cette information dans le canal Alpha pour obtenir un masque de sélection parfait.


## Références


> [!example]- Flashcards
> ...




## Liens 




