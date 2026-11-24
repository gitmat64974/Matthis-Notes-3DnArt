---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/BlinkScript/","tags":["note_permanente"],"ctime":"2026-11-19T10:20:28.789+01:00","mtime":"2026-11-18T21:07:29.078+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["https://learn.foundry.com/nuke/Content/comp_environment/blinkscript/image_processing_blink.html","https://learn.foundry.com/nuke/developers/17.1/BlinkUserGuide/BlinkKernelAPIReference.html","https://beforesandafters.com/2020/02/20/a-visual-history-of-nuke/"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-18","aliases":["Blink","Blink Script","Kernel Blink"]}}
---


## La note 

**BlinkScript** est le node de Nuke dans lequel on **écrit du code pour créer son propre effet d'image** — un blur custom, un glitch, un swirl, un outil qu'aucun node natif ne sait faire — sans quitter Nuke et sans écrire de plugin C++.

#### Ce que c'est vraiment

- Le node fait tourner le framework **Blink** de Foundry : un langage proche de C++, spécialisé traitement d'image, dont la promesse est *write once, run on any device*. Le code n'est jamais interprété : il est **traduit puis compilé à la volée** — en C++/SIMD pour le CPU, en OpenCL ou CUDA pour le GPU. On bascule CPU↔GPU d'un clic sans toucher au code.
- Un **[[3_GARDEN/Notes permanentes/Kernel\|kernel]]** est une sorte de classe C++ dont la fonction `process()` est exécutée une fois **pour chaque pixel** (`ePixelWise`) ou **pour chaque composante** (`eComponentWise`) de l'image de sortie, massivement en parallèle, sans ordre garanti (chaque exécution est indépendante). L'espace d'itération suit la résolution de la sortie : un kernel component-wise sur une UHD RGBA = 3840×2160×4 exécutions.
- Les `param` deviennent automatiquement des knobs de l'onglet *Kernel Parameters* : float → slider, int → champ animable, bool → checkbox, float2/3/4 → vecteur/couleur, tableaux/matrices → champs multiples. L'artiste règle l'effet sans lire une ligne de code.
- Historique : le framework Blink est au cœur de Nuke depuis Nuke 7 (2012, premières bases GPU) ; le **node BlinkScript** arrive avec Nuke 8 (2013) ; Nuke 12.1 (2020) ajoute **ParticleBlinkScript** (kernels sur les particules) ; Nuke 16 (2024) ajoute Safety Rails, Bake/Protect et les Library Files ; Nuke 16.1 ajoute des macros de version de Nuke pour conditionner le code.

#### Comment on l'utilise dans Nuke (workflow précis)

1. **Créer le node** : Tab dans le node graph → « BlinkScript » (menu *Other*). L'input s'appelle `src`. Le node arrive pré-rempli avec le kernel d'exemple **SwirlomaticKernel** (un swirl) — le premier réflexe est d'ouvrir son code et de le lire.
2. **Onglet BlinkScript** : c'est là que vit le code. Éditeur avec coloration, auto-complétion (Tab), find/replace, recompilation au **Ctrl+Entrée** ou bouton *Recompile* ; les erreurs de compilation s'affichent directement dans l'éditeur. *Load/Save* via le champ *Kernel File* — extension officielle **.rpp** ; des fonctions réutilisables peuvent vivre dans des **Library Files (.blib)**.
3. **Onglet Kernel Parameters** : auto-généré depuis le kernel — les knobs de l'effet (Swirlomatic : Amount, Radius, Centre), le mapping des **Inputs** (quelles layers/canaux de l'input alimentent chaque image `eRead`), l'**Output** (canaux écrits), **Use GPU if available** (+ *Local GPU*), **Vectorize on CPU** (SIMD), **Safety Rails** (garde-fous contre les accès mémoire hors-limites pendant le dev), format de sortie.
4. **Développer** : connecter le footage, observer dans le viewer, modifier `process()`, *Recompile*, itérer. ⚠️ Le code kernel n'est pas sandboxé : Foundry prévient explicitement qu'un kernel buggé peut **crasher Nuke** — garder les Safety Rails pendant le dev et sauver le script avant les tests audacieux.
5. **Partager / industrialiser** : publier le kernel dans un Group → sauver en **gizmo** ; **Bake** cache les Library Files dans le node (copier-coller facile) ; **Protect** chiffre le kernel pour protéger l'IP ; *Make Live* repasse en mode édition.
6. **Rendre** : GPU si dispo, sinon fallback CPU transparent ; en rendu command-line/farm, ajouter **`--gpu`** pour activer le GPU.
7. **Cas d'usage réels** (les exemples officiels donnent le ton) : box blur 1D/2D custom, flou pondéré par une deuxième image, médian 5×5, swirl, rideau/ripple, lens flare **généré sans aucun input** (le kernel crée l'image), effet de transition entre deux plans, resize en deux passes. En production : outil de prototypage, effets maison, portage d'idées venues d'ailleurs (VEX, shaders).

#### Le kernel « Hello World » — Invert

Ce kernel de base inverse simplement les couleurs de l'image
```cpp
kernel Invert : ImageComputationKernel<eComponentWise>
{
  Image<eRead> src;    // input
  Image<eWrite> dst;   // sortie unique

  param:
    float multiply;            // deviendra un knob

  local:
    float whiteAccessPoint;    // interne, non exposé

  void define() {
    defineParam(multiply, "Multiply", 1.0f);
  }

  void init() {
    whiteAccessPoint = 1.0f;
  }

  void process() {
    dst() = (whiteAccessPoint - src()) * multiply;
  }
};
```

Lecture : chaque composante est traitée pour elle-même (`eComponentWise`, rapide quand les canaux ne se mélangent pas) ; `src()` lit la valeur courante en entrée, `dst()` écrit la sortie ; `Multiply` apparaît comme un knob animable dans le node. Pour un flou, on passerait `src` en `eAccessRanged2D` et on bouclerait sur le voisinage dans `process()`.

## Références

- [Guide to Writing Blink Kernels](https://learn.foundry.com/nuke/developers/17.1/BlinkUserGuide/BlinkKernelAPIReference.html) — la référence complète : kernels, granularité, images et accès, params/knobs, syntaxe et restrictions du langage, debugging.
- [Using the BlinkScript Node](https://learn.foundry.com/nuke/Content/comp_environment/blinkscript/image_processing_blink.html) + [Quick Start](https://learn.foundry.com/nuke/content/comp_environment/blinkscript/quickstart.html) + [Using and Writing Kernels](https://learn.foundry.com/nuke/Content/comp_environment/blinkscript/use_write.html) — workflow utilisateur, éditeur, .rpp/.blib, licence NukeX pour éditer/sauver les kernels.
- [Reference guide — BlinkScript](https://learn.foundry.com/nuke/Content/reference_guide/other_nodes/blinkscript.html) — tous les knobs (Use GPU, Vectorize on CPU, Safety Rails, Library Files, Bake/Make Live/Protect), `--gpu` en rendu.
- [A visual history of Nuke](https://beforesandafters.com/2020/02/20/a-visual-history-of-nuke/) — BlinkScript ajouté avec Nuke 8 (2013), GPU dès Nuke 7 (2012).
- [Foundry Insights — ParticleBlinkScript (Nuke 12.1)](https://foundry.com/insights/film-tv/particle-blink-script-nuke) — kernels sur particules.
- Exemples officiels de kernels (blurs, swirl, flare, transition, resize 2-pass…) : Blink Developer's Guide → *Examples*.

> **Source** : documentation officielle Foundry (Nuke 17.1v3, consultée le 18/11/2026) + beforesandafters.com + Foundry Insights.

> [!example]- Flashcards
> #logiciel/nuke
>
> ---
> À quoi sert le node BlinkScript dans Nuke ?
> ;;
> Écrire du code (un kernel) directement dans Nuke pour créer son propre effet d'image, exécuté en parallèle sur CPU ou GPU, puis utilisable comme un node normal (ou un gizmo) par les artistes.
>
> ---
> Différence entre eComponentWise et ePixelWise ?
> ;;
> eComponentWise : process() tourne composante par composante (aucune dépendance entre canaux → le plus rapide). ePixelWise : accès à toutes les composantes du pixel à la fois (nécessaire dès que les canaux interagissent, ex. saturation).
>
> ---
> Que doit obligatoirement contenir un kernel Blink dans un BlinkScript ?
> ;;
> Au moins une image de sortie (`Image<eWrite>`, unique dans BlinkScript) et une fonction `process()`.

## Liens 

- [[3_GARDEN/Notes permanentes/Pixel\|Pixel]] et [[3_GARDEN/Notes permanentes/Couches d'une image numérique\|Couches d'une image numérique]] — l'unité que le kernel transforme, composante par composante.
- [[3_GARDEN/Notes permanentes/Node graph Nuke\|Node graph Nuke]] — où vit le node dans le graphe, et comment l'insérer.
- [[3_GARDEN/Notes permanentes/Creation de Gizmo Nuke\|Creation de Gizmo Nuke]] — l'étape publish → Group → gizmo qui industrialise un kernel.
- [[3_GARDEN/Notes permanentes/Kuwahara gizmo for nuke\|Kuwahara gizmo for nuke]] — un effet custom d'atelier ; le genre d'outil qu'un BlinkScript sait fabriquer.
- [[3_GARDEN/Notes permanentes/Types de flous\|Types de flous]] — les flous custom (box 1D/2D, pondéré) sont LE cas d'usage classique des kernels.
- [[3_GARDEN/Notes permanentes/VEX\|VEX]] — l'équivalent conceptuel côté Houdini : décrire une formule appliquée à chaque unité plutôt que painter l'effet.
- [[3_GARDEN/Notes permanentes/Optimisation des temps de rendu\|Optimisation des temps de rendu]] — GPU vs CPU, Vectorize on CPU, Safety Rails à couper en production.

*Émergence* : BlinkScript comble le vide entre « artiste qui règle des knobs » et « développeur qui écrit un plugin C++/NDK » : on écrit une formule de pixel en pseudo-C++, Foundry la compile pour chaque device, et l'effet devient un node anonyme. C'est exactement la philosophie des shaders GPU de toute l'industrie (VEX, GLSL, OSL) — apprendre Blink, c'est apprendre un réflexe transversal des outils de 3D/comp.
