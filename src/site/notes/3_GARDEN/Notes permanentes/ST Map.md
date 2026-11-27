---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/ST Map/","tags":["note_permanente"],"ctime":"2026-03-25T20:36:26.430+01:00","mtime":"2026-03-25T20:38:37.520+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes permanentes/AOVs Utilitaires]]"],"Projets":null,"tags":["note_permanente"],"creation date":202503250000,"aliases":["UV Map Nuke","STmap Nuke"]}}
---

## La note

### C'est quoi un STMap ?

Une image où chaque pixel encode une coordonnée écran :
- **Canal R** = position X (0 = gauche → 1 = droite)
- **Canal G** = position Y (0 = bas → 1 = haut)

Le nœud `STMap` dans Nuke utilise ces valeurs pour **remapper les pixels** d'une image source. Un STMap vierge (non modifié) = image de sortie identique à l'entrée *(sanity check indispensable)*.

> [!tip] ST vs UV
> UV = coordonnées texture dans l'espace objet. ST = coordonnées de surface dans l'espace texture (origine Renderman). En pratique dans Nuke : identiques.

---

### Créer un STMap

**Méthode 1 — Expression node** (la plus propre) :
```
r = (x + 0.5) / width
g = (y + 0.5) / height
```
*(le +0.5 centre les coordonnées sur le milieu du pixel)*

**Méthode 2 — 2 Ramp nodes** additionnés :
- Ramp rouge : horizontal, 0→1
- Ramp vert : vertical, 0→1

> [!warning] Export
> Toujours pré-rendre les STMaps en **EXR 32-bit** pour conserver toute la précision.

---

### Setup de base dans Nuke

```
[Image source] → STMap (input 0 / src)
[STMap image]  → STMap (input 1 / stmap)
```

**Réglage obligatoire** : dans le nœud `STMap`, mettre **`UV Channels → rgb`** (la valeur par défaut ne fonctionne pas).

**Améliorer la qualité du warp** :
```
Reformat (x2) → STMap → Reformat (original)
```
Upscaler avant le warp, puis revenir à la résolution d'origine évite les artefacts de filtrage.

---

### Cas d'usage

#### 1. ReTexturing avec l'AOV `__st` *(le cas principal)*

L'AOV `__st` du rendu contient les coordonnées UV de chaque pixel du mesh.

```
[Nouvelle texture]  → STMap (src)
[AOV __st du rendu] → STMap (stmap) — UV Channels: rgb
```

→ La texture s'applique sur le mesh en 2D comme si elle était en 3D, sans re-rendre.

---

#### 2. Lens Distortion portable

Convertir une distorsion propriétaire (3DEqualizer, etc.) en fichier partageable :

```
STMap vierge → LensDistortion node → pré-render EXR 32-bit
```

→ L'EXR remplace le node propriétaire. Partage inter-studios sans dépendance.

---

#### 3. Blend de warps seamless *(avantage clé du STMap)*

Au lieu d'appliquer un SplineWarp ou GridWarp directement sur l'image avec un masque (= ghosting), on l'applique sur un STMap :

```
STMap vierge → SplineWarp/GridWarp (masqué) → blur aux bords → STMap node → image finale
```

**Pourquoi ?** Flouter la STMap dans les zones de transition = les coordonnées se mélangent → résultat seamless, sans ghosting. C'est impossible à obtenir avec un warp direct masqué.

→ Permet de **combiner plusieurs warps** (KeyMix entre STMaps, pas entre images).

---

#### 4. Fix SmartVectors

Quand le VectorDistort est presque bon mais pas parfait :

```
STMap (depuis SmartVectors) → GridWarp (ajustements manuels) → STMap node
```

→ On tweake l'espace de warp sans retravailler le tracking.

---

#### 5. Accélérer la Projection Mapping

Un `ScanlineRender` sur dense géo = lent à recalculer.

```
Project3D + ScanlineRender → pré-render STMap EXR → STMap node sur image finale
```

→ On calcule la 3D une seule fois, puis le STMap s'applique instantanément à chaque frame.

---

### Résumé des nœuds associés

| Nœud | Rôle |
|------|------|
| `STMap` | Applique la map sur une image (UV Channels → **rgb**) |
| `Expression` | Crée un STMap vierge |
| `Reformat` | Upscale avant warp pour la qualité |
| `GridWarp` / `SplineWarp` | Modifie le STMap (pas l'image directement) |
| `KeyMix` | Blend entre deux STMaps |

---

## Références vidéo

- [STMap in nuke : how to use? and when to use?](https://www.youtube.com/watch?v=pwSFZOwTc98)
- [UV / ST Maps Part 2 — Compositing Academy](https://www.youtube.com/watch?v=0A-DC41U09M) *(projection mapping + UV expression)*
- [What to do differently with STMaps — Comp Lair](https://www.youtube.com/watch?v=QYGi_tH5oog) *(warp seamless, application concrète)*

## Liens

- [[3_GARDEN/Notes permanentes/AOVs Utilitaires\|AOVs Utilitaires]]
- [[3_GARDEN/Notes permanentes/Color grading dans NUKE\|Color grading dans NUKE]]
- [[3_GARDEN/Notes permanentes/Atmos NUKE\|Atmos NUKE]]

