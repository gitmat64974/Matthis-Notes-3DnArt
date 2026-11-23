---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/PBR/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:34.744+01:00","mtime":"2025-12-23T00:02:55.665+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/3D]]"],"source":["Perplexity"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-12-22","aliases":["différence entre raytracing et path tracing","PBR et path tracing"]}}
---

## La note 

Le PBR (Physically Based Rendering) et le path tracing sont deux techniques essentielles en infographie 3D pour obtenir des rendus réalistes. Le PBR définit des matériaux physiquement plausibles, tandis que le path tracing simule l'éclairage global de manière non biaisée​

#### PBR expliqué

Le Physically Based Rendering modélise l'interaction de la lumière avec les surfaces en s'appuyant sur des principes physiques réels, comme la réflexion, la diffusion et la conservation d'énergie. Il utilise des cartes de textures spécifiques (albédo pour la couleur de base, rugosité, métallité, normale pour les détails) pour que les matériaux réagissent de façon cohérente sous n'importe quel éclairage, évitant les artefacts des anciens shaders. Cela simplifie les workflows en 3D, rendant les assets réutilisables et photoréalistes, idéal pour l'animation surréaliste ou CGI.​

#### Path tracing expliqué

Le path tracing est une méthode de ray tracing avancée qui trace des rayons lumineux de manière aléatoire depuis la caméra, en simulant leurs rebonds multiples jusqu'à convergence vers l'équation de rendu physique. Contrairement au ray tracing classique limité aux réflexions directes, il capture l'illumination globale (ombres douces, caustiques, GI) sans biais, mais génère du bruit qui s'estompe avec plus d'échantillons. C'est computationnellement intensif, souvent accéléré par GPU dans des moteurs comme ceux de NVIDIA RTX


## Références


> [!example]- Flashcards
> ...




## Liens 




