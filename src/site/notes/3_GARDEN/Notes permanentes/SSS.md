---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/SSS/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.739+01:00","mtime":"2026-04-24T17:43:18.988+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SHADING TEXTURING]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2024-08-19","aliases":null,"Source":["[[3_GARDEN/Notes littéraires/Using PXR surface]]","[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]"]}}
---


## La note

![external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.sessions.edu%2Fwp-content%2Fuploads%2Fmandarin-slice-subsurface-scattering.jpg&f=1&nofb=1&ipt=f3f2c713fcb0e91a6a6da76b4ae6048625aedbc8876c42587c5200621a3b48d3](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.sessions.edu%2Fwp-content%2Fuploads%2Fmandarin-slice-subsurface-scattering.jpg&f=1&nofb=1&ipt=f3f2c713fcb0e91a6a6da76b4ae6048625aedbc8876c42587c5200621a3b48d3)

![external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.ytimg.com%2Fvi%2F38hSdGlUH6w%2Fmaxresdefault.jpg&f=1&nofb=1&ipt=4daac0a8aa2dd834d17a91b6abe6781c7c1b2bfc397d34fadef6704108215cbf](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.ytimg.com%2Fvi%2F38hSdGlUH6w%2Fmaxresdefault.jpg&f=1&nofb=1&ipt=4daac0a8aa2dd834d17a91b6abe6781c7c1b2bfc397d34fadef6704108215cbf)


Le SSS (subsurface scattering) est globalement un effet de lumière. Il se produit lorsque la lumière traverse plusieurs couches ou plusieurs profondeurs dans un objet. 

Tous les diélectriques ont ce phénomène mais il est généralement peu ou pas notable car les couches traversées sont très peu nombreuses ou unique.

Mais par exemple, sur des éléments comme la cire de bougie, le caramel, la peau, ou les feuilles, le SSS est très visible.

#### SSS en CG dans renderman

Reboucher ou cacher suffisamment les trous de la modélisation, car le SSS pourrait créer des artefacts.
Désactiver la [[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]].

> [!abstract]+ Les 2 modes à utiliser : 
> ***Non-Exponential path traced*** : 
> Le mode Non-Exponential path traced est préféré, il est le plus proche de la réalité mais c’est aussi le plus coûteux en rendu. 
> 
***Jensen Dipole*** : 
> Le Jensen Dipole (plus léger) peut être utilisé sur les petites surfaces comme les yeux (Le non exponential a du mal parfois sur l’occlusion avec d’autres objets)

**Mean Free Path Distance** : 
	A quel distance la lumière pénètre dans le volume.
	L'échelle est en millimètre, donc 10 = 1 unité par défaut.
	multiplier avec le mean free path color et l’unit lenght (à 0,1 par défaut).

**Mean Free Path Color**
	Multiplication RGB du Mean Free Path Distance.

Si l’objet à des interpénétrations, cocher Resolve Intersection pour corriger les artefacts (*Par exemple pour bien gérer lorsque le doigt se plie si jamais il y a des intersections (il y en aura car on a rarement le budget pour faire en sorte que le doigt se plaît en parfait contact sans intersections)*)

- **Directionnalité** : Permet en quelque sorte que les photons suivent la courbure de la surface. Cela vient donc occluder le centre : éléments au centre qui ne transmettent pas la lumière (par exemple un os sous un muscle). Cela vient recréer de l’opacité sous la peau
- **Bleed** : permet de préserver les détails à la surface du SSS et que la transmission commence un peu après la surface directe. Si on l’augmente trop ça peut faire trop diffuse
- **Diffuse blend** : on ne l'utilise pas ou que très très peu

Valeurs pour la peau de ces paramètres : 
- **Directionnality** : 0.720
- **Bleed** : 0.783
- **Diffuse Blend** : 0

---

Pour la peau humaine : 
- Cocher résolve self intersection (*éviter les artefacts de lumière sur les surfaces auto-intersectantes*)

Pour les ongles et les sclera (plus petites surfaces) : Utiliser le jensen dipôle sans le résolve intersection

---

## Références 

[Renderman-Subsurface Scattering](https://www.renderman.jp/subsurfaceScattering.html)


- [[3_GARDEN/Notes permanentes/Peindre le SSS\|Peindre le SSS]]

![external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimages-wixmp-ed30a86b8c4ca887773594c2.wixmp.com%2Ff%2F06d4d763-9fb0-4ffb-a5af-3e7d2008c376%2Fdaw0240-573b829d-8688-4ed7-961b-a0f6b53b898c.jpg%2Fv1%2Ffill%2Fw\_966%2Ch\_827%2Cq\_70%2Cstrp%2Fsubsurface\_scattering\_tutorial\_by\_cgcookie\_daw0240-pre.jpg%3Ftoken%3DeyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9ODc3IiwicGF0aCI6IlwvZlwvMDZkNGQ3NjMtOWZiMC00ZmZiLWE1YWYtM2U3ZDIwMDhjMzc2XC9kYXcwMjQwLTU3M2I4MjlkLTg2ODgtNGVkNy05NjFiLWEwZjZiNTNiODk4Yy5qcGciLCJ3aWR0aCI6Ijw9MTAyNCJ9XV0sImF1ZCI6WyJ1cm46c2VydmljZTppbWFnZS5vcGVyYXRpb25zIl19.J\_mrFZZXMsTJcbnB4kFEPOluyfU0wWQZow6ispIfuuw&f=1&nofb=1&ipt=85252a4d83f4b1547238c3c446bbf18f96e8b2f488d9e8d9a9c6e09e1812951d](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimages-wixmp-ed30a86b8c4ca887773594c2.wixmp.com%2Ff%2F06d4d763-9fb0-4ffb-a5af-3e7d2008c376%2Fdaw0240-573b829d-8688-4ed7-961b-a0f6b53b898c.jpg%2Fv1%2Ffill%2Fw_966%2Ch_827%2Cq_70%2Cstrp%2Fsubsurface_scattering_tutorial_by_cgcookie_daw0240-pre.jpg%3Ftoken%3DeyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9ODc3IiwicGF0aCI6IlwvZlwvMDZkNGQ3NjMtOWZiMC00ZmZiLWE1YWYtM2U3ZDIwMDhjMzc2XC9kYXcwMjQwLTU3M2I4MjlkLTg2ODgtNGVkNy05NjFiLWEwZjZiNTNiODk4Yy5qcGciLCJ3aWR0aCI6Ijw9MTAyNCJ9XV0sImF1ZCI6WyJ1cm46c2VydmljZTppbWFnZS5vcGVyYXRpb25zIl19.J_mrFZZXMsTJcbnB4kFEPOluyfU0wWQZow6ispIfuuw&f=1&nofb=1&ipt=85252a4d83f4b1547238c3c446bbf18f96e8b2f488d9e8d9a9c6e09e1812951d)


## Liens 

