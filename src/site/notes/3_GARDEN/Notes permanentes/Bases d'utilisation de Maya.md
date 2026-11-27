---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Bases d'utilisation de Maya/","tags":["note_permanente","plante"],"ctime":"2026-03-22T12:15:21.651+01:00","mtime":"2026-11-08T18:09:22.256+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/MODELISATION]]"],"source":["#cours [[Cours de modélisation ESMA]]"],"Projets":null,"tags":["note_permanente","plante"],"creation date":"2023-10-01","aliases":null}}
---


## La note 

### I. Configuration du projet

Dans Mes documents, Maya va créer un dossier appelé MAYA. Ce dossier contient le dossier projet : c'est là que l'on place les projets. Les fichiers Maya sont des scènes, qui se trouvent dans un dossier de projet.

- **Sécurité de projet** :
    1. Définir d'abord le projet avec `File -> Set Project` avant d'ouvrir une scène
    2. Ouvrir ensuite la scène via `File -> Open...`

![Pièces jointes/d0d38414b673f12837772bf6d8469ba4_MD5.png](/img/user/Pi%C3%A8ces%20jointes/d0d38414b673f12837772bf6d8469ba4_MD5.png)

![Pièces jointes/2f42a37c88b99dffc1aa3f5fe4549d17_MD5.png](/img/user/Pi%C3%A8ces%20jointes/2f42a37c88b99dffc1aa3f5fe4549d17_MD5.png)

Maya permet d'utiliser des workspaces. Par précaution (par exemple si l'on déplace les fenêtres n'importe comment), on peut sauvegarder un fichier par défaut comme workspace via `New windows - workspaces`.

### II. Navigation et vues (Hotkeys)

**Navigation** :
- Alt + LMB : Orbite
- Alt + MMB : Translation latérale/Pan
- Alt + RMB : Avant/Arrière

**Fonctions supplémentaires** :
- Ctrl + M : Afficher/masquer les menus généraux (hotbox)
    - Contient tous les menus principaux de Maya
- Shift + M : Accès aux commandes spécifiques par type (onglets de la fenêtre)

### III. Outils de transformation

| Hotkey | Fonction |
| --- | --- |
| W | Translate/Move Tool |
| E | Rotate Tool |
| R | Scale Tool |

**Opérations importantes** :

- **Freeze Transformation** :
    1. Sélectionner l'objet
    2. Utiliser `Modify -> Freeze Transformations`
    - L'opération convertit les valeurs actuelles de translation, rotation et scale en valeurs fixes à 0

### IV. Mesures et distances (Hotkeys)

- Ctrl + D : Dupliquer une sélection
- +/- : Changer la taille du manipulateur
- **Navigation** : `W + LMB` pour déplacer l'outil Translate après avoir sélectionné un mode

### V. Affichage des informations de maillage

**Nb de points** : `Display -> Heads-up Display -> Poly Count`.

**Détails objets** :
1. Ouvrir `Display -> Heads-up Display -> Object Details`
2. La première colonne affiche les caractéristiques de tous les objets sélectionnés
3. La deuxième colonne affiche celles de l'objet sélectionné actuellement

### VI. Gestion d'objets et modèles

**Edge loops** :
- Soften edges : pour créer des arrondis automatiques
- Insérer une edge loop : `Mesh -> Insert Edge Loop Tool`

**Arêtes frontières** :
- `Select -> Boundary Edges`
- Affiche les arêtes situées aux bords de la géométrie

### VII. Déformations et projection

**Shrinkwrap (projection)** :
1. Sélectionner l'objet à projeter
2. Ouvrir `Deform -> Shrinkwrap`
3. Configuration recommandée :
    - Alignement parallèle aux axes bidirectionnel
    - Cliquer sur `Apply` pour exécuter la commande

### VIII. Autres commandes utiles

**Freeze Transformations** : opération pour conserver les valeurs actuelles de transformation comme référence.

**Match Transformation** :
1. Sélectionner l'objet source et destination
2. Ouvrir `Modify -> Match Transformation...`

**Symmetry Tool** :
- Utiliser la commande symétrie dans le menu Modeling (en haut à gauche)
- Permet d'appliquer une transformation en symétrie selon différents axes

### IX. Gestion des sets de sélection

- **Créer un set** : `Create -> Set`
    - Pour ajouter/supprimer des objets : clic droit sur le set > `Select Set Members`

## Références

Notes atomisées depuis cette note :
- [[Set Project dans maya\|Set Project dans maya]] · [[Navigation dans maya\|Navigation dans maya]] · [[Transformations dans maya\|Transformations dans maya]] · [[Manipulateur dans maya\|Manipulateur dans maya]] · [[Heads-up Display dans maya\|Heads-up Display dans maya]]
- [[Freeze transformations dans maya\|Freeze transformations dans maya]] · [[Match Transformation dans maya\|Match Transformation dans maya]] · [[Shrinkwrap dans maya\|Shrinkwrap dans maya]] · [[Arêtes frontières dans maya\|Arêtes frontières dans maya]] · [[Sets de sélection dans maya\|Sets de sélection dans maya]]

Opérations déjà couvertes par des notes existantes : [[3_GARDEN/Notes permanentes/Dupliquer dans maya\|Dupliquer dans maya]] (Ctrl + D), [[3_GARDEN/Notes permanentes/Symétrie dans Maya\|Symétrie dans Maya]] (Symmetry Tool), [[3_GARDEN/Notes permanentes/Multicut dans maya\|Multicut dans maya]] (Insert Edge Loop)
Complément lighting : [[3_GARDEN/Notes permanentes/CG Lights\|CG Lights]]
