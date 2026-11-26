---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Mouvements de caméra/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:19.960+01:00","mtime":"2026-04-24T17:43:18.861+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/STORYBOARD]]","[[3_GARDEN/Notes permanentes/CINEMA]]"],"source":["[[Les techniques du storyboard ou scénarimage]] / [[1er et 2e cours analyse filmique esma 3d2]] / [[Cours compositing Rebuild Shot (insecte 3D2)]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-08-28","aliases":null}}
---


## La note

- Panoramiques → cam fixe qui pivote. Peut être horizontal, vertical ou oblique. Fonction de dévoilement. Un point de vue plus omniscient
- Travelling → Mouvement de la cam sur un axe. Rentrer dans la diegese du film. Il nous fait rentrer dans l’action
    - Travelling avant, arrière, latérale, circulaire
    - Travelling d’accompagnement → quand il y a tjrs une même distance entre la cam et le sujet
- Panotravelling → combiner travelling et panoramique. On peut même en combiner plus
- Caméra épaule : soutenue par le cadreur, occasionnant un tremblement voire des sautes du cadre
- Mouvement de grue (plongée totale par exemple) ou aujourd’hui avec le drones
- Transtrav / travelling optique: association simultanée du travelling avant ou arrière à un zoom optique (ex. Vertigo-> effet Vertigo). crée un grand désordre, perturbation. L’origine c’est vertigo d’[[3_GARDEN/Notes permanentes/Alfred Hitchcock\|Hitchcock]]
- Steadicam : caméra portée par un opérateur sur un bras stabilisateur, elle sert à sécuriser le cameraman dans les scènes qui bougent beaucoup. 
- Jump cut → des sautes dans la façon dont c’est filmé. Traduire un lien avec le temps qui passe. Le temps s’étire où se rétracte. Fait sortir de l’univers diégetique.
- Prise de vue sur grue (crane shot) ou aujourd'hui avec des drones : mouvements verticaux et latéraux 
- Zoom : Le **zoom** simule un déplacement de caméra par le réglage de l’objectif dans le sens du grossissement (zoom avant) ou du rapetissement (zoom arrière).
#### En Anglais 

|Movement Name (ENG)|(FR)|Description|
|---|---|---|
|Zoom|idem|Ajustement de la LongueurFocale/du Zoom de la Camera sur l’axe N (sans Translation ni Rotation). Mouvements associés: - Rack-Focus = Passage du point focal d’un objet à un autre dans la profondeur de champ; - Dolly-Zoom/TransTrav/TravellingCompensé = Sur un Dolly, ajustement de la LongueurFocale/Zoom pour garder le plan en focus à la même distance perçue, tout en éxagérant la perspective sur le reste de l’image.|
|Tilt|Panoramique vertical|Rotation verticale de la Camera sur l’axe U (sans Translation). — TiltUp = Rotation vers le Haut; — TiltDown = Rotation vers le Bas;|
|Pan|Panoramique horizontal|Rotation horizontale de la Camera sur l’axe V (sans Translation). — Pan Left = Rotation vers la Gauche; — Pan Right = Rotation vers la Droite;|
|Cant / Roll|idem|Rotation sur l’axe N de la Camera sur l’axe N (sans Translation). — Cant Left = Rotation anti-horaire; — Cant Right = Rotation horaire;|
|Truck|Travelling Gauche/Droite|Translation latérale de la Camera sur l’axe U (sans Rotation). — Truck Left = Translation vers la Gauche; — Truck Right = Translation vers la Droite;|
|Pedestal|Travelling Haut/Bas|Translation d’élévation verticale de la Camera sur son pied sur l’axe V (sans Rotation). — Pedestal Up = Translation vers le Haut; — Pedestal Down = Translation vers le Bas;|
|Dolly|Travelling Avant/Arrière|Translation dans la profondeur de la Camera sur l’axe N (sans Rotation). — Dolly Out = Translation vers l’Arrière; — Dolly In = Translation vers l’Avant;|
|Arc|idem|Translation+Rotation Horizontale de la Caméra le long d’un chemin, le long d’un vecteur dans la direction de l’axe V de la Caméra. La caméra est orientée pour préserver l’objet visé dans le cadre à son centre. — Arc Left = Déplacement vers la Gauche; — Arc Right = Déplacement vers la Droite;|
|Tongue|idem|Translation+Rotation Horizontale de la Caméra au bout d’une grue, le long d’un vecteur dans la direction de l’axe V de la Caméra. La rotation de la Caméra est compensée pour qu’elle préserve son axe de visée. — Tongue Left = Déplacement vers la Gauche; — Tongue Right = Déplacement vers la Droite;|
|Crane / Boom|idem|Translation+Rotation Verticale de la Caméra au bout d’une grue, le long d’un vecteur dans la direction de l’axe V de la Caméra. La rotation de la Caméra est compensée pour qu’elle préserve son axe de visée. — Crane Up = Déplacement vers le Haut; — Crane Down = Déplacement vers le Bas;|

#### Tips de mouvements de caméra

Source : [8 Mistakes to Avoid when Animating Cameras #b3d - YouTube](https://youtu.be/gLNl8Lidzk0?si=TmLCn1cNHjI92-a1)

> [!multi-column]
> 
> > [!info]+ Arrêts et départs brusques
> > La caméra ne doit pas commencer ou s'arrêter net. Dans la réalité, une caméra a du poids et de l'inertie. Il faut utiliser les **courbes de Bézier** dans l'éditeur graphique pour créer un **ralentissement progressif (ease out)** à la fin du mouvement et une **accélération progressive (ease in)** au début.
> 
> > [!info]+ Utilisation des courbes de Bézier par défaut
> > Les transitions *ease out/in* automatiques de Blender peuvent sembler artificielles et **trop parfaites**. Il est conseillé de **modifier ces courbes** en les étirant ou en ajoutant des clés pour **rompre l'uniformité**. L'add-on *shakeify* peut aussi ajouter un **tremblement aléatoire**.
> 
> > [!info]+ Finir le plan trop tôt
> > Après un mouvement de caméra, surtout pour révéler quelque chose, **ne coupez pas immédiatement**. Laissez au public **quelques instants** pour absorber la nouvelle information ou profiter de la vue.
> 

> [!multi-column]
> 
> > [!info]+ Mouvement de caméra trop rapide
> > Il faut souvent se référer à la réalité. À moins de vouloir simuler un drone rapide, une caméra sur un hélicoptère ou un avion irait à une certaine vitesse. **Ralentir le mouvement** peut le rendre plus **réaliste** et plus **épique**.
> 
> > [!info]+ Tremblement de caméra disproportionné
> > Si la caméra bouge lentement (vitesse de marche), le tremblement **ne doit pas simuler une course effrénée**. Assurez-vous que l'**énergie du tremblement corresponde à celle du mouvement global** de la caméra.
> 
> > [!info]+ Caméra devant le personnage
> > C'est une **règle simple** : **ne laissez jamais la caméra devancer l'action** du personnage. **Suivez toujours le mouvement** du personnage en ajoutant un **léger décalage (lag)**, comme si la caméra essayait constamment de le rattraper. Cela donne au spectateur l'impression de **découvrir l'action en même temps** que le réalisateur.
> 

> [!multi-column]
> 
> > [!info]+ Déconnexion entre plusieurs mouvements
> > Lorsque vous combinez plusieurs mouvements de caméra dans un même plan (ex: grue puis travelling), **ne les faites pas s'arrêter complètement** l'un avant que l'autre ne commence. Utilisez des objets *"empty"* parents pour organiser les mouvements et **superposez légèrement leurs animations**. L'ajout de **courbes de Bézier** et d'un **léger tremblement** aide à rendre la transition plus **naturelle**.
> 
> > [!info]+ Perte d'énergie entre les plans
> > Lorsque vous montez plusieurs plans ensemble, **pensez à la séquence dans son ensemble**. Si vous avez une série de plans qui se rapprochent, le dernier plan **ne devrait pas passer brusquement à une caméra statique**. **Ralentissez progressivement** le mouvement de caméra tout au long de la séquence pour que les **transitions entre les plans soient fluides**.
> 



## Références 


## Liens 

