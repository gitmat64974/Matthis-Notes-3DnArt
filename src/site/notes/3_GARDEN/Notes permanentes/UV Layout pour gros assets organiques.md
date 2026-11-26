---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/UV Layout pour gros assets organiques/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:45.932+01:00","mtime":"2025-11-14T14:00:51.402+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/UV]]","[[3_GARDEN/MOCs/3D]]"],"source":["[[3_GARDEN/Notes littéraires/Cours de lighting rendu ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-14","aliases":null}}
---

## La note 

En utilisant la boucle médiane EdgeLoop (celle qui divise le modèle en deux dans l'axe médian), vous pouvez avoir des UV identiques à GAUCHE et à DROITE.

Dans la disposition UV ci-dessous, vous verrez que les **LEFT UVIslands** sont en **Front** (==**bleu**), tandis que les **îlots UV DROITE** sont en **Back**  (==**rouge**).
Cela facilite le processus de texturing dans Mari, où vous pouvez copier/coller des données entre les UVIslands.
Ce n'est pas le cas dans SubstancePainter (qui est vraiment nul...) 😭


![Pasted image 20251114135715.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251114135715.png)

- L'UVLayout distribue également les UVTiles en fonction des régions de l'asset. 
Il y a une logique (de bas en haut) dans celui-ci, qui distribue les UVTiles de la tête à la queue.
Les UVTiles sont également répartis par partie du corps (tête, torse, pattes avant, ventre, bassin, pattes arrière, queue et extrémité de la queue).

## Références


> [!example]- Flashcards
> ...




## Liens 




