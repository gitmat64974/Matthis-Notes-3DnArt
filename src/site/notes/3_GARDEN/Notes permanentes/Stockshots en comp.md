---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Stockshots en comp/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.742+01:00","mtime":"2026-04-24T17:43:18.989+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["#cours [[Cours de compositing ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-02-27","aliases":null}}
---


## La note 

Un StockShot est généralement un métrage d'archives (= capture vidéo) d'un phénomène visuel, qu'il s'agisse de fumée, de poussière, d'eau, etc.

Etapes :

1. Node read
2. nœud [Shuffle] pour placer le canal 'R' dans le canal 'A' pour que ce canal fonctionne également comme le canal Alpha
3. Un grade pour ajuster l’alpha (changer le channel → alpha) puis un grade pour ajuster la couleur
4. node premult
5. card -> scene -> scanline render

On peut ensuite venir masquer le premier plan avec la zdepth pour intégrer le stock shot

#### Nodes pour retimer

> [!multi-column]
> 
> > [!NOTE]+ FrameHold
> > ![Capture d'écran 2025-05-12 222212.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20222212.png)
> > 
> > The [FrameHold] will Freeze the StockShot on the desired frame. Perfect to get a still Frame from a StockShot 
> 
> > [!NOTE]+ Retime
> > ![Capture d'écran 2025-05-12 222624.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20222624.png)
> > 
> > The [Retime] node is the most powerful Time node. It can adjust the speed & the frameRange of the input. An absolutely powerful node 😎
> 
> > [!NOTE]+ TimeOffset
> > ![Capture d'écran 2025-05-12 224943.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20224943.png)
> > 
> > The [TimeOffset] will delay the frameRange of the input by the desired frame amount. Perfect to adjust the timing of your StockShot to a specific timing in your Shot!
> 
> > [!NOTE]+ AppendClip
> > ![Capture d'écran 2025-05-12 224902 1.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20224902%201.png)
> > 
> > The [AppendClip] will add a second input at the last frame of a first one. Perfect to combine two Stockshots together & Blend them together using the ‘FadeIn’ & ‘FadeOut’ attributes if your first one is too short!
> 

## Références



## Liens 




