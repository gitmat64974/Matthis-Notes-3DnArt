---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Skinning Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[3_GARDEN/MOCs/RIG|RIG]]"],"source":["Houdini doc"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-17","aliases":null}}
---

## La note 

---

#### Skin / Capture

[Skin capture - Houdini documentation](https://www.sidefx.com/docs/houdini/character/kinefx/capture.html)

Lors du skinning (appelé plutôt capture dans Houdini), Houdini vient créer des tétrahèdres temporaires qui remplissent tout l'intérieur de la modé, ce qui permet de skinner par correspondance intérieur et pas selon la surface. Par exemple un point sur la jambe droite n'aura aucun risque d'être influencé par un joint de la jambe gauche car le chemin intérieur entre jambe gauche et droite est très long alors que les points sont très proches en surface

Le skinning se fait principalement via le node <font color="#9bbb59">jointcapturebiharmonics</font> (skinning automatique) et le <font color="#9bbb59">jointcapturepaint</font> (correction ou création manuelle du skinning)

Setup de base avec le <font color="#9bbb59">jointcapturebiharmonics</font> : 

![Pasted image 20260111005355.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260111005355.png)

ou encore plus simple : 

![](https://www.sidefx.com/docs/houdini/images/char/kinefx_capture_tuberigpose.png)


*Le rig pose et le bone deform sont là pour tester les déformations du skin. Pour animer, il est largement préférable d'utiliser le framework APEX*

---
#### Example : Skinner une géo qui a des parties dures et d'autres molles

Première étape est de séparer les parties dures des parties molles
Puis on skin les parties dures avec le `capturepackedgeo` et les parties molles avec le `jointcapturebiharmonic` : 

![Capture d'écran 2026-09-25 214006.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-25%20214006.png)


> [!NOTE]+ Fonctionnement du `capturepackedgeo`
> Ce qu'il faut faire : 
> 1. S'assurer que le joint a le meme name que la geo qu'on veut skin
> 2. Cocher pack input pour que la geo soit packée et donc skinnée entièrement à 1
> 3. Cocher unpack output pour que la geo puisse etre déformée
> 4. Cocher capture by attribute pour faire correspondre automatiquement le joint à la geo qui a le meme name

---
#### Les principaux nodes de skinning

|Create Capture Weights|Description|
|---|---|
|[Joint Capture Biharmonic SOP](https://www.sidefx.com/docs/houdini/nodes/sop/kinefx--jointcapturebiharmonic.html "Captures skin geometry to a SOP skeleton for use with Joint Deform.")|Creates smoothed-out capture weights based on joint position and volume. Works well for softer, non-mechanical, organic deformation.|
|[Joint Capture Proximity SOP](https://www.sidefx.com/docs/houdini/nodes/sop/kinefx--jointcaptureproximity.html "Supports Joint Deform by assigning capture weights to points based on distance to joints.")|Creates capture weights based on the geometry’s distance to the skeleton joints. This is a quicker and less computationally-intensive operation than the Joint Capture Biharmonic SOP, but results in weights that are not as evenly distributed or smoothed out, especially for organic surfaces. The Joint Capture Proximity SOP works well for rigging simple geometry like a tube.|
|[Capture Packed Geometry SOP](https://www.sidefx.com/docs/houdini/nodes/sop/kinefx--capturepackedgeo.html "Rigidly captures packed geometry to a SOP skeleton.")|This is a rigid weighting method where geometry pieces are assigned to a given joint with 100% weighting.|
|[Joint Capture Paint SOP](https://www.sidefx.com/docs/houdini/nodes/sop/kinefx--jointcapturepaint.html "Lets you paint capture weights directly onto geometry.")|Allows you to interactively paint capture weights on geometry.|

|Modify Capture Weights|Description|
|---|---|
|[Attach Joint Geometry SOP](https://www.sidefx.com/docs/houdini/nodes/sop/kinefx--attachjointgeo.html "Creates control geometry for SOP-based KineFX rigs.")|Attaches geometry to joints, with the geometry influencing the capture result.|
|Joint Capture Paint SOP|Allows you to interactively paint capture weights on geometry that have existing weights.|




---


## Références

[[3_GARDEN/MOCs/RIG|RIG]]
- [[3_GARDEN/MOCs/RIG HOUDINI|RIG HOUDINI]]

[Houdini KineFX 101: Attach Object To Rig // Capture Packed Geometry - YouTube](https://youtu.be/0XPCNxefOz8?si=urDWg-WFeEqxAp4b)

> [!example]- Flashcards
> ...




## Liens 




