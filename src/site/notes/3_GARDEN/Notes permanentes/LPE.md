---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/LPE/","tags":["note_permanente","en_cours"],"ctime":"2026-03-21T20:44:45.954+01:00","mtime":"2026-11-08T20:16:01.233+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["#cours [[Cours de compositing ESMA]] : [loucasrongeart.notion.site/PRMan-Course-ID-0010-LightPathExpressions](https://loucasrongeart.notion.site/RENDERMAN-COURSES-LightPathExpressions-LPEs-c7a445d6b13348649854a5f5a7628718)"],"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2025-05-15","aliases":null}}
---


## La note

> [!DEFINITION]
> 
> - **Un LightPath** : est une information calculée avec des **Rayons** spécifiques ;
>     
> - **LightPathExpressions (LPEs)** : est un langage basé sur des expressions qui spécifie quel **LightPath** se retrouvera dans chacune de vos ArbitraryOutputValues (**AOVs**), également appelées **renderPasses** !
>     


> [!info]+ Historique
> Les LightPathExpressions sont des expressions dérivées de l'OpenShadingLanguage (OSL), qui ont depuis été intégrées dans RenderMan.
> _OSL_ a été développé à l'origine par _SonyPicturesImageworks_ pour leur moteur de rendu interne, principalement utilisé pour les longs métrages d'animation et les _VFX_.

#### Exemple

Illustrons cela avec un rendu CGI et son **Compositing** :
Tous les comportements/lobes des **shaders de surface** ont été divisés en 4 catégories, et ainsi distribués dans 4 **AOVs**/passes personnalisées correspondantes utilisant différentes **LPEs** :

![Capture d'écran 2025-05-15 224240.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-15%20224240.png)

- **Diffuse Reflection** — tous les lobes diffus directs/indirects ;
	- *lpe*: `C<RD>.*[<L.>]`
- **Specular Reflection** — tous les lobes spéculaires directs/indirects ;
    - *lpe*: `C<T[DS]>.*[<L.>]`
- **Transmission** — lobes diffuseTransmit, transmissiveSingleScatter, transmissiveSubSurfaceScattering & transmissiveGlass ;
    - *lpe*: `C<RS>.*[<L.>]`
- **Emission** — tous les lobes émissifs de surface (= Glow) + leurs rebonds indirects sur d'autres surfaces d'objets ;
    - *lpe*: `C.*O`
        - Bien sûr, les rebonds indirects de la surface émissive ont également été ajoutés à l'AOV ‘_diffuse_EmissionLobesSource_’. Cela aidera à ajuster l'intensité de la lumière source et les rebonds indirects en même temps en Compositing. 


![MAYA_CamTrackIntegration_LPE_beauty.webp](/img/user/Pi%C3%A8ces%20jointes/MAYA_CamTrackIntegration_LPE_beauty.webp)

#### Syntaxe précise

![Capture d'écran 2025-05-15 230300.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-15%20230300.png)

| **lpe:**    | Initialization LPE Token;                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| **C**       | CameraEvent LPE Token;                                                                                  |
| `<RD>`      | Intersection of ScatteringEvents of direct Diffuse & Reflections = direct DiffuseReflections LPE Token; |
| **[<L.>O]** | Union of all LightsEvents + all Emissive surfaces LPE Token;                                            |
#### Liste de tous les LPE tokens

###### LPE EVENTS: 

> [!INFO]+ lpe:C 
> 
> Token LPE d'Initialisation pour indiquer l'utilisation du langage LPE dans le ChannelSource ;
> 
> _Exemple_ : `lpe:C.*[<L.>O]` (= BEAUTY) 
> Obtient toutes les réponses de surface de toutes les **Lumières** et de toutes les surfaces émissives ;

> [!INFO]+ <L.'lightGroupName'> 
> 
> Token LPE pour obtenir les réponses des surfaces à partir du lightGroup appelé ‘lightGroupName’ ;
> 
> _Exemple_ : `lpe:C.*[<L.'KEY'>O]`
> Obtient toutes les réponses de surface de toutes les **Lumières** du **lightGroup** ‘_KEY_’ et de toutes les surfaces émissives ;

> [!INFO]+ O - Réponse des Surfaces Émissives
> 
> Token LPE pour obtenir les réponses des surfaces à partir de toutes les surfaces émissives (= PrimaryEvent + All Hits) ;
> 
> _Exemple_ : `lpe:C.*O`
> Obtient toutes les réponses de surface de toutes les surfaces émissives ;

> [!INFO]+ <type event 'LPEGroupName'> 
> 
> Token LPE pour obtenir les réponses des surfaces à partir des GEOs (Géométries) du LPEGroup appelé ‘LPEGroupName’ ;
> 
> _Exemple_ : `lpe:C<RD'greenBall'>.*[<L.>]`

Att Editor -> Transform -> RenderMan -> Shading -> LPE Group 

###### LPE SCATTERING EVENTS/TYPES:

Les **Événements/Types de Diffusion LPE** sont des **Tokens LPE** utilisés pour faire référence à des comportements de surface spécifiques.
En utilisant les **Événements/Types de Diffusion**, vous pouvez isoler les réponses des **lobes de shader**.

| **LPE SCATTERING TYPES** | **LPE SCATTERING EVENTS** |
| ------------------------ | ------------------------- |
| _Reflection ‘R’_         | _Diffuse ‘D’_             |
| _Transmission ‘T’_       | _Specular ‘S’_            |
|                          | _User ‘U’_                |
LPE SCATTERING TYPES: 
- **R** : refers to Reflection surface responses : (To get all Reflective responses : `CR.*[<L.>O]`)
	- **RD** - reflectionDiffuse lobes;
	- **RS** - reflectionSpecular lobes;
- **T** : refers to Transmissive surface responses : (To get all Transmissive responses : `CT.*[<L.>O]`)
	- **TD** - transmissiveDiffuse lobes;
	- **TS** - reflectionSpecular lobes;

LPE SCATTERING EVENTS: 
- **D** : refers to Diffuse surface responses -> `CD.*[<L.>O]`
- **S** : refers to Specular surface responses -> `CS.*[<L.>O]`
- **U** : refers to User defined signal responses -> `CU.*[<L.>O]`

LPE QUALIFIERS: 



> [!abstract] CONTEXTE
> Chaque fois que vous lancez un **Rendu** sur votre machine, pour **chaque pixel** de l'image que vous rendez, des milliers de **Rayons** sont émis depuis votre **Caméra** pour calculer la valeur RGBA de chaque pixel.
> 
> Émis depuis l'origine de la caméra, les **Rayons Émis** (_CastRays_) voyageront dans la direction opposée à celle des photons dans l'espace et le temps, afin de reconstruire leurs trajectoires individuelles approximatives traversant le centre de chaque pixel de l'image rendue et menant vers l'origine de la Caméra.
> 
> Pour chaque pixel, si les **Rayons Caméra** ne touchent aucune surface d'objet dans l'espace 3D, la valeur du pixel résultant sera **nulle** — `RGBA=(0;0;0;0)`.
> 
> Pour chaque pixel, si les **Rayons Caméra** touchent une surface d'objet dans l'espace 3D, ils émettront des **Rayons secondaires** (_Rayons Lumière_ & _Rayons Ombre_) pour calculer la contribution de chaque **Lumière** et des autres objets de la scène afin d'établir la valeur RGB la plus précise possible pour le pixel traversé par le Rayon Caméra.
> 
> En fonction du **shader de surface** et du comportement de la surface, d'autres **Rayons secondaires** (_Rayons Réflexion_ & _Rayons Transmission_) seront émis dans toute la scène pour fournir la contribution de la lumière indirecte aux autres objets de la scène.

***

## Références

- [Using LPE - Renderman 26 - RenderMan](https://renderman.atlassian.net/wiki/spaces/REN26/pages/19661899/Using+LPE)
- [Setting up LPEs in Solaris](https://rmanwiki-27.pixar.com/space/RFH27/544641953/Setting+up+LPEs+in+Solaris)

