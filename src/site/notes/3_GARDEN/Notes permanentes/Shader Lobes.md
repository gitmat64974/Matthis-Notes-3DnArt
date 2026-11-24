---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Shader Lobes/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.673+01:00","mtime":"2026-03-30T20:32:09.711+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]","[[3_GARDEN/MOCs/LIGHTING]]"],"source":["[[3_GARDEN/Notes littéraires/8e, 10e cours compositing]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510070007,"aliases":null}}
---

## La note 

List complète des shader lobes (display beauty dans renderman par exemple)

### **BEAUTY LOBES**

| **AOV Name** | **Type**   | **Description**                                                                              |
| ------------ | ---------- | -------------------------------------------------------------------------------------------- |
| `beauty`     | float3 RGB | Somme des Lobes de _tous les Shaders_, multipliée par la **pass de Shadows** ;               |
| `albedo`     | float3 RGB | Valeur RGB de l’intensité de **DiffuseCOL** (**DiffuseCOL** multiplié par **DiffuseGAIN**) ; |

### **ShaderLobes minimaux qui peuvent être présents dans la scene**

| **SHADER LOBE**     | **CORRESPONDING DIRECT AOV**                   | **CORRESPONDING INDIRECT AOV**                      | **CORRESPONDING FULL LOBE**                  |
| ------------------- | ---------------------------------------------- | --------------------------------------------------- | -------------------------------------------- |
| **Diffuse**         | directDiffuseLobe                              | indirectDiffuseLobe                                 | <span style="background:#ff4d4f">needs a LPE |
| **DiffuseTransmit** | directDiffuseLobe                              | indirectDiffuseLobe                                 | <span style="background:#ff4d4f">needs a LPE |
| **PrimarySpecular** | directSpecularPrimaryLobe / directSpecular     | indirectSpecularPrimaryLobe / indirectSpecular      | <span style="background:#ff4d4f">needs a LPE |
| **Rough**           | directSpecularRoughLobe / directSpecular       | indirectSpecularRoughLobe / indirectSpecular        | <span style="background:#ff4d4f">needs a LPE |
| **ClearCoat**       | directSpecularClearcoatLobe / directSpecular   | indirectSpecularClearcoatLobe / indirectSpecular    | <span style="background:#ff4d4f">needs a LPE |
| **[[3_GARDEN/Notes permanentes/Iridescence\|Iridescence]]**     | directSpecularIridescenceLobe / directSpecular | indirectSpecularIridescenceLobe / indirectSpecular  | <span style="background:#ff4d4f">needs a LPE |
| **Fuzz**            | directSpecularFuzzLobe / directSpecular        | indirectSpecularFuzzLobe / indirectSpecular         | <span style="background:#ff4d4f">needs a LPE |
| **Subsurface**      | <span style="background:#ff4d4f">needs a LPE   | <span style="background:#ff4d4f">needs a LPE        | subsurface / subsurfaceLobe                  |
| **SingleScatter**   | <span style="background:#ff4d4f">needs a LPE   | <span style="background:#ff4d4f">needs a LPE        | transmissiveSingleScatterLobe                |
| **Glass**           | <span style="background:#ff4d4f">needs a LPE   | <span style="background:#ff4d4f">needs a LPE</span> | transmissiveGlassLobe                        |
| **GlassReflection** | <span style="background:#ff4d4f">needs a LPE   | <span style="background:#ff4d4f">needs a LPE        | <span style="background:#ff4d4f">needs a LPE |
| **GlassRefraction** | <span style="background:#ff4d4f">needs a LPE   | <span style="background:#ff4d4f">needs a LPE        | <span style="background:#ff4d4f">needs a LPE |
| **Glow**            | //NULL//                                       | //NULL//                                            | emissive                                     |

==Par exemple Dans une scène avec uniquement des shaders utilisant **Diffuse**, **Specular** et **Glass**, nous n'aurons besoin que de ces **AOVs**.==

On peut tester en faisant un rebuild rapide et comparer le resultat du rebuild avec un preview render (IT render par exemple), si les deux images sont identiques, on est bons !
### **DIFFUSE LOBES**

| **AOV Name**          | **Lobe Type**      | **Type**   | **Description**                                                                              |
| --------------------- | ------------------ | ---------- | -------------------------------------------------------------------------------------------- |
| `directDiffuse`       | **Direct Lobes**   | float3 RGB | Multiplication de l’Input de **DiffuseCOL** et l’Input de **DiffuseGAIN** ;                  |
| `directDiffuse`       | **Direct Lobes**   | float3 RGB | Valeur RGB de l’intensité de **DiffuseCOL** (**DiffuseCOL** multiplié par **DiffuseGAIN**) ; |
| `directDiffuseLobe`   | **Direct Lobes**   | float3 RGB | Lobe de **Diffuse Directe** ;                                                                |
| `indirectDiffuse`     | **Indirect Lobes** | float3 RGB | Multiplication de l’Input de **DiffuseCOL** et l’Input de **DiffuseGAIN** ;                  |
| `indirectDiffuse`     | **Indirect Lobes** | float3 RGB | Valeur RGB de l’intensité de **DiffuseCOL** (**DiffuseCOL** multiplié par **DiffuseGAIN**) ; |
| `indirectDiffuseLobe` | **Indirect Lobes** | float3 RGB | Lobe de **Diffuse Directe** ;                                                                |

### **TRANSMISSIVE LOBES (SSS + SingleScatter + TransmissiveDiffuse + GlassRefraction)**

| **AOV Name**                    | **Type**   | **Description**                                                                                                    |
| ------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------ |
| `subsurface`                    | float3 RGB | Somme des Lobes de _SubSurface_ + _SingleScatter_ + _TransmissiveDiffuse_, multipliée par la **pass de Shadows** ; |
| `transmissiveSingleScatterLobe` | float3 RGB | Lobe de _SingleScatter_, multiplié par la **pass de Shadows** ;                                                    |
| `transmissiveGlassLobe`         | float3 RGB | Lobe de _transmissibleGlassLobe_ (_GlassRefraction_), multiplié par la **pass de Shadows** ;                       |

### **SPECULAR LOBES (Primary + Rough + Clearcoat + Iridescence + Fuzz + GlassReflection)**

| **AOV Name**                      | **Lobe Type**      | **Type**   | **Description**                                                                                                                                               |
| --------------------------------- | ------------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `directSpecular`                  | **Direct Lobes**   | float3 RGB | Somme des Lobes de _Spéculaires directes_ (**Primary**+**Rough**+**ClearCoat**+**Iridescence**+**Fuzz**+**Glass**), multipliée par la **pass de Shadows** ;   |
| `directSpecularUnoccluded`        | **Direct Lobes**   | float3 RGB | Somme des Lobes de _Spéculaires directes_ (**Primary**+**Rough**+**ClearCoat**+**Iridescence**+**Fuzz**+**Glass**), _sans la pass de Shadows_ ;               |
| `directSpecularPrimaryLobe`       | **Direct Lobes**   | float3 RGB | Lobe _Primary_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                                |
| `directSpecularRoughLobe`         | **Direct Lobes**   | float3 RGB | Lobe _Rough_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                                  |
| `directSpecularClearcoatLobe`     | **Direct Lobes**   | float3 RGB | Lobe _Clearcoat_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                              |
| `directSpecularIridescenceLobe`   | **Direct Lobes**   | float3 RGB | Lobe _Iridescence_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                            |
| `directSpecularFuzzLobe`          | **Direct Lobes**   | float3 RGB | Lobe _Fuzz_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                                   |
| `directSpecularGlassLobe`         | **Direct Lobes**   | float3 RGB | Lobe _Glass_ de Spéculaires directe, multipliée par la **pass de Shadows** ;                                                                                  |
| `indirectSpecular`                | **Indirect Lobes** | float3 RGB | Somme des Lobes de _Spéculaires indirectes_ (**Primary**+**Rough**+**ClearCoat**+**Iridescence**+**Fuzz**+**Glass**), multipliée par la **pass de Shadows** ; |
| `indirectSpecularUnoccluded`      | **Indirect Lobes** | float3 RGB | Somme des Lobes de _Spéculaires indirectes_ (**Primary**+**Rough**+**ClearCoat**+**Iridescence**+**Fuzz**+**Glass**), _sans la pass de Shadows_ ;             |
| `indirectSpecularPrimaryLobe`     | **Indirect Lobes** | float3 RGB | Lobe _Primary_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                              |
| `indirectSpecularRoughLobe`       | **Indirect Lobes** | float3 RGB | Lobe _Rough_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                                |
| `indirectSpecularClearcoatLobe`   | **Indirect Lobes** | float3 RGB | Lobe _Clearcoat_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                            |
| `indirectSpecularIridescenceLobe` | **Indirect Lobes** | float3 RGB | Lobe _Iridescence_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                          |
| `indirectSpecularFuzzLobe`        | **Indirect Lobes** | float3 RGB | Lobe _Fuzz_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                                 |
| `indirectSpecularGlassLobe`       | **Indirect Lobes** | float3 RGB | Lobe _Glass_ de Spéculaires indirecte, multipliée par la **pass de Shadows** ;                                                                                |

### **EMISSIVE LOBES**

| **AOV Name** | **Type**   | **Description**     |
| ------------ | ---------- | ------------------- |
| `emissive`   | float3 RGB | Lobe d’_Emissive_ ; |


## Références


> [!example]- Flashcards
> ...




## Liens 
