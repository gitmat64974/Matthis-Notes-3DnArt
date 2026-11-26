---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/AOVs Utilitaires/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:32.096+01:00","mtime":"2026-03-30T20:32:03.908+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":["[[3_GARDEN/Notes littéraires/8e, 10e cours compositing]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510070007,"aliases":null}}
---

## La note 

#### AOV Utilitaires à ajouter de manière générale

| AOV Name           | Category     | Description                                                                |
| ------------------ | ------------ | -------------------------------------------------------------------------- |
| **albedo**         | *Lighting*   | Diffuse/Transmit color rgb surface intensity;                              |
| **beauty**         | *Lighting*   | Rendered BXDF lobes;                                                       |
| **a**              | *Standard*   | Alpha/Opacity value;                                                       |
| **id**             | *Standard*   | Per-object identifier value;                                               |
| **dPdcameradtime** | *Standard*   | Derivative in XYZ-space of P in time (velocity vector) relative to camera; |
| **dPdtime**        | *Standard*   | Derivative in XYZ-space of P in time (velocity vector);                    |
| **motionFore**     | *Standard*   | Forward motion vector                                                      |
| **motionBack**     | *Standard*   | Backward motion vector                                                     |
| **Po**             | *Standard*   | Per-Pixel object world position                                            |
| **NoN**            | *Standard*   | Non-Displaced XYZ-space surface relief face orientation;                   |
| **z**              | *Standard*   | Non-Aliased depth from camera in world-space                               |
| **Pworld**         | *Integrator* | Displaced XYZ-space surface relief coordinates;                            |
| **Nworld**         | *Integrator* | Displaced XYZ-space surface relief face orientation;                       |
| **depth**          | *Integrator* | R:filtered depth, G:filtered height, B:geometric-facingRatio               |
| **st**             | *Integrator* | UV (U & V) coordinates of surface                                          |
| **cputime**        | *Integrator* | CPU runtime taken per pixel/bucket;                                        |
| **sampleCount**    | *Integrator* | Amount of Samples taken during runtime per pixel/bucket;                   |

#### Primitive Data AOVs

> [!info]+ ID For Keying/Matte
> 
> * **id** - *Standard*
>     Nombre assigné à chaque GEO, à l’aide d’un attribut d’identification;
> 
> * **Cryptomatte** - *Standard*
> 	* id = float-1 id — Nombre assigné à chaque GEO, à l’aide d’un attribut d’identification;

> [!info]+ Normals
> 
> * **__Nworld** - *Integrator*
>     Normalized Shading normal (post-displacement);
>     Elle contient, pour chaque pixel:
>     * `__Nworld.r` : World-relative Camera.X axis-viewed ShadedFace Normals (w/Displacement)
>     * `__Nworld.g` : World-relative Camera.Y axis-viewed ShadedFace Normals (w/Displacement)
>     * `__Nworld.b` : World-relative Camera.Z axis-viewed ShadedFace Normals (w/Displacement)
> 
> * **Nn** - *Standard*
>     Normalized Shading normal (post-displacement);
>     Elle contient, pour chaque pixel:
>     * `__Nn.r` : Object-Relative Camera.X axis-viewed ShadedFace Normals (w/Displacement)
>     * `__Nn.g` : Object-Relative Camera.Y axis-viewed ShadedFace Normals (w/Displacement)
>     * `__Nn.b` : Object-Relative Camera.Z axis-viewed ShadedFace Normals (w/Displacement)
> 
> * **Non** - *Standard*
>     Normalized Shading normal (pre-displacement)
>     Elle contient, pour chaque pixel:
>     * `__Nworld.r` : Object-Relative Camera.X axis-viewed ShadedFace Normals (w/o Displacement)
>     * `__Nworld.g` : Object-Relative Camera.Y axis-viewed ShadedFace Normals (w/o Displacement)
>     * `__Nworld.b` : Object-Relative Camera.Z axis-viewed ShadedFace Normals (w/o Displacement)
> 

> [!info]+ 3D Position / Coordinates
> * **__Pworld** - *Integrator*
>     Position in world-space
>     Elle contient, pour chaque pixel:
>     * `__Pworld.r` : x component
>     * `__Pworld.g` : y component
>     * `__Pworld.b` : z component
> 
> * **P** - *Standard*
>     Shading Position in world-space (post-displacement)
>     Elle contient, pour chaque pixel:
>     * `P.r` : Object-Relative ShadedFace World.X Coordinates (w/Displacement)
>     * `P.g` : Object-Relative ShadedFace World.Y Coordinates (w/Displacement)
>     * `P.b` : Object-Relative ShadedFace World.Z Coordinates (w/Displacement)
> 
> * **Po** - *Standard*
>     Shading Position in world-space (pre-displacement)
>     Elle contient, pour chaque pixel:
>     * `Po.r` : Object-Relative ShadedFace World.X Coordinates (w/o Displacement)
>     * `Po.g` : Object-Relative ShadedFace World.Y Coordinates (w/o Displacement)
>     * `Po.b` : Object-Relative ShadedFace World.Z Coordinates (w/o Displacement)
> 
> * **__st** - *Integrator*
>     Surface texture/UV coordinates (in UV normalized space)
>     Elle contient, pour chaque pixel:
>     * `__st.r` : u component (Object-Relative ShadedFace Texture/UV Coordinates w/Displacement)
>     * `__st.g` : v component (Object-Relative ShadedFace Texture/UV Coordinates w/Displacement)
>     * `__st.b` : (Likely unused or specific data)
>     *Note: The original text's description components (`P.r`, `P.g`, `P.b`) seemed incorrect for UV coordinates; corrected to `__st.r`, `__st.g`, `__st.b` with typical UV interpretation.*
> 

#### Lighting / Depth Of Field AOVs

> [!info]+ Depth of Field
> 
> * **z** - *Standard*
>     z = float-1 depth from camera in world-space
> 
> * **__depth** - *Integrator*
>     Multi-purpose AOV
>     Elle contient, pour chaque pixel:
>     * `__depth.r` : depth from camera in world-space
>     * `__depth.g` : height in world-space
>     * `__depth.b` : geometric facing ratio : abs(Nn.V)

#### Motion-Blur AOVs

> [!info]+ 2D Motion-Blur
> * **motionFore** - *Standard*
> 	* motionFore = Forward 2D-rasterSpace motion (float-3 vector)
> * **motionBack** - *Standard*
> 	* motionBack = Backward 2D-rasterSpace motion (float-3 vector)

> [!info]+ Vector Motion-Blur
> * **dPdtime** - *Standard*
>     Instantaneous velocity in 3D-Space (float-3 vector) (without Camera Movement)
> 
> * **dPcameradtime** - *Standard*
>     Instantaneous velocity in 3D-Space (float-3 vector) (with Camera Movement)

#### General / Debug AOVs

> [!info]+ Shadow-Casting
> 
> * **occluded** - *Shadow*
> 	* occluded = Beauty + Collected shadows, only for self-occluded areas of the 3Dspace;
> * **shadow** - *Shadow*
> 	* shadow = collected shadows cast by objects onto primitives of the current collection;
> 

> [!info]+ Debug
> * **cpuTime** - *Diagnostic*
>     Time taken to render a pixel — *Higher values means that these regions are the most expensive in time to render. Optimize your scene if render times are too high*;
> 
> * **sampleCount** - *Diagnostic*
>     Number of samples taken for the resulting pixel (*color-pick/pixel-Analyze the pixel values to see the sampleCount, or reduce the exposure to see the most expensive zones*);
> 

#### AOVs TO ALWAYS HAVE

| UTIL AOV NAME | AOV CATEGORY | DESCRIPTION                                               | PURPOSE                        | NODES TO USE THEM WITH                     |
| :------------ | :----------- | :-------------------------------------------------------- | :----------------------------- | :----------------------------------------- |
| **__Nworld** | *Integrator* | Normalized Shading normal (post-displacement);            | Relighting                     | `[normalsRotate NKPD]`, `[C44Kernel]`, `[Matrix3]` |
| **__Pworld** | *Integrator* | Position in world-space;                                  | Relighting, Atmos              | `[aPMatte]`                                |
| **__Depth** | *Integrator* | R:filtered depth, G:filtered height, B:geometric-facingRatio | Atmos                          | `[blacksMatch]`                            |
| **__st** | *Integrator* | Surface texture/UV coordinates (in UV normalized space)   | ReTexturing, Tracking          | `[STmap]`                                  |
| **z** | *Standard* | Z:unfiltered depth from camera in world-space             | Defocus                        | `[ZDefocus]`, `[OpticalZDefocus]`, `[Bokeh]`     |


## Références


> [!example]- Flashcards
> ...




## Liens 
