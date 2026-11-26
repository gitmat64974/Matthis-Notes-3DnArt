---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Matte/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:25.599+01:00","mtime":"2026-04-24T17:43:18.849+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/3e et 4e cours compositing esma 3d2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


## La note

On appelle un **Matte** la silhouette en blanc du Channel Alpha générée à partir d’une information RGB d’une Plate.

On produit habituellement ce Matte à partir de trois techniques: produite par Rotoscopie/Keying.
- Technique 01 — La **Rotoscopie**, qui consiste à délimiter à l’aide de Courbes le contour en 2D d’un objet, et d’en remplir le contenu de blanc (peut être d’autres valeurs & gradients);
- Technique 02 — Le **Keying**, qui consiste à extraire d’autres Channels (R, G, B ou autres) des plages de valeurs à convertir en Matte; -> node keyer dans NUKE 
- Technique 03 — Le **Chroma-Keying**, qui consiste à tourner sur set devant des green-screens/autres panels colorés; afin de convertir tous les pixels de cette couleur en information d’Alpha et ainsi générer le Matte;
- Technique 04 — **Cryptomatte/ID** ou **CGAlpha** — Si la Plate provient d’un rendu 3D, le channel d’Alpha ou les AoVs de Cryptomatte ou d’ID peuvent contenir l’information de Matte que nous recherchons: </aside>

![Pasted image 20241109133431.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241109133431.png)


## Références 

## Liens 
