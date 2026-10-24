---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/RIG/","tags":["MOC"],"dg-note-properties":{"aliases":["RIGGING"],"MOC":["[[3_GARDEN/MOCs/RIG|RIG]]","[[3D]]"],"tags":["MOC"],"Source":["[[Notes de cours de rigging d'élèves au dessus, traité par ChatGPT]]"],"creation date":"2024-09-30"}}
---

![](https://cdn.fastpixel.io/fp/ret_img+v_948d+q_lossy+to_webp/aaagameartstudio.com%2Fwp-content%2Fuploads%2F2023%2F08%2Frigging-in-3d-animation-character-rigging.jpg)

Le rigging consiste à créer un système de squelettes et de contrôleurs pour permettre à un modèle 3D de bouger, facilitant ainsi l’animation. En plus de personnages, les riggers travaillent aussi sur des objets ("props") dans une scène, comme des véhicules ou des machines. 

*Le rigging est aussi utilisé dans le **cinéma traditionnel** et le **théâtre**, par exemple pour contrôler les caméras ou déplacer des accessoires à l’aide de grues ou de poulies.* 

**L’idée est de rendre le travail moins pénible pour l’animation. « Friendly rigging », on facilite, on rend lisible et ergonomique (UX), visible etc.
L’idée du rigging est tout ce qui concerne l’amélioration de l’expérience utilisateur, l’UX en gros**

---

> [!example]- Ressources
> 
> > [!tip] Pdfs rig des années sup de l'esma : 
> > - [LE RIGG - Google Docs](https://docs.google.com/document/d/1SItmrfHC1FZ2t-EKq0HmywPhXOAYwtUcqWMMW9s-_X8/edit?mode=html&tab=t.0)
> > - [Rig Avancé - Google Docs](https://docs.google.com/document/d/1JhcEPy36RanooHfCXQben4Y8AhxZ3E2JVgGCfe7D-Co/edit?tab=t.0#heading=h.v5xph27gqkwn) 
> > - [Masterclass CFX - Google Docs](https://docs.google.com/document/d/11NNQJp5_Hugflg2ch-fO4xA-UbCM5L3WOAhRkL9Q3Eg/edit?tab=t.0#heading=h.q44q2astpgp2)
> 
> Simulation muscles : 
> - [Cours complet Houdini muscle simulation](https://www.sidefx.com/muscles-masterclass-essentials/)
> - [Maya to Houdini Transition Guide | Robert Magee | Houdini Hive Worldwide - YouTube](https://youtu.be/z0S3bGeQMIE?si=RYWvHJUsqft7yU-2)
> - [advanced rigging techniques](https://www.cgguru.com/advanced-rigging-techniques)
> 
> Rig facial : 
> - [Face rigging course](https://youtube.com/playlist?list=PLgala72Uap1rRXj4Uv8_lxXmGAfpHmrxe&si=9frCZXIGe5_pLcC-)
> - [Maya Facial Rigging for Beginners](https://youtube.com/playlist?list=PLbvsJz5ZcmxGpUYWF-JqqXyRdAMpFtVf9&si=3yBZjlZo0S31ErVh)
> 
> Rig bidep : 
> - [Rigging in maya, biped course](https://youtube.com/playlist?list=PLgala72Uap1rYD3m7Z6BpzNpdIQzgVtsM&si=9L0CGONWUG2sekwL)
> - Exemple du même gars : [Rigging real time alien](https://youtube.com/playlist?list=PLgala72Uap1rtI7sy75fDHqV7VKQBMknt&si=1ugKKMl7qAzlRI8s)
> 
> Rig quadruped : 
> - [Rigging in maya, quadruped course](https://youtube.com/playlist?list=PLgala72Uap1oClPtT7oCtrdwxA5xsHsFV&si=_dXpWvLNRZ54ThCX)
> 
> #### Plugin/Scripts Auto rig
> 
> [mgear-framework.com – mGear Framework](https://www.mgear-framework.com/) : MGEAR, auto rig gratuit pour maya et unreal engine
> 	doc : [Overview — mGear: Rigging Framework 4.0.3 documentation](https://mgear4.readthedocs.io/en/latest/overview.html)
> 
> [Maya: Hive Autorigger – Create 3d Characters](https://create3dcharacters.com/maya-hive-autorigger/) : HIVE Autorigger par Zoo Tools, payant mais pas encore trop cher
> 
> [PERSEUS AUTO RIG](https://perseusrigging.com/) : Plugins payants mais incroyables de rig auto biped, quadruped et facial
> 
> [Frigger v5 - Auto facial rigger for Maya](https://cgkode.gumroad.com/l/frigger) : Script d'auto rig facial (peut être plus pour du cartoon ?)

# MOC

Le rigging se superpose aux autres étapes du [[3_GARDEN/Notes permanentes/Pipeline de production en animation|Pipeline de production en animation]] : 
- **Modélisation** : Création de la géométrie du personnage ou de l’objet. [[3_GARDEN/MOCs/MODELISATION|MODELISATION]]
- **Rigging** : Application des contrôleurs et des squelettes sur les modèles.
- **Animation** : Utilisation du rig pour donner vie au modèle. [[3_GARDEN/MOCs/ANIMATION|ANIMATION]]


On a 3 types d'informations dans un rig notamment dans kinefx : 
- Geo skinnée 
- Joint (capture pose)
- Joint animés

Et les controleurs qui viennent gérer la déformation des joints


---

## Principes de rig généraux 

Voir [[3_GARDEN/MOCs/RIG|RIG]] (plus axé Rig Maya bien sur)

[[3_GARDEN/Notes permanentes/Joint (rig)|Joint (rig)]]
- [[3_GARDEN/Notes permanentes/Joints rig bidep|Joints rig bidep]]

[[3_GARDEN/Notes permanentes/Orient Joints|Orient Joints]]

---
## Rig dans Maya 

*Il n'y a pas encore grand chose pour ce qui est du rig Maya*

Cours 3D2 : 

[[3_GARDEN/Notes littéraires/Cours skinning rig biped 3D2|Cours skinning rig biped 3D2]]
[[3_GARDEN/Notes littéraires/Cours controleurs rig biped 3D2|Cours controleurs rig biped 3D2]]

Notes en Vrac : 

[[3_GARDEN/Notes permanentes/Wrinkle Map|Wrinkle Map]] 

[[3_GARDEN/Notes permanentes/Matrice (Rig)|Matrice (Rig)]] 

---

## Rig dans Houdini

[[3_GARDEN/MOCs/RIG HOUDINI|RIG HOUDINI]]

