---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Vanilla walk/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.936+01:00","mtime":"2026-04-24T17:43:19.025+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/ANIMATION]]"],"source":["[[3_GARDEN/Notes littéraires/Cours anim marche]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-08-19","aliases":["Animer une marche","cycle de marche"]}}
---


## La note

Marche classique sans personnalité (expression américaine qui vient du fait que la vanille est le parfum de glace classique, quand on sait pas choisir)

On rejoutera ensuite de la personnalité à la marche dans une démarche de caractérisation ou de stylisation.

[[3_GARDEN/Notes permanentes/Timing\|Timing]] : un cycle en une seconde (24fps) donc contact 1 frame 1, contact inverse frame 13 et contact 1 frame 25 etc

![Marche25frs.jpg](/img/user/Pi%C3%A8ces%20jointes/Marche25frs.jpg)

### En pratique :

###### <font color="#00b050">Blocking</font>


> [!abstract] Commencer à DEVELOPPER UN CYCLE de 1 à 25 Frs 
> 
> - COMMENCER PAR LE PIED DE DEVANT
> ajouter la valeur du pied Tz en fr1 + valeur Tz en fr13
> Cela vous donne la valeur de déplacement d un demi cycle.
> 
> -ANNULER LE DEPLACEMENT DU PIED
> copier la valeur fr1 Tz et la coller jusqu en 13.
> 
> REPERCUTER CETTE VALEUR DE DEMI AVANCEE SUR LE ROOT
> garder uniquement les clef Tz fr 1 et 13, tangentes linéaires, cycle avec offset.
> Poser un clefs en 25, Vous connaitrez donc la valeur globale d avancée sur 25frs.
> 
> FINIR L AVANCEE DU PIED
> frs 25, sur la Tz taper la valeur globale d avancée + la valeur que le pied a fr1.
> Cleaner la Tz et travaillez juste manuellement le déroulé.
> 
> FAIRE L AUTRE PIED
> Ce mettre en fr 13 et taper la valeur du pied quand il est devant + l avancée d un demi cycle.
> Curve Tz en cycle offset + clean et déroulé etc …

**On va avoir 4 poses clés qui constituent le blocking : La contact, la down, la passing et la up**

![Pièces jointes/d930a374d7b53d0cf227034b183d53b9_MD5.png](/img/user/Pi%C3%A8ces%20jointes/d930a374d7b53d0cf227034b183d53b9_MD5.png)

![Pièces jointes/4a3473f334b3c9fdaa99d4c238275d5a_MD5.png](/img/user/Pi%C3%A8ces%20jointes/4a3473f334b3c9fdaa99d4c238275d5a_MD5.png)

![Pièces jointes/c93b01455ae6f5888b0d6cff7a75377f_MD5.png](/img/user/Pi%C3%A8ces%20jointes/c93b01455ae6f5888b0d6cff7a75377f_MD5.png)

![Pièces jointes/e0117756e5cb2b5b06316a96e52dd6f9_MD5.png](/img/user/Pi%C3%A8ces%20jointes/e0117756e5cb2b5b06316a96e52dd6f9_MD5.png)


> [!detail] Détail des 4 poses du blocking
> - La contact : Jambe avant tendue (essentiel pour le poids), jambe arrière légèrement pliée. Pieds avance avec un mouvement circulaire, un arc; Pieds plutôt rapprochés. Pour le rig : footroll, ballroll etc à utiliser que lorsque le pieds est au sol pour éviter les confusions dans le graph editor ![Pièces jointes/27a7a8cc4b50a9631c8aa94f6d8cce15_MD5.png](/img/user/Pi%C3%A8ces%20jointes/27a7a8cc4b50a9631c8aa94f6d8cce15_MD5.png)
> - La down : ![Pièces jointes/f8fb28cef361d9e70cc179b9dafd54ac_MD5.png](/img/user/Pi%C3%A8ces%20jointes/f8fb28cef361d9e70cc179b9dafd54ac_MD5.png)
> - La passing : ![Pièces jointes/fffc5d92ab750240520724c383560b88_MD5.png](/img/user/Pi%C3%A8ces%20jointes/fffc5d92ab750240520724c383560b88_MD5.png)
> - La Up : ![Pièces jointes/6589c93e7c03c96001a3df103dd53e14_MD5.png](/img/user/Pi%C3%A8ces%20jointes/6589c93e7c03c96001a3df103dd53e14_MD5.png)
> 
> <span style="background:#40a9ff">Et on boucle avec les pieds inversés : </span>
> <span style="background:#40a9ff">Contact frame 13 </span>
> <span style="background:#40a9ff">Down Frame 16 </span>
> <span style="background:#40a9ff">Passing Position Frame 19 </span>
> <span style="background:#40a9ff">Up Frame 22 </span>
> <span style="background:#40a9ff">Contact identique à la première pose Frame 25</span>

###### <span style="background:#d4b106">Spline (Travail des interpolations)</span>

Etape 1 : Dans le graph editor passer toutes les interpolations des hanches en spline et celles des pieds en linéaire

Étape 2 (poids du pieds) : frame juste après la contact le pieds doit être à plat pour l’impression de poids. Sur cette frame on peut mettre un peu de ballroll pour faire un overlap mais le pied est à plat (footroll à 0)

Etape 3 (travail des hanches) :

Translate y (axe vertical) : On va venir monter légèrement les hanches au niveau des passing et des contact pour avoir une courbe un peu comme la balle qui rebondit (plus arquée vers le haut, moins linéaire). Le but est de rester un tout petit peu plus suspendu sur la up.

Translate z (axe d’avancée) : il faut que ce soit à peu près linéaire (pas forcément complètement). On corrige le placement du centre de gravité à l’oeil pour le réalisme.

Translate x (axe de balancement) : On veut une courbe globalement sinusoïdale un peu arcquée pour avoir de la suspension quand les hanches sont sur le côté (un peu comme le translate y mais pour le balancement).

Rotate x (avant / arrière) : courbe fluide un peu en dent de scie. Faire à l’œil vraiment là pour le coup

![Courbes_Root_Walk.png](/img/user/Pi%C3%A8ces%20jointes/Courbes_Root_Walk.png)

##### Polish

Checker le graph pour l’améliorer, notamment le fait que le pied parte un peu sur le côté lorsqu’il est en l’air pour revenir à se position de départ dès qu’il se pose. Le pied se pose légèrement de biais (rotate de balancement).

Déroulé du pied (très important)

Placer un locator sur le talon pour suivre le déroulé du pied. Contrainte de parenté (menu constrain) avec le maintain offset de coché. Ensuite mettre des frames sur le locator puis mettre le blend parent (dans la channel box) à 1 (casser la connexion pour pas qu’il soit animé → break connexion) et enfin mettre un motion trail sur le locator.

Ensuite bah faut ajuster le footroll etc

![Pièces jointes/5e71102ca5754b11e7131bb3d4d86df0_MD5.png](/img/user/Pi%C3%A8ces%20jointes/5e71102ca5754b11e7131bb3d4d86df0_MD5.png)

pour arriver à ça :

![Pièces jointes/4a6c244da1fefd78dd4c7c8b85340994_MD5.png](/img/user/Pi%C3%A8ces%20jointes/4a6c244da1fefd78dd4c7c8b85340994_MD5.png)

Correction des genoux qui claquent :

Ce qui fait que ça claque c’est que le genoux alterne rapidement entre des positions pliées et tendues.

On peut le corriger soit à la main avec du footroll soit avec le contrôle de stretch disponible sur certains rigs.

### étapes en vidéo

![[marche_etape1.mov]]

![[marche_etape2.mov]]

![[marche_etape3.mov]]

![[marche_etape4.mov]]

![[marche_etape5.mov]]
## Références 

## Liens 


## Flashcards

