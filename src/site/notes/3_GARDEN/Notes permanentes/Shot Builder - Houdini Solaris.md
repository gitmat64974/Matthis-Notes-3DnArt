---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Shot Builder - Houdini Solaris/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[USD]]","[[Lighting dans Houdini|Solaris]]","[[HOUDINI]]","[[LIGHTING]]"],"source":["https://youtu.be/xE0M6a7mJKc"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-02","aliases":null}}
---

## La note 

Le ***Shot Builder*** est une boîte à outils de Houdini 21 — uniquement dans le contexte Solaris/LOPs.
Son but : donner « un pipeline dans une boîte », c'est-à-dire toute l'organisation d'un projet multi-plans : plusieurs shots, plusieurs couches de travail (layout, lookdev, lighting…), plusieurs artistes — tout cela gérable depuis un SEUL fichier Houdini. 

En utilisant le shot Builder, on édite des layers USD ([[USD Layers|USD Layers]]) côte à côte ou en équipe. La numérotation des versions (v1, v2…), le chargement du bon shot à chaque bascule : tout se fait en coulisses. Les artistes travaillent et le pipeline s'organise tout seul.

> [!example]+ Notions en prérequis
> - [[USD Layers|USD Layers]]
> - Unité (unit) : le bloc de base de la hiérarchie. Souvent un shot (un plan du film), mais ça peut être un asset, un environnement… Chaque type d'unité contient son propre paquet de couches.
> - project.json : le petit fichier « plan du projet ». Il déclare les types d'unités et les layers de chacune. Toute la structure de dossiers et de fichiers en est déduite.
> - HPR Resolver : l'asset resolver intégré de SideFX. Une resolver est une boîte noire qui gère les chemins de fichiers : où ranger les exports, quelle version (v1, v2, v3) charger — toujours la plus récente, sauf si vous l'épinglez.
> - 4 nodes essentiels : Shot Load (charger le shot courant), Shot Layer Edit (éditer un layer), Shot Switch, Shot Output (publier les données / rendre les images).

### Utilisation Studio et bénéfices

![k_806.jpg](/img/user/Pi%C3%A8ces%20jointes/k_806.jpg)

Prenons l'exemple de cinq artistes métiers différents, chacun avec SON fichier Houdini dans son coin (ici USD Workflow_Layout, _Animation, _Camera, _Shading, _Lighting), mais tous branchés sur le même projet. Chacun édite ses couches, publie avec Shot Output… et la scène « courante » des autres se met à jour sans se demander.

- L'artiste lookdev met en place un shading sur le plan, exporte sa couche sur les shots.
- L'artiste lighting ouvre son fichier, recharge, place la lumière d'environnement pour tous les shots, exporte.
- L'artiste layout actualise : nouveaux modèles, nouveau shading, nouvelles lumières sont déjà dans SA scène.
- Il peut différencier un asset uniquement dans le shot 001 (branche Shot Split) et republier ; le lighting artist voit aussitôt si son éclairage tient toujours. Chaque métier avance en parallèle, sans jamais écraser l'autre.

Concrètement, ça change quoi : la coordination passe par des couches publiées et non par des échanges de fichiers

### Utiliser un projet Shot Builder déjà setup





---

### Créer un projet Shot Builder de A à Z
#### Etape 1 : Le project.json

Dans Houdini vide : panneau Shot Builder Project → New Project… La boîte de dialogue demande simplement comment configurer le projet : « Shots with Sublayers » (mode équipe : chaque layer est un fichier séparé) ou « No Sublayers » (mode solo, tout dans un seul fichier). L'option sublayers est l'usage principal du workflow.

![](https://i.imgur.com/Chqbk96.png)

Le project.json définit la structure de base des layers de chaque shot, c'est à dire donc ce qu'on veut qu'il y ait dans chaque shot en terme de départements. *Par exemple par défaut on a lighting, fx, animation et layout. Mais on pourrait très bien avoir environnement, lookdev, animation, camera, fx etc*
Ce fichier se crée par défaut là où se trouve le .hip, et sera ainsi reconnu automatiquement par tout fichier houdini au même endroit

Il est donc très intéressant de venir éditer ce json dans VSCode. Quelques modifs classiques à faire : 

- Renommer le projet. Remplacer une couche existante (lighting → lookdev) et en ajouter une (« camera ») en copiant-collant un bloc — pensez à la virgule du bloc précédent, et jamais de virgule sur le dernier bloc : le JSON est pointilleux.
- Passer les couches de .usda à .usd : le format texte .usda reste lisible par un humain, mais dès qu'on y exporte de la géométrie ou de l'animation, il devient énorme. Le binaire .usd est plus compact.
- Ajouter un second type d'unité « assets » avec deux couches seulement : model et look.

![](https://i.imgur.com/RI27kgz.png)


#### Etape 2 : Créer les shots 

Retour dans le panneau Shot Builder (onglet « Shot Builder Project (Beta) » en bas de la fenêtre). Le panneau montre la hiérarchie : Unit / Linked Units / Start Frame / End Frame. Clic droit sur le type « shot » → Add new "shot" unit…

![](https://i.imgur.com/44dD9f5.png)

La boîte Add Shot reprend exactement les couches du JSON (lookdev, fx, animation, layout, camera). On nomme « 001 », on clique Create — la fenêtre reste ouverte pour enchaîner 002 et 003 — puis OK. 

L'arborescence est créée donc en même temps sur le disque (un dossier shots avec les fichiers à l'intérieur), et un menu déroulant « Shot » apparaît en haut de Houdini : l'interrupteur du projet. Vous passez du plan 001 au plan 003 sans quitter ni rouvrir quoi que ce soit.

#### Etape 3 : Construire ce qui est commun à tous les shots

![](https://i.imgur.com/RoQHbR9.png)


Shot Load est le point d'entrée de tout réseau Shot Builder. Il lit le plan, charge les couches USD du shot sélectionné dans le menu déroulant, et son panneau latéral (Sublayers — 'shot/s001') liste les couches avec leur version — « No Layer Detected » tant qu'elles sont vides.

Pour remplir une couche : clic droit dessus → Edit Layer (ou Create Layer si elle n'existe pas encore) : Houdini pose automatiquement le nœud Shot Layer Edit avec la bonne syntaxe.

- On double-clique dans le nœud : c'est là que le travail a lieu (ici, un simple grid). Tout ce qu'on fait dans ce sous-réseau n'écrit QUE dans la couche cible — impossible d'écraser le travail du voisin.

![](https://i.imgur.com/Iilu0FZ.png)

Shot Output écrit le travail en USD dans le pipeline. Mode : Publish (uniquement les données USD), Render (uniquement les images du shot), ou les deux. Pour exporter une couche qui n'existe que dans les unités « shot », on tape le motif _shot/_ dans Multi-Shot → l'export déroule tous les shots. Save to Disk, et c'est parti.

Dépannage vu dans la vidéo : si le save échoue, deux causes classiques — la syntaxe du motif d'export, ou un nœud fautif : ouvrir le nœud, remonter au top network et forcer Cook in Process sur le nœud défaillant, puis relancer.

Résultat dans l'explorateur : un dossier shot_layout.usd contenant la première version du fichier ; le Shot Load voit la mise à jour immédiatement. Comme le motif visait tous les shots, le plan ajouté existe désormais dans chaque plan du film — un seul montage, trois shots servis.

#### Etape 4 : Différentier un plan

![](https://i.imgur.com/Zn4WKkN.png)


PROBLÈME : jusqu'ici tout était identique sur les trois shots, mais on veut souvent une variation par plan (ex. un élément qui n'existe que dans le shot 001). RÉPONSE : Shot Split/Shot Switch — un nœud qui ramifie le réseau en branches, avec un Output Shot Pattern par branche : shot/s001, shot/s002, shot/s003.

Confort notable : quand on plonge dans une branche, le contexte du haut (shot/s001…) bascule automatiquement sur le bon shot — plus de risque d'éditer le mauvais plan. On reboucle tout sur un seul Shot Output.

#### 5. Ajouter une couche en plein projet

![](https://i.imgur.com/Oxi1nZS.png)


Le scénario : la couche lookdev doit être coupée en deux — une personne sur le shading, une autre sur le lighting — parce qu'ils ne doivent pas écraser le travail l'un de l'autre. On ajoute des couches au vol, sans re-créer le projet :

- Un Shot Layer Edit laissé de côté, Create New Layer cochée, nom : shading.usd (⚠️ l'extension .usd est obligatoire, sinon ça échoue), New Layer Index 0. Exporter avec un Shot Output comme d'habitude.
- Répéter pour lighting.usd, Index 1 cette fois. ⚠️⚠️ À NE PAS OUBLIER sur cette seconde couche : décocher Clear Source Layer — sinon elle supprime la couche shading qu'on vient de créer.
- Exporter une fois, et les deux nouvelles couches apparaissent dans la hiérarchie de tous les shots visés.

#### 6. Les nested layers

![](https://i.imgur.com/iDZPZbp.png)


Dernier étage de la fusée : imbriquer des unités dans d'autres unités. Cas type : un environnement (un décor complet) réutilisé dans plusieurs shots. Dans le JSON : créer un type d'unité « envs » (avec sa couche ./model.usd), puis dans le type « shot » ajouter la ligne **env**: {} — deux underscores, « env », deux underscores, accolades : c'est l'écriture « je réserve un emplacement pour une unité env ici ».

```json
"__env__": {}
```

Effet dans Houdini : à la création d'un nouveau shot, la ligne envs de Add Shot devient un menu déroulant — on choisit l'environnement à embarquer. 

![](https://i.imgur.com/PDTO9ZO.png)

La décor se remplit une fois dans son unité à lui, et tous les shots concernés l'affichent. On peut l'ajouter rétroactivement : clic droit sur un shot existant → add, puis un refresh (ou un redémarrage de la scène) l'applique.

### Un regard sur le contenu des fichiers usd créés

Le _scenegraph_ de chaque shot est construit à partir de différents _Layers_, ce qui permet de cloisonner les différentes étapes de travail, et de les travailler en parallèle, de façon collaborative, sans risque d’écraser le travail des autres membres de l’équipe.

Concrètement, un shot est un fichier usd, dont la structure ressemble à ceci :

- _shot_0010.usda_
    
    ```c
    #usda 1.0
    (
    	metersPerUnit = 0.01
    	subLayers = [
    		@./charas.usd@,
    		@./lighting.usd@,
    		@./layout.usd@,
    		@./camera.usd@
    	]
    	upAxis = "Y"
    )
    ```
    

Chaque _layer_ est stocké dans un fichier USD dédié, dans lequel sont _référencés_ les divers éléments qui le composent. Par exemple, un fichier `set_v1.usda` :

```json
#usda 1.0
(
    metersPerUnit = 0.01
    upAxis = "Y"
)

def "set_jardin" (
    prepend references = @C:/WORK/3D4_2027/PROD/usd/sets/set_jardin/set_jardin.usda@</set>
)
{
}

```

Le node **Shot Load** permet de modifier individuellement chaque layer, et les modifications sont enregistrées dans une nouvelle version.

Par défaut, le node va automatiquement chercher la dernière version (c’est le principe d’un _Resolver_), mais il est possible de choisir, pour chaque layer, de revenir sur une version antérieure.

#### Répertoire

Le principe est de préparer une structure de répertoire séparant les données produites par l’équipe et l’assemblage final des shots (*un dossier usd contenant tous les usd à référencer et un dossier sequence contenant chaque shot builder project*)

Voir [[3_GARDEN/Notes permanentes/Pipeline USD|Pipeline USD]] pour un exemple de répertoire qui fonctionne pour cet outil

## Références


> [!example]- Flashcards
> ...




## Liens 




