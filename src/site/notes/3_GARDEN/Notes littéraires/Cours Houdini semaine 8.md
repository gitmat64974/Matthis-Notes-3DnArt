---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 8/","tags":["note_litteraire","cours","A_traiter"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours","A_traiter"],"creation date":"2025-11-24"}}
---



## Denoise


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

#### Denoise dans houdini :

> [!abstract]+ Rendering et renderpasses
> On fait le calcul de denoise après le rendu 
> Le dénoiser nvidia est cross frame, on va l’utiliser après le rendu
> Pour cela il faut certaines passes de rendu qui le rendront bien plus performant : 
> 
> Dans le node karma render settings 
> - beauty 
> - Albedo 
> - N (smooth normal)
> - Motion vectors 
> - On désactive le Motion blur dans la beauty (il sera quand même calculé) : rendering -> camera effects -> disable image blur
> 
> Ne pas oublier de bien mettre les render settings dans l’usd render rop : 
> Render settings : /Render/rendersettings

---

> [!abstract]+ Denoise après le rendu : 
> COP network : 
> - File : on vient chercher la séquence 
> 	- -> add AOVs from file
> - Denoiseai (denoise machine learning) : choisir optix denoiser. Plug tous les AOVs nécessaires dans les entrèes du node denoise
> 
> On va avoir seulement un problème pour l’entrée prevframe : la frame de départ est la première, il n’y en a pas avant 
> 
> On va donc faire un setup pour avoir l’image 0 puis pour que le denoise recalcule à chaque fois selon la frame rendue précédente : 
> 
> > [!tip]+ Setup de denoise
> > 1. On rend juste l'image à la frame 1. Puis on renomme l'exr rendu en ``.0000.exr`` au lieu de ``.0001.exr``
> > 
> > ![denoise_houdini01.png](/img/user/Pi%C3%A8ces%20jointes/denoise_houdini01.png)
> > 
> > 2. Puis on rend toutes les images : 
> > ![denoise_houdini02.png](/img/user/Pi%C3%A8ces%20jointes/denoise_houdini02.png)
> 
> 

---



</div></div>
 

## Solver 


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

Node en dessous de tous les autres solver

Il ne prend pas en compte l’anim qui lui est donné
Il faut rentrer dedans pour mettre de l’anim

---

La vitesse en 3D : c’est un vecteur avec une direction, contrairement au monde réel où la vitesse n’a pas de direction

---

A noter en VEX (et en C d’ailleurs)

Dir += lampe : même chose que Dir = Dir + lampe
Et c’est pareil pour tout



</div></div>
 

