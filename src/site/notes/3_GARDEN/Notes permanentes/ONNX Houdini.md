---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/ONNX Houdini/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:27.590+01:00","mtime":"2026-02-06T22:24:27.536+01:00","dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-02-06","aliases":null}}
---

## La note 

[Free Houdini Tutorial: Machine Learning with ONNX in Houdini 20 - YouTube](https://youtu.be/aCAatiY53s8?si=XFZPnuNzO8kD-oIc)


![](https://i.imgur.com/amxs2qi.png)

Gestion des fichiers / environnements : 

![](https://i.imgur.com/hOFVtl7.png)


Ressources github de fichiers onnx pré entrainés : [GitHub - onnx/models: A collection of pre-trained, state-of-the-art models in the ONNX format](https://github.com/onnx/models)

#### Fonctionnement du node onnx

On load un model 

ensuite les valeurs des tableaux sont remplies automatiquement : elles se lisent de gauche à droite et de haut en bas. 
La première est généralement 1, c'est le nombre d'image que le model va traiter à la fois, la deuxième est le nombre de canaux de l'image (1 pour noir et blanc, 3 pour rgb), ensuite c'est la résolution de l'image


#### Transfer de style

Dans l'exemple ci dessous, on prend un model dans cette collection : [models/validated/vision/style\_transfer/fast\_neural\_style at main · onnx/models · GitHub](https://github.com/onnx/models/tree/main/validated/vision/style_transfer/fast_neural_style)

![Pasted image 20260206221924.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260206221924.png)

Le processus est très simple : on prend une grid, on lui assigne une texture qui peut etre animée (node attribute from map), puis on utilise le model pour modifier le style de l'image

Mais il y a un problème que les wrangle viennent régler : l'onnx attend un type d'input de donnée rrrr...gggg...bbbb alors qu'il reçoit rgbrgbrgbrgb... Il ne comprend donc pas. 
Les wrangle viennent séparer les couches : 
Pour chaque couche : 

```C
f@in = v@Cd.r;
```

On normalize l'attribut out en sortie du onnx
Puis on vient réappliquer tout ça sur la grid dans un dernier wrangle : 

```C
int np = npoints(0);

float r = point(1, "out", @ptnum);
float g = point(1, "out", @ptnum + np);
float b = point(1, "out", @ptnum + np + np);

v@Cd = set(r,g,b);
```


#### Depth map

C'est quasiment le meme principe : 

![Pasted image 20260206222304.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260206222304.png)

Le dernier wrangle est juste beaucoup plus simple : 

```C
float depth = point(1, "out", @ptnum);

v@P += set(0, depth*.3, 0);
```

*Remarquons la dernière ligne : elle sert à appliquer la depth générée à la position des points, pour déformer réellement la grid en 3 dimensions*


## Références


Un model de depth déjà pret pour onnx : [julienkay/sentis-MiDaS · Hugging Face](https://huggingface.co/julienkay/sentis-MiDaS)


> [!example]- Flashcards
> ...




## Liens 




