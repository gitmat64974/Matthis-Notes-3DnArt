---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/MARI - Procedural Skin Imperfection/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[SHADING TEXTURING]]","[[MARI]]"],"source":["[[Cours de lighting rendu ESMA]]","https://youtu.be/LbKCVhkQRfs?si=zRsLGidEM2z3LV0A"],"Projets":["[[ESMA project skin texturing intro MARI]]"],"tags":["note_permanente"],"creation date":"2025-10-31","aliases":["Mari, Blood texturing","Mari, Scar texturing"]}}
---

## La note 

> [!info]- Les 3 couches de la peau : 
> - **Épiderme**
>     - Couche la plus externe de la peau.
>     - Sert de barrière protectrice contre l’environnement.
>     - Contient la couche cornée (autre sous-couche de l’épiderme).
> - **Derme**    
>     - Situé sous l’épiderme.
>     - Renferme la majorité des composants structurels : vaisseaux sanguins, nerfs, glandes sudoripares, follicules pileux.
>     - Apporte élasticité et résistance grâce au collagène.  
> - **Hypoderme** (ou tissu sous-cutané) 
>     - Couche la plus profonde
>     - Constituée principalement de tissu adipeux  
>     - Rôle d’isolant thermique et de réserve énergétique.

**Deux types d’imperfections** : 

| Ajout d’un matériau sur la peau                                                                    | Altération du matériau de la peau elle-même                                   |
| -------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| ![Capture d'écran 2025-10-31 122815.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-10-31%20122815.png)                                                         | ![Capture d'écran 2025-10-31 122829.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-10-31%20122829.png)                                    |
| *(ex : maquillage, sang, boue) — avec identité de matériau et reliefs propres, ajoutés à la peau.* | *(ex : boutons, cicatrices, tatouages) — relief mélangé et identité modifiée* |

#### Le process dans MARI

**1. Concept et Création d'un masque ISO :**

- Un _masque ISO_ (isolation channel) sert à isoler des zones spécifiques de la texture pour piloter différents effets ou comportements sur la peau.
- Il est essentiel d'utiliser un pinceau avec une **petite douceur sur les bords** (brush smoothness). Cela crée un dégradé : au centre du coup de pinceau la valeur est élevée et elle s’atténue vers les bords.
- Ce dégradé est indispensable car il permet aux nodes _Brightness Lookup_ d’isoler des plages de valeurs spécifiques pour piloter différents effets sur la peau.

**2. Utilisation des nodes "Brightness Lookup" :**

- Le node _Brightness Lookup_ (filtre de courbe) permet soit :
    - De grader la valeur du masque (contraste global)
    - D’isoler une plage de valeurs du masque (par exemple, pour cibler uniquement les contours d’une cicatrice ou une zone précise)
- Il faut créer plusieurs "Brightness Lookup" avec des courbes différentes pour chaque effet désiré :
    - Un pour la zone centrale
    - Un pour le contour
    - Un pour inverser le masque, etc.

**3. Application des masques ISO dans les différents channels :**

- Chaque masque ISO piloteras d’autres nodes pour chaque channel à modifier :
    - _Displacement_ (relief, bosses/cicatrices)
    - _Color_ (décoloration/inflammation autour d’une cicatrice)
    - _Specular/Roughness_ (rugosité, brillance)
- Par exemple, pour une cicatrice :
    - Le masque ISO passe dans plusieurs _Brightness Lookup_ qui isolent différentes parties de la cicatrice (centre, bords, croûte...)
    - Chaque plage de valeurs pilote un node "merge" qui applique une couleur ou une valeur de relief différente.

**4. Ajustements dynamiques et contrôle du look :**

- Tout l’intérêt est de pouvoir ajuster, en temps réel, ses _Brightness Lookups_ en fonction de ce qu’on voit dans le shader.
- Il est conseillé d’exporter ses maps, tester dans le logiciel de rendu final, puis revenir dans MARI pour ajuster les courbes des masques ISO.

### Cas concrets : 

#### Scars

Le masque ISO : 
On merge avec une texture tilée pour plus de richesse et de réalisme

![Capture d'écran 2025-11-11 110251.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20110251.png)

Color : 

On vient isoler les bords, le centre etc pour les traiter séparément 

![Capture d'écran 2025-11-11 110718.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20110718.png)

Displace : 
Idem

![Capture d'écran 2025-11-11 110532.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20110532.png)

#### Sang

Masque ISO : 

On a 2 masques : Blooddrop et splashes

![Capture d'écran 2025-11-11 112319.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20112319.png)

![Capture d'écran 2025-11-11 112334.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20112334.png)

Color : 

On a 2 colors : un rouge clair pour quand le sang est fin (splashes etc) et un rouge foncé pour quand le sang est épais (coulure)

![Capture d'écran 2025-11-11 112458.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20112458.png)


Displace : 

Légèrement de displace sur les splashes et plus sur les drops


![](https://i.imgur.com/SRxW8WW.png)

#### Tatoo / makeup

Colo : 
On récupère un peu de la valeur de la peau + texture triplanaire pour richesse et réalisme

![Capture d'écran 2025-11-11 121605.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20121605.png)

disp : 
Simplement ajouter un peu de displace avec un merge et un constant (comme tous les setup plus haut mais en beaucoup plus simple)

dispRGB : 
On vient enlever un peu des infos de disprgb car un tatoo ou un makeup "smooth" un peu la peau



## Références

Le template mng : (explication mng : [[3_GARDEN/Notes permanentes/MARI Projects et MARI Archives|MARI Projects et MARI Archives]])
![[MARI_TEMPLATE_v01.mng]]

> [!example]- Flashcards
> ...




## Liens 




