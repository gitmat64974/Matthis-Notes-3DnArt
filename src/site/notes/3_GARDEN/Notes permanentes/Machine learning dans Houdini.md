---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Machine learning dans Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[IA]]"],"source":["Houdini Hive"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-10-09","aliases":null}}
---

## La note 

Le Machine Learning est une façon d'enseigner à un ordinateur à apprendre à partir de données plutôt que de programmer explicitement l'exécution d'une tâche spécifique.

Quelques définitions : 
- **Inference** : L'inférence est le processus consistant à utiliser un modèle entraîné pour générer des prédictions sur de nouvelles données que l'ordinateur n'a jamais vues auparavant
- **ONNX** : ONNX signifie Open Neural Network Exchange et est un format ouvert conçu pour représenter les modèles d'apprentissage automatique
- **Supervised learning** : L'apprentissage supervisé est une approche d'apprentissage automatique où un modèle est entraîné à l'aide d'exemples étiquetés qui incluent des données d'entrée et les données de sortie correctes.
- **PCA** : Le *Principle component analysis* est une technique qui transforme un grand ensemble de variables en un ensemble plus restreint de motifs clés, capturant la majeure partie des informations importantes contenues dans les données. Cela permet de simplifier le jeu de données tout en conservant sa structure essentielle.

Les nodes de machine learning dans Houdini 21 : 

|**EXAMPLE PROCESSING**|**DATA SET I/O**|**TRAINING**|**INFERENCE**|
|---|---|---|---|
|Principal Component Analysis|Geometry Raw Output|Python Virtual Environment|ONNX Inference|
|ML Example|ML Example Output|Python Script|ONNX Inference (COP)|
|ML Example Decompose|ML Example Import|ML Regression Train|ML Regression Inference|
|ML Extract Example|ROP ML Example Raw Output|ML Regression Kernel|ML Regression Proximity|
|ML Example Partition||ML Train Style Transfer|ML Regression Linear|
|ML Attribute Generate||ML Preprocess OIDN|ML Regression Kernel|
|ML Pose Generate||ML Train OIDN|ML Deform|
|ML Pose Serialize||ML Train Deformer (Recipe)|APEX Add ML Deformer|
|ML Pose Deserialize||ML Train Volume Upres (Recipe)|ML Volume Tile Inference|
||||ML Volume Upres|

---

### Les étapes : 

![Capture d'écran 2026-10-10 123656.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-10%20123656.png)


#### 1- Data collection

Collecter les meilleurs données possibles

#### 2- Model training

Entrainer un modèle avec ces données

Dans Houdini : TOPs

Node : ML Train regression
- Ce node prend un dataset en entrée en output un ONNX file

#### 3- Model inference

Un fois que le modèle est entrainé, le but est de faire en sorte que le modèle fasse des prédictions sur des nouvelles données

ça se fera grâce au node onnix inference (en SOP ou en COP)



## Références


> [!example]- Flashcards
> ...




## Liens 




