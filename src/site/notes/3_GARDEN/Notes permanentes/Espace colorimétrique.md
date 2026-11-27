---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Espace colorimétrique/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.125+01:00","mtime":"2026-04-04T12:57:39.633+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/3D]]","[[3_GARDEN/MOCs/COULEUR]]"],"source":["[[3_GARDEN/Notes littéraires/Chris Brejon, CG Cinematography book chapter 1, note litt]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510041727,"aliases":null}}
---

## La note 

Un espace colorimétrique RVB est composé de toutes les couleurs disponibles dans notre espace de travail. Il se définit par trois composantes :

- Primaires : _Les coordonnées chromatiques primaires définissent la gamme, la plage de couleurs (le triangle de couleurs) qui peut être codée par un espace colorimétrique RVB donné. Voir plus bas_
- Point blanc
- Fonctions de transfert

![Pièces jointes/29c588e05bee049f7dabdaf8ea90f891_MD5.gif](/img/user/Pi%C3%A8ces%20jointes/29c588e05bee049f7dabdaf8ea90f891_MD5.gif)

[https://www.colour-science.org/](https://www.colour-science.org/)

#### Primaires :

![Pièces jointes/379acbea59cfa64978a5c6ef047a319c_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/379acbea59cfa64978a5c6ef047a319c_MD5.jpg)

**Les primaires sont les sommets des triangles pour chaque gamut.**

Chacun de ces sommets possède **une valeur RVB pure** exprimée dans son propre espace colorimétrique :

- Rouge = 1, 0, 0
- Vert = 0, 1, 0
- Bleu = 0, 0, 1

Mais chacun de ces sommets a **une coordonnée xy unique** sur le diagramme CIE. C’est ainsi que nous pouvons les comparer.

![Pièces jointes/145dcd4341ac65fff1799e2dbd1c54d9_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/145dcd4341ac65fff1799e2dbd1c54d9_MD5.jpg)

Par exemple, il n’y a rien de plus saturé sur terre que les primaires BT.2020 ou les lasers, ils sont tous deux situés sur le locus spectral (la bordure du diagramme de chromaticité).

|                                | **Valeurs RVB sRGB/BT.709** | **Rec.2020 Valeurs RVB**   |
| ------------------------------ | --------------------------- | -------------------------- |
| **sRGB/BT.709 rouge primaire** | 1, 0, 0                     | 0.62742, 0.096910, 0.01639 |
| **sRGB/BT.709 vert primaire**  | 0, 1, 0                     | 0.32928, 0.91594, 0.08803  |
| **sRGB/BT.709 bleu primaire**  | 0, 0, 1                     | 0.04331, 0.01136, 0.89559  |
| **BT.2020 primaire rouge**     | 1.66045, -0.12455, -0.01815 | 1, 0, 0                    |
| **BT.2020 primaire vert**      | -0.58762, 1.13290, -0.10059 | 0, 1, 0                    |
| **BT.2020 primaire bleu**      | -0.07284, -0.00835, 1.11874 | 0, 0, 1                    |


#### Point blanc

_Le [point blanc](https://en.wikipedia.org/wiki/White_point) définit la couleur blanche pour un espace colorimétrique RVB donné._

![Pièces jointes/9cfd9df6ae6d25d15b71cc637ea7f333_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/9cfd9df6ae6d25d15b71cc637ea7f333_MD5.jpg)

Il existe différents types de points blancs. Par exemple, lorsqu’un point blanc est fourni avec un ensemble de primaires, il est utilisé pour équilibrer les primaires. Par exemple, les espaces colorimétriques sRGB et Rec.2020 ont un point blanc de D65. Cela fait partie de leurs caractéristiques intrinsèques.

Mais un espace colorimétrique RVB peut avoir [différents points blancs](https://github.com/colour-science/colour-notebooks/blob/master/notebooks/colorimetry/illuminants.ipynb) en fonction de son utilisation contextuelle. Il peut s’agir d’un choix créatif :

- Si vous souhaitez simuler la qualité de la lumière d’une **cabine d’observation standard**, choisissez le D50. La sélection d’une température de couleur chaude telle que D50 créera un blanc de couleur chaude.
- Si vous souhaitez simuler **la qualité de la lumière du jour à midi**, choisissez D65. Un réglage de température plus élevé tel que D65 créera un blanc légèrement plus froid.
- Si vous préférez une lumière du jour plus fraîche, choisissez D75

#### Fonctions de transfert

> [!info]
> Le système visuel humain (HVS) est plus sensible aux différences relatives dans les tons plus sombres plutôt que dans les tons plus clairs. Pour cette raison, ne pas utiliser de correction [[3_GARDEN/Notes permanentes/Gamma\|Gamma]] est un gaspillage car trop de bits seront alloués aux régions tonales où le HVS ne peut pas distinguer les tonalités.

Les fonctions de transfert (ou gamma) permettent de mieux encoder les bits, augmentant ainsi les performances. Il existe deux fonctions de transfert :

- **OETF** : la fonction de transfert opto-électronique, convertit la lumière linéaire de la scène en signal vidéo, généralement à l’intérieur d’une caméra. Lorsque vous photographiez ou **numérisez (pour l’encodage**).
- **EOTF** : fonction de transfert électro-optique, qui convertit le signal vidéo en flux lumineux linéaire de l’écran. Lorsque vous envoyez un signal à l’écran (pour le **décodage**).

![Pièces jointes/9512201c734613523533579625f30624_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/9512201c734613523533579625f30624_MD5.jpg)

_Il existe également des fonctions de transfert logarithmiques, mais c’est un autre sujet._

Deux propriétés sont également nécessaires **pour interpréter correctement un ensemble de valeurs RVB : l’état de l’image et l’environnement de** _visualisation_. Etat de l’image :

L’état de l’image est défini dans la [norme internationale ISO 22028-1](https://www.iso.org/standard/68761.html). Il s’agit essentiellement de la norme internationale sur la façon de définir un espace colorimétrique RVB.

L’état de l’image peut être référencé par la scène ou par l’affichage.

_Une image référencée par une scène est une image dont les valeurs de lumière sont enregistrées telles qu’elles existaient au niveau du plan focal de la caméra avant tout type de traitement dans l’appareil photo. Ces valeurs de lumière linéaire sont directement proportionnelles à la lumière objective et physique de l’exposition de la scène._

_Une image référencée par l’affichage est une image définie par la façon dont elle sera affichée. Rec.709, par exemple, est un espace colorimétrique référencé par l’écran, ce qui signifie que la plage de contraste des images Rec.709 est mappée à la plage de contraste du périphérique d’affichage, un téléviseur HD._

Environnement d’affichage : oui, l’environnement d’affichage est important lorsqu’il s’agit d’espaces colorimétriques. La pièce dans laquelle vous êtes assis, la lumière que vous utilisez, la couleur de vos murs... Tout cela a une influence sur vos conditions de visionnage et pour BT.709, elles sont définies [ici](https://www.itu.int/rec/R-REC-BT.2035-0-201307-I/en).

Normes de l’industrie

Les fabricants d’écrans et les majors du cinéma se sont mis d’accord sur certaines normes. Leurs caractéristiques modifient la façon dont nos images sont affichées et rendues. Voici les cinq plus importants pour nous :

- [sRGB](https://en.wikipedia.org/wiki/SRGB) pour Internet, Windows et les photos de l’appareil photo.
- [Rec. 709](https://en.wikipedia.org/wiki/Rec._709) a les **mêmes primaires** que sRGB mais diffère sur la fonction de transfert/[[3_GARDEN/Notes permanentes/Gamma\|Gamma]]. En effet, l’utilisation cible de Rec.709 est la vidéo où elle est censée être visionnée sur un environnement sombre.
- [DCI-P3](https://en.wikipedia.org/wiki/DCI-P3) pour projecteurs de cinéma.
- [Rec. 2020](https://en.wikipedia.org/wiki/Rec._2020), également appelé UHD TV, l’avenir de la colorimétrie.
- [AdobeRGB](https://en.wikipedia.org/wiki/Adobe_RGB_color_space) pour les projets d’impression.

![Pièces jointes/563084ae6e27bfda36881de2399dc826_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/563084ae6e27bfda36881de2399dc826_MD5.jpg)

lorsque l’on travaille sur un projet, il faut se poser la question : quelle est notre cible d’affichage ? Nos images vont-elles être vues sur un smartphone, sur un téléviseur ou dans une salle de cinéma ? Fondamentalement, l’espace d’affichage doit correspondre aux moniteurs utilisés dans votre entreprise.

Dans un flux de travail CG, il est essentiel de savoir **à chaque étape dans quel espace colorimétrique vous travaillez.**

> Lorsque vous achetez un moniteur, vous devez vérifier la couverture de ces espaces colorimétriques


## Références


> [!example]- Flashcards
> ...




## Liens 
