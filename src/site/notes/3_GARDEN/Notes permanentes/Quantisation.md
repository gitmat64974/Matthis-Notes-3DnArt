---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Quantisation/","tags":["note_permanente"],"dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":null,"aliases":null}}
---

## La note 

La **quantification** (ou _quantization_), c'est simplement l'art de transformer une valeur continue et lisse (comme une pente) en paliers discrets (comme un escalier). En 3D, on l'utilise souvent pour créer des effets de "snap", de voxels ou de terrasses.

 On va utiliser la fonction `trunc()` : elle coupe tout ce qui se trouve après la virgule
Mais on ne l'utilisera pas toute seule car elle ne permet pas un vrai contrôle sur la taille des "marches". En effet : 

- Si tes valeurs sont minuscules (ex: $0.002$), elles deviennent toutes $0$. L'information est détruite.
- Si elles sont immenses (ex: $4000.5$), l'effet d'escalier (qui se fera de $1$ en $1$) sera visuellement imperceptible.

La solution mathématique élégante consiste à **diviser, tronquer, puis remultiplier**.

### L'astuce mathématique

Pour forcer une valeur à s'aligner sur une "taille de marche" précise (le facteur $f$), on utilise cette logique :

  

$$V_{\text{quantifié}} = \text{trunc}\left(\frac{V}{f}\right) \times f$$

Imaginons que nous voulons des marches d'une taille de **$0.5$**. Voici comment cette formule transforme différentes valeurs continues pour les grouper sur des paliers :

  

|**Valeur originale (V)**|**1. Diviser (V/0.5)**|**2. Tronquer (trunc)**|**3. Multiplier (×0.5)**|
|---|---|---|---|
|**$1.1$**|$2.2$|$2$|**$1.0$**|
|**$1.4$**|$2.8$|$2$|**$1.0$**|
|**$1.6$**|$3.2$|$3$|**$1.5$**|

Toutes les valeurs comprises entre $1.0$ et $1.49$ sont "aimantées" sur le palier $1.0$. Dès qu'on atteint $1.5$, on passe à la marche suivante.

  

### Exemple en VEX

Voici le code sommaire qu'on pourrait utiliser en VEX
```C
// 1. On calcule la distance du point par rapport à l'origine (0,0,0).
float d = length(@P); 

// 2. On multiplie cette distance par un paramètre 'scale'.
// Cela permet d'accentuer ou de réduire la pente globale avant de la découper.
d *= ch('scale'); 

// 3. On crée un slider 'factor'. C'est lui qui définit la hauteur exacte de nos marches d'escalier.
float f = ch('factor'); 

// 4. L'algorithme de quantification :
d /= f;        // On divise pour adapter l'échelle à notre taille de marche
d = trunc(d);  // On coupe les décimales (création des paliers plats)
d *= f;        // On remultiplie pour retrouver les proportions d'origine

// 5. On applique cette nouvelle valeur "en escalier" à la position Y (la hauteur) du point.
@P.y = d;
```

**Le résultat visuel :** Si tu appliques ce code (dans un _Point Wrangle_) sur une géométrie de type _Grid_, au lieu d'obtenir un cône parfaitement lisse qui s'élève depuis le centre, tu obtiendras une pyramide à degrés (comme un temple maya ou des rizières en terrasses). En bougeant le slider `factor`, tu pourras ajuster la hauteur de chaque terrasse en temps réel.


## Références


> [!example]- Flashcards
> ...




## Liens 




