---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Code VEX pour créer une curve smooth à partir de 2 points/","tags":["note_permanente"],"ctime":"2026-04-06T00:00:37.000+02:00","mtime":"2026-04-06T00:00:37.000+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/MODELISATION]]"],"source":["Prof FX","Perplexity"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-03-10","aliases":null}}
---


## La note 

Code VEX pour créer une curve smooth selon 2 points et leurs normals 

Résultat : 

| ![](https://i.imgur.com/XBLqitB.png) | ![](https://i.imgur.com/baJCWxU.png) |
| ------------------------------------ | ------------------------------------ |

```C
int pts[];

// Exécuter une seule fois (sur point 0 uniquement pour éviter doublons)
if(@ptnum==0){
// Récupérer positions et normales des 2 points originaux
vector P0 = point(0,"P",0);
vector P1 = point(0,"P",1);
vector N0 = normalize(point(0,"N",0));  // Normaliser explicitement
vector N1 = normalize(point(0,"N",1));

float len = distance(P0, P1) * chf("tension");  // Tension = 0.3 par défaut
vector T0 = N0 * len * 0.5;      // Tangente SORTANTE de P0
vector T1 = -N1 * len * 0.5;     // Tangente ENTANTE vers P1 (inversée)

// Générer 20 points sur courbe Hermite cubique
int nseg = chi("segments");  // Paramètre int = 20
pts = {};
for(int i=0; i<=nseg; i++){
    float t = float(i)/nseg;
    float t2 = t * t;
    float t3 = t2 * t;

    // Formule Hermite standard: h00*P0 + h10*T0 + h01*P1 + h11*T1
    float h00 = 2*t3 - 3*t2 + 1;
    float h10 = t3 - 2*t2 + t;
    float h01 = -2*t3 + 3*t2;
    float h11 = t3 - t2;

    vector pos = h00*P0 + h10*T0 + h01*P1 + h11*T1;
    int pt = addpoint(0, pos);
    setpointattrib(0, "N", pt, normalize(lerp(N0, N1, t)));  // Normales interpolées
    append(pts, pt);
}

// Créer primitive polyline fermée/non
int prim = addprim(0, "polyline", pts);
setprimattrib(0, "closed", prim, 0);

// Supprimer les 2 points originaux
removepoint(0, 0);
removepoint(0, 1);

}
```

### Explications du code


#### 1. Préparation (lignes 4-5)

```C
int pts[];   if(@ptnum==0){
```

- `int pts[]` : Crée une **liste vide** pour stocker tous les nouveaux points de la courbe
- `if(@ptnum==0)` : **Exécute le code UNE SEULE FOIS** (seulement sur le premier point) pour éviter de créer 2 courbes identiques
    

#### 2. Récupérer les données des 2 points (lignes 7-10)

```C
vector P0 = point(0,"P",0);  // Position point 0 
vector P1 = point(0,"P",1);  // Position point 1   
vector N0 = normalize(point(0,"N",0));  // Normale point 0 (direction) 
vector N1 = normalize(point(0,"N",1));  // Normale point 1 (direction)
```

**Comme si on disait :** "Va chercher la position (xyz) et la direction (normale) de mes 2 points de départ"

#### 3. Calculer les "poignées de courbure" (lignes 12-14)

```C
float len = distance(P0, P1) * chf("tension"); vector T0 = N0 * len * 0.5;      // ← Courbure SORT du point 0 
vector T1 = -N1 * len * 0.5;     // ← Courbure ENTRE au point 1
```

**Analogie simple :** Les normales `@N` sont comme des **flèches** sur chaque point. On les transforme en **"poignées"** (T0, T1) qui tirent la courbe dans la bonne direction. Le `-` sur T1 inverse la flèche du point 1 pour qu'elle "tire vers l'intérieur".

#### 4. Générer les points de la courbe (lignes 16-28)

```C
for(int i=0; i<=nseg; i++){  // Boucle 21 fois (0 à 20)     
float t = float(i)/nseg;  // t=0 (début) → t=1 (fin)
```

**La magie Hermite** (formule mathématique) :
La formule hermite est en gros la formule qui permet de créer les courbes de bézier : manipulation de curves par des poignées, garantissant leur aspect lisse. 

```C
float h00 = 2*t3 - 3*t2 + 1;  // Poids point 0 
float h10 = t3 - 2*t2 + t;    // Poids poignée 0   
float h01 = -2*t3 + 3*t2;     // Poids point 1 
float h11 = t3 - t2;          // Poids poignée 1
```

**Résultat** : `pos` = mélange intelligent de P0+P1+poignées → **chaque point bouge selon les normales !**

#### 5. Créer la ligne finale (lignes 30-34)

```C
int prim = addprim(0, "polyline", pts);  // Relie tous les points 
setprimattrib(0, "closed", prim, 0);     // Ligne ouverte 
removepoint(0, 0);                       // Supprime anciens points removepoint(0, 1);
```





## Références


> [!example]- Flashcards
> ...




## Liens 




