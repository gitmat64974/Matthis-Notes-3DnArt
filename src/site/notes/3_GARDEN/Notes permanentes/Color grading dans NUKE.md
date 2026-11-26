---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Color grading dans NUKE/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:45.032+01:00","mtime":"2026-04-24T17:43:18.639+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/3e et 4e cours compositing esma 3d2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


---
## La note

#### Visualisation colorimétrique

> [!NOTE]+ Histogram, Waveform et vectorscope
> 
> ![Capture d'écran 2025-05-12 183504.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20183504.png)
> 
> Pour Ouvrir les onglets d’Histogram, Waveform & VectorScope — RMB sur un Pane, puis ‘Windows/NewScope/..
> 


> [!info]+ Color Picker
> **Color-Picker** : Dans le Viewer, lorsque vous faites un CTRL+LeftMouseButton sur un pixel (ou un ensemble de pixels), vous aurez un petit carré rouge, dont les valeurs sont analysées par le Color-Picker. Elles sont affichées en temps réel en bas du Viewer, sur la partie droite de la barre d’information inférieure.
> 
> *Il est aussi possible de changer le mode d’affichage des valeurs color-pickées en Spotmeter, valeurs 8bits, 8bit Hex, Log & HSVL*
> *Il est possible de faire une sélection de multiples pixels avec: GAUCHE—CTRL+SHIFT+LeftMouseClick = Rectangle de sélection; ————————————-——— DROITE—CTRL+LeftMouseClick = Stroke (coup de brosse) de pixels*
> 


> [!NOTE]+ Pixel Analyzer
> **Pixel Analyzer :** Le PixelAnalyzer est une version avancée du Color-Picker, qui permet de déterminer et afficher plusieurs valeurs à partir de zones sélectionnées par le Color-Picker!
> Il permet de venir afficher: 
> 
> - **“Min”** — Valeurs de pixels les plus basses de la sélection; 
> - **”Max”** — Valeurs de pixels les plus hautes de la sélection; **
> - ”Average”** — Valeur moyennes des pixels de toute la sélection; 
> - **”Median”** — Valeur médiane dex pixels de toute la sélection;
> 
> > [!warning] ⚠️ Différence entre “Average” et “Median” ⚠️:
> > ”Average” = Somme de toutes les valeurs divisées par la quantité de valeurs samplées de la sélection; ”Median” = Valeurs se situant au milieu, entre la valeur minimale et la valeur maximale des valeurs samplées de la sélection;

---
#### Méthodologie de Color-Grading logique

###### 0. AJUSTER LE COLORSPACE DE L’INPUT 

Utiliser le Colorspace ou le OCIOColorSpace afin de convertir l’Input vers l’espace colorimétrique de travail pour le Compositing (optionnel si les éléments sont déjà dans ce ColorSpace)

###### 1. AJUSTER LE CONTRASTE

⚠️ Eviter le “ColorCorrect.Contrast” car il aplatit trop les valeurs ⚠️

> [!tip]+ Technique 01, basique : Node: Grade
> Augmenter le Contraste: Baisser la valeur de Grade.[[3_GARDEN/Notes permanentes/Gamma\|Gamma]] & Augmenter la valeur de Multiply
> Baisser le Contraste: Augmenter la valeur de Grade.[[3_GARDEN/Notes permanentes/Gamma\|Gamma]] & Baisser la valeur de Multiply
> 
> ![Screenshot_30a.webp](/img/user/Pi%C3%A8ces%20jointes/Screenshot_30a.webp)
> 
> *Le “Gamma” contrôle la quantité de Constraste, et “Multiply” est un multiplicateur linéaire des valeurs de chacun des pixels.*
> 

> [!tip]+ Technique 02, avancée, qui garde la Saturation & la Hue : Nodes: Colorspace, Grade
> On convertit l’image Linear en HSV (Hue/Saturation/Value), puis Grade le Channel BLUE (Value) pour en éditer le contraste, avant de reconvertir le HSV en Linear!
> 
> ![Screenshot_29a.webp](/img/user/Pi%C3%A8ces%20jointes/Screenshot_29a.webp)
> 
> *On décoche “red” et “green” du Grade, et bouge les potards “Blackpoint” et “Whitepoint” afin d’ajuster le Contraste de la luminosité. Puis on reconvertit l’info HSV en Linear.*
> 

###### 2. AJUSTER LA CHROMINANCE & TEINTE:

Lorsque le contraste d’un élément est match à une Plate, il est important d’ajuster sa chrominance avec la teinte des lumières directes/indirectes de l’environnement. Cela sert également parfois à ajuster un Texturing/LookDev trop peu crédible, et aider à mieux vendre l’image.

Ajuster la couleur dans le multiply ou le gamma d'un grade

###### 3. AJUSTER L’INTENSITE LUMINEUSE:

L’intensité lumineuse est en lien direct avec la luminance de chaque pixel de l’élément. En photographie, l’exposition relative (=quantité de lumière) est exprimée via l’unité de “Stop” de lumière. Un “Stop” de lumière est aussi appelé “EV” (Exposure Value).

> [!NOTE]+ Technique visuelle : Avec un grade
> Node: Grade — Ajuster le paramètre “Multiply” ou “Gain”; Ces deux paramètres ont un effet identique, mais ont un nom différent

> [!NOTE]+ Technique photographique : via le node ‘Exposure’
> Node: Exposure — Ajuster le paramètre “RGB - Red/Green/Blue” (possibilité de décocher “gang” pour ajuster l’exposure de chaque Channel individuellement); 
> *L’Exposure (en Stops) à une valeur de 2 correspond bien à la même intensité lumineuse qu’un Gain à valeur de 2²=4.*

###### 4. DEBOUCHER LES BASSES-LUMIERES / LES OMBRES: 

Node: Toe — Ajuster le paramètre “Lift”; Contrairement au BlackPoint du Grade, le Toe.Lift n’écrase pas les basses valeurs, et préserve également le reste de la courbe colorimétrique.

> [!tip] Effectuer une opération inverse au “Toe” & atténuer les hautes valeurs:
> Mettre un Invert avant & après un “Toe”
> 
> ![ColorIntegration_03j.jpg.webp](/img/user/Pi%C3%A8ces%20jointes/ColorIntegration_03j.jpg.webp)
> 

#### Méthodologie de Color-Grading artistique et sand box

Si vous souhaitez avoir une approche plus créatique/empirique, ou que vous souhaitez avoir les full-powers afin de manipuler la donnée en détail; Voici d’autres nodes de Color-Grading:

|NODE **NAME (**⭐: fav)|CATEGORY|LINK||DESCRIPTION|
|---|---|---|---|---|
|**ColorCorrect**|General|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colorcorrect.html)||Ajustements à Tirettes pour de multiples possibles sur des plages de données multiples (master, shadows, midtones & highlights) pour la Saturation, Contrast, Gamma, Gain & Offset;|
|**ColorLookup**|General|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colorlookup.html)||Ajustements à Curves (base LUT) pour le Contrast, Gamma, Gain & Offset;|
|**Gamma**|General|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/gamma.html)||Ajustement à Tirette du Gamma;|
|⭐ **Colorspace**|ColSpace|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colorspace.html)||Conversion de l’Input d’un Colorspace à un autre;|
|⭐ **OCIOColorSpace**|ColSpace|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/ociocolorspace.html)||Conversion de l’Input d’un ColorSpace à un autre;|
|**OCIOLogConvert**|ColSpace|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/ociologconvert.html)||Conversion de l’Input du ColorSpace ‘compositing_log’ vers ‘scene_linear’;|
|**HSVTool**|Hue-Sat|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/hsvtool.html)||Ajustements à Tiretes pour la Hue, Saturation & autres contrôles spécifiques à la Chrominance -peu recommandé-;|
|**HueCorrect**|Hue-Sat|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/huecorrect.html)||Ajustements à Curves (base LUT) pour les niveaux de saturation & les plages de Hue;|
|**HueShift**|Hue-Sat|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/hueshift.html)||Ajustements à Tirettes pour la Hue, Saturation & autres contrôles spécifiques à la Crominance -recommandé-;|
|**Saturation**|Hue-Sat|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/saturation.html)||Ajustements à Tirettes pour la Saturation;|
|⭐ **Clamp**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/clamp.html)||Contraint les valeurs des channels sélectionnés sur une plage de valeurs minimale & maximale;|
|**Add**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/add.html)||Ajout d’une valeur linéaire réelle;|
|**ColorMatrix**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colormatrix.html)||Multiplie les valeurs RGB par une matrice à entrée 3x3;|
|**ColorTransfer**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colortransfer.html)||Automation de transfer des couleurs d’un Input A vers un input B;|
|⭐ **Expression**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/expression.html)||Application d’expressions TCL aux valeurs RGB — ExpressionVide=0 — rsrc: [https://www.gatimedia.co.uk/expressions](https://www.gatimedia.co.uk/expressions);|
|**HistEQ**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/histeq.html)||Equalise l’histogramme de l’Input;|
|⭐ **Invert**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/invert.html)||Inverse les valeurs de l’Input ( ValeurPixelSortie = 1/ValeurPixelEntrée );|
|**Multiply**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/multiply_color.html)||Multiplie les valeurs d’un Input par un facteur donné;|
|**Posterize**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/posterize.html)||Réduit la résolution colorimétrique (= échantillonnage) d’un Input, par une quantité de valeurs possibles donnée;|
|**Sampler**|Utils|[**link**](https://learn.foundry.com/nuke/content/reference_guide/color_nodes/colorcorrect.html)||Analyse l’Input & affiche un historique sous forme de ligne de balayage (scanline);|
|**SliceTool**|Utils|[**link**](http://www.nukepedia.com/gizmos/other/slicetool)||Permet de visualiser l’histogramme de l’Input sous forme de ligne de balayage (scanline);|


## Références 

## Liens 
