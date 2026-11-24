---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Matériaux de base renderman/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.983+01:00","mtime":"2026-04-24T17:43:18.850+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SHADING TEXTURING]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2024-08-19","aliases":null,"Source":["[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]","[[3_GARDEN/Notes littéraires/Using PXR surface]]"]}}
---


## La note

3 Types de matériaux : diélectrique, conductif, transparent

#### Diélectriques et métaux

Diffuse : matériaux diélectriques
Métaux (aussi appelés conducteurs) : diffuse gain à 0 : il n’y a pas de diffusion de la lumière.

Spécular : Dès qu'un matériau est réfléchissant, on peut monter l'edge color au max. Pour un diélectrique, la face color doit être extrêmement basse (et seulement en valeurs de noir et blanc).

Pour un métal : la face color peut aller jusqu’au max et peut être colorée

Pour un résultat le plus correct possible physiquement on peut utiliser le mode physical : voir PXR Surface physical mode)

<font color="#92d050"><u>Les éléments plus particuliers : </u></font>

> [!note] Primary specular Advanced
> [[3_GARDEN/Notes permanentes/Spéculaire\|Specular]] model : beckman → plus effet mirroir ; Ggx → plus effet naturel (à utiliser obligatoirement pour les plastiques)
> 
> Anisotropy : Lorsque les réflections du métal on une certaine direction. L’anisotropy va venir “étaller” les spéculaires soit en longueur soit en largeur en fonction des UVs (-1 jusqu’à +1 en valeur) :
> 
> ![Pièces jointes/40c0dfa1e1d39d7d1ea4cfe6de31780b_MD5.png](/img/user/Pi%C3%A8ces%20jointes/40c0dfa1e1d39d7d1ea4cfe6de31780b_MD5.png)
> 
> Shading tangent : appliquer une map pour l’anisotropy : 
> ![Pièces jointes/12a7126225d3352ecc3e434a6e4fef45_MD5.png](/img/user/Pi%C3%A8ces%20jointes/12a7126225d3352ecc3e434a6e4fef45_MD5.png)

> [!NOTE] Fuzz
> Simule les minis poils, minis texture de vêtement (le velour par exemple) et les minis réflexions de ces poils.
Ajoute un effet velour ou poussiéreux à la matière.
cone angle = roughness
> à utiliser comme un edge color

> [!NOTE] [[3_GARDEN/Notes permanentes/Iridescence\|Iridescence]]
> Permet de faire les effets bulles de savon ou des taches d’huile ou d’essence par exemple

> [!NOTE] Glow
> Pour que l’objet émette de la lumière. On peut parfois le combiner avec la diffuse mais à voir
N'interagit pas avec la lumière, ne simule pas de lumière direct. C’est de l’indirect. Ce qui peut créer des fireflies si les valeurs sont abusé.
Si la source doit être lumineuse et direct. Utiliser alors un mesh light.

#### Transparents

Verre : gain diffuse à 0 et dans la partie glass rflection et refraction gain à 100%.
- On a aussi les matériaux translucents ([[3_GARDEN/Notes permanentes/SSS\|SSS]]) 


## Références 


- Vantablack : matériau le plus absorbant du monde (sinon c le charbon)
## Liens 

