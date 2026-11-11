---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Kernel/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[SOLARIS]]","[[HOUDINI]]"],"source":["Recherche agent du 2026-11-11 — doc SideFX : [Karma XPU pre-compiling (H21)](https://www.sidefx.com/docs/houdini/solaris/support/karma_precompile.html)"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-11","aliases":["Karma XPU kernels","Precompile Karma XPU Render Kernels"]}}
---


## La note

### 1. Un « kernel », de manière générale

En compute GPU, un **kernel** est un programme compilé pour être exécuté directement sur le GPU : le code hôte (CPU) lance le kernel, et le GPU exécute ce programme en parallèle sur des milliers de threads. Contrairement à un binaire CPU, un kernel GPU passe par une **compilation en plusieurs étapes** (ex. pipeline NVIDIA) :

1. source (C++ / VEX / shader graph compilé) → **PTX** (IR vendor-neutral de NVIDIA) ou **OptiX IR**
2. le driver GPU compile ensuite le PTX → **SASS**, le code machine natif de *ta* architecture GPU précise (JIT à l'installation ou au chargement)

C'est cette chaîne de compilation — l'équivalent d'un compilateur C++ complet — qui est coûteuse. Un kernel n'est pas portable de machine en machine : il est compilé pour un modèle de GPU, une version de driver et une version de logiciel donnés.

### 2. Précisément dans Karma XPU

Karma XPU tourne sur deux moteurs : **OptiX** (GPU NVIDIA) et **Embree** (CPU). Au premier rendu, l'appareil OptiX *stall* car il compile des programmes pour le GPU. La doc SideFX distingue explicitement **deux types de programmes** :

| Type | C'est quoi | Compilation |
|---|---|---|
| **Render kernels** | Le code de rendu du cœur de XPU : ray tracing, BVH, échantillonnage, intégration, denoising… Ce code est **spécialisé en fonction des besoins de la scène** (le renderer génère les variantes des kernels correspondant aux features requises). | Lourde : quelques secondes à plusieurs minutes par kernel — c'est lui que le precompile vise |
| **User shaders** | Tes graphes de matériaux (Karma, MaterialX) et light filters, traduits en programmes de shading. | Rapide, compilée à la volée, **non pré-compilable** (impossible d'anticiper l'arrangement des graphes) |

Donc dans ce contexte, « kernel » ≠ « shader » : le render kernel est le moteur de rendu lui-même, généré/compilé comme code natif GPU, et mis en cache par scène « similaire » ensuite.

### 3. Que fait *Pre-compile Karma XPU Render Kernels* (menu Render, H21+)

C'est un processus **entièrement optionnel** qui pré-construit tout le cache de kernels hors rendu :

- il parcourt l'espace des render kernels possibles et les compile **par avance**, en écrivant les résultats de façon incrémentale dans un cache disque — utilisable en plusieurs fois (stop/resume, ça reprend où c'était) ;
- à rendre, si un kernel manque au cache, Karma XPU le compile *on the fly* (d'où le message d'attente en haut à droite du viewport) ;
- il ne sert **que** pour le device OptiX (EmbreeCPU n'en bénéficie pas) et n'a aucune utilité pour Karma CPU ;
- scriptable en headless : `import karma_precompile_xpu; karma_precompile_xpu.run_terminal()` dans un hython ;
- un message au premier lancement de Solaris le propose aussi.

Cache disque, **plusieurs Go**, séparé par version majeure de Houdini :

- Windows : `C:\Users\<user>\AppData\Local\NVIDIA\OptixCache\Houdini21.0`
- Linux : `/var/tmp/OptixCache_<user>/Houdini21.0`

### 4. Pourquoi si long

1. **C'est une vraie compilation native** : chaque kernel est compilé (C++ → IR → code machine GPU), un pipeline équivalent à un build de projet ; en coulisses tu vois des processus `karma_cc.exe` (le compilateur) faire le boulot.
2. **Multiplication des variantes** : le code de rendu est spécialisé selon les features requises — matériaux, volumes, motion blur, denoiser, light filters… Le nombre de kernels à générer explose, d'où un total qui peut atteindre **plusieurs heures** (chiffre officiel SideFX).
3. **Par-device** : un kernel est compilé pour des spécifications système et GPU précises — impossible de partager le cache d'une machine à une autre, SideFX déconseille explicitement un cache réseau.
4. **Dépendant de ta machine** : le temps varie fortement selon CPU/RAM/driver, et pendant la compilation le système peut ralentir fortement (SideFX recommande de sauver le travail et libérer les ressources).

### 5. Faut-il re-precompiler à chaque modification de scène ? **Non.**

Le cache de render kernels **n'est pas invalidé par le contenu de la scène**. Ce qui le déclenche vs pas :

| Événement | Recompile le cache ? |
|---|---|
| Nouvelle installation / upgrade majeure de Houdini | ✅ Oui (cache séparé par version) |
| Mise à jour du driver GPU / composant système | ✅ Oui — bannière `Compiled Render Kernel Cache out of Date` dans le viewport |
| Changer géométrie, lumières, caméra, textures, matériaux existants | ❌ Non — user shaders recompilés à la volée, ils sont rapides |
| Activer une feature jamais utilisée dans une scène | ❌ Pas une invalidation : kernel manquant compilé *on the fly* (stall ponctuel), ensuite caché |

**Workflow recommandé** : lance le precompile une fois après l'install de H21 / chaque mise à jour de driver ou de GPU (idéalement la nuit, via le script hython), oublie-le ensuite — le cache reste valable tant que tu ne changes pas de version de Houdini, de driver ou de GPU. Les micro-pauses à l'ouverture d'une scène avec des matériaux inédits sont les **user shaders**, pas les render kernels : elles ne disparaissent pas avec le precompile, mais sont bénignes. Et pour la farm : inutile, les machines compileraient à la demande ; le precompile ne sert qu'à l'interactivité.

## Références

- [Karma XPU pre-compiling — doc SideFX H21](https://www.sidefx.com/docs/houdini/solaris/support/karma_precompile.html)
- [Karma XPU — doc SideFX](https://www.sidefx.com/docs/houdini/solaris/karma_xpu.html)
- [Menus → entrée Pre-compile + script hython](https://www.sidefx.com/docs/houdini/ref/menus.html)
- [What's new Karma H21](https://www.sidefx.com/docs/houdini/news/21/karma.html)
- [Forum SideFX — karma_cc.exe / threading](https://www.sidefx.com/forum/topic/104348/)

> [!example]- Flashcards
> #3D/rendu
>
> ---
> Dans Karma XPU, quelle différence entre **render kernels** et **user shaders** ?
> ;;
> Render kernels = code de rendu du cœur (ray tracing, BVH, échantillonnage, denoising), compilé en code natif GPU et spécialisé selon les features requises par la scène. User shaders = tes graphes de matériaux / light filters, compilés à la volée (rapides) et **non pré-compilables**.
>
> ---
> Quand le cache de kernels Karma XPU devient-il invalide ?
> ;;
> Nouvelle installation / upgrade majeure de Houdini, mise à jour du driver GPU ou composant système (bannière `Compiled Render Kernel Cache out of Date`). Jamais au changement du contenu de la scène (géométrie, lumières, textures, matériaux) ni à l'activation d'une nouvelle feature (compilation ponctuelle on the fly, puis mise en cache).
>
> ---
> Où est stocké le cache de kernels OptiX de Karma XPU (Houdini 21) ?
> ;;
> Windows : `C:\Users\<user>\AppData\Local\NVIDIA\OptixCache\Houdini21.0` ; Linux : `/var/tmp/OptixCache_<user>/Houdini21.0`. Plusieurs Go, séparé par version majeure de Houdini, non partageable entre machines.

## Liens

- [[3_GARDEN/Notes permanentes/LPE|LPE]] — autre brique de knowledge Solaris/Karma liée aux AOVs
- [[3_GARDEN/Notes permanentes/Render threads optimization Karma|Render threads optimization Karma]] — optimisation d'un autre goulet de rendu Karma
- [[3_GARDEN/Notes permanentes/Light Filters Solaris|Light Filters Solaris]] — les light filters font partie des *user shaders* compilés à la volée
- [[3_GARDEN/MOCs/USD|USD]] — Karma rend l'USD produit par Solaris ; le cache de kernels, lui, ne dépend pas du contenu USD
- Connexion croisée : même logique de JIT-compilation de kernels que dans l'infographie temps réel (moteurs de jeux qui compilent leurs shaders à l'installation ou en « shader warming », dérivés de la spéculation pipeline) — même cause de « stutter » au premier usage.
