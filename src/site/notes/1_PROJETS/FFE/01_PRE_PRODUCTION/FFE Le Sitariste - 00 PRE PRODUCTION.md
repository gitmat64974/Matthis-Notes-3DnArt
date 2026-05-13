---
{"dg-publish":true,"permalink":"/1-projets/ffe/01-pre-production/ffe-le-sitariste-00-pre-production/","dg-note-properties":{"MOC":null,"tags":null,"status":"En cours","weight":10,"type":"Projet","creation date":"2026-04-04","Startdate":"2026-04-04","endDate":"2026-06-04","tn_and_checkbox_tasks":0,"tn_and_checkbox_tasks_completed":0,"banner":"![plan_final.png](/img/user/Pi%C3%A8ces%20jointes/plan_final.png)","Personnes":["Matthis","Julie","Nerys","Ludo","Brayane","Enzo","Raphael","Berenice","Hugo","Elliot","Titouan"]}}
---

# Suivi


- [ ] test
## Weekly reviews


```base
model:
  version: 1
  kind: Table
  columns: []
pluginVersion: 1.0.0
filters:
  and:
    - file.folder.contains("1_PROJETS/FFE/00_REVIEWS")
    - file.name != "00_REVIEWS.base"
    - file.name != "Contexte"
views:
  - type: table
    name: Table
    groupBy:
      property: file.folder
      direction: ASC
    order:
      - file.name
      - objectifs atteints
      - mood de l'equipe
    sort:
      - property: file.ctime
        direction: DESC
    limit: 5
    columnSize:
      file.name: 299
      note.objectifs atteints: 158

```



## Documentation






## Départements de pré production


```base
model:
  version: 1
  kind: Table
  columns: []
pluginVersion: 1.0.0
filters:
  and:
    - file.folder == "1_PROJETS/FFE/01_PRE_PRODUCTION"
    - file.name != "01_PRE_PRODUCTION.base"
    - file.name != "FFE Le Sitariste - 00 PRE PRODUCTION"
formulas:
  Untitled: "if(tn_and_checkbox_tasks > 0, html(\"<div style='width: 100%; height: 8px; background: #2d1b69; border-radius: 4px; overflow: hidden'><div style='height: 100%; width: \" + ((tn_and_checkbox_tasks_completed / tn_and_checkbox_tasks) * 100).round(0) + \"%; background: \" + if(((tn_and_checkbox_tasks_completed / tn_and_checkbox_tasks) * 100).round(0) <= 25, \"#ef4444\", if(((tn_and_checkbox_tasks_completed / tn_and_checkbox_tasks) * 100).round(0) <= 50, \"#f59e0b\", if(((tn_and_checkbox_tasks_completed / tn_and_checkbox_tasks) * 100).round(0) <= 75, \"#eab308\", if(((tn_and_checkbox_tasks_completed / tn_and_checkbox_tasks) * 100).round(0) < 100, \"#0ea5e9\", \"#10b981\")))) + \"; transition: width 0.3s ease; border-radius: 4px;'></div></div>\"), \"\")"
  Time progress: "if(EndDate > Startdate, html(\"<div style='width: 100%; height: 8px; background: #8d6e63; border-radius: 4px; overflow: hidden'><div style='height: 100%; width: \" + (((date(today()) - Startdate).days / (EndDate - Startdate).days) * 100).round(0) + \"%; background: \" + if((((date(today()) - Startdate).days / (EndDate - Startdate).days) * 100).round(0) >= 100, \"#10b981\", if((((date(today()) - Startdate).days / (EndDate - Startdate).days) * 100).round(0) <= 50, \"#10b981\", if((((date(today()) - Startdate).days / (EndDate - Startdate).days) * 100).round(0) <= 75, \"#eab308\", \"#ef4444\"))) + \"; transition: width 0.3s ease; border-radius: 4px;'></div></div>\"), \"\")"
properties:
  formula.Untitled:
    displayName: Task progress
views:
  - type: table
    name: Table
    order:
      - file.name
      - formula.Untitled
      - formula.Time progress
      - Personnes
    sort:
      - property: formula.Untitled
        direction: DESC
      - property: file.mtime
        direction: DESC
    columnSize:
      file.name: 289
      formula.Untitled: 137
      formula.Time progress: 123

```




### Organisation

Drive : GGDrive [FFE_LeSitariste - Google Drive](https://drive.google.com/drive/folders/1-I-_NonzcmTJTf9Oa8SBtO0EqWb4ZKM4?usp=sharing)
Discord : espace de discussion



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-projets/ffe/01-pre-production/ffe-le-sitariste-scenario/#dossier-scenario" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



# Dossier scenario

### Synopsis court





### Synopsis développé


Ecran noir…

On entend un bruit de bois qui se brise…

Le soleil se lève et les premières lueurs du jour éclairent peu à peu un sitar brisé.

Un jeune homme à la silhouette élancée s’en saisit et sort de la pièce encore plongée dans la pénombre.

Sitar en main, Ekma se mêle aux passants qui s’affairent dans la rue animée d’une ville indienne. Parmi le brouhaha de la foule, un homme clame une annonce. Il parle d’une audition ayant lieu le soir même au palais, une occasion unique de devenir le sitariste du Sultan.

Ekma arrive sur une place occupée d’étals de toutes sortes, et repère le modeste étal d’une vieille luthière. Il s’en approche avec l’espoir qu’elle puisse réparer son sitar. Celle-ci n'a pas le matériel nécessaire pour et lui en propose un autre, sobre mais fonctionnel, qu’il refuse avec arrogance. Dans son agitation, il bouscule une clochette qui tombe au sol, mais à la place d’un léger tintement, un bruit sourd retentit.

Ekma sursaute et se retourne à la recherche de la provenance du son. La foule s’est figée, tous les regards sont posés sur lui, et au milieu de cette foule, se tient un homme portant un masque coloré aux traits monstrueux, un gong dans la main. Le jeune homme est subitement au centre de l’attention, les regards pèsent sur lui, il se fige, ne sachant que faire.

Puis la foule se remet en mouvement, les passants reprennent leurs occupations, et l’homme masqué disparaît au milieu du monde. Padma, la vieille luthière, lui indique les montagnes d’un geste de la main. Là-bas, au palais du Sultan, il trouvera un luthier talentueux, capable de satisfaire ses attentes.

Il s’en va d’un pas rapide, sans prendre la peine de la remercier.

Sous le soleil de midi, Ekma traverse un canyon démesurément grand, la chaleur se fait ressentir. Des masques se détachent dans les roches des montagnes.

Il entre dans un village troglodyte, désert, et repère une boutique. Piqué par la curiosité, il y entre et découvre Padma, en train de réparer un sitar, mais ne la reconnaît pas. Elle porte des parures et sa tenue est différente. Un homme masqué est assis au fond de la pièce, il joue avec des bagues dans un cliquetis répétitif.

Ekma s’adresse à la vieille femme, demandant à ce que son sitar soit réparé sur le champ. Celle-ci est en train de poncer un morceau de sitar, et ne répond pas immédiatement. Le silence s’étire, brisé seulement par le bruit métallique des bagues s’entrechoquant. Elle lève finalement la tête et le regarde d’un air désolé, poussant une longue liste de commandes et une plume vers lui.

Le jeune homme ne cesse de jeter des coups d'œil vers le fond de la boutique, paraissant de plus en plus troublé. Il repousse la liste abruptement, et après avoir tenté sans succès de la convaincre, il s’en va d’un pas pressé. Le bruit s’atténue à mesure que le sitariste s’éloigne.

L'après-midi touche à sa fin lorsqu’il arrive au pied du grand palais. Les lourdes portes de pierre, surplombées de masques sculptés, s’ouvrent d’elles même à son approche. Il se retrouve face à un immense escalier orné de gravures toutes plus belles les unes que les autres. Il gravit alors les étages du palais un à un jusqu’à se retrouver sur une somptueuse terrasse.

Encore une fois Padma est mystérieusement présente, elle porte une tenue plus complexe que les fois précédentes et elle est couverte de bijoux et d’or. Assise près d’un grand rideau, elle accorde un sitar. Ekma, qui ne semble toujours pas la reconnaître, se dirige vers elle.

Le jeune homme lui demande s'il arrive trop tard pour l’audition, ce à quoi Padma répond par la négative. On entend une mélodie provenant de derrière le rideau, elle lui confie que le candidat n’a pas le niveau suffisant pour être retenu. Il lui demande avec empressement de réparer son instrument et le lui passe sans attendre sa réponse.

Elle l’examine minutieusement, et, ne semblant rien trouver d’anormal, commence à jouer la même mélodie que celle qu’on entend derrière le rideau, avec une étonnante fluidité. Sa version semble plus complexe et les bruits du palais se taisent comme pour l’écouter, ses mains se déplacent habilement sur le sitar, qui dans ses mains semble en parfait état. Ekma est pris de jalousie et dans un geste brusque, le lui arrache des mains, la repoussant en arrière.

Celle-ci tombe de l’autre côté du rideau, interrompant l’audition.

Elle se retrouve dans un auditorium aux dimensions démesurées, surplombant la scène.

Le soleil couchant inonde la pièce d’une lumière dramatique par de grandes arches.

Le temps semble s’arrêter… On découvre quatre juges masqués, l’un d’eux avec un gong devant lui, un autre jouant avec ses bagues, et les deux derniers murmurant des paroles inaudibles. Ils scrutent un jeune homme assis sur la scène face à eux, sitar en main.

Lorsque Ekma l’aperçoit, il a un mouvement de recul, frappé par l’horreur. L’homme sur scène lui ressemble comme deux gouttes d’eau. Avant qu’il n’ait le temps de réagir, celui-ci tourne la tête et leurs regards se croisent. Sous la surprise, il lâche son sitar qui tombe au sol et se brise.

Le soleil disparaît derrière les montagnes et les dernières lueurs du soir éclairent le sitar. Pendant un instant on aperçoit une fleur de lotus sur un des morceaux brisés avant que la pièce ne soit plongée dans le noir.

Ecran noir…

### Genre 

- Récit de mise en garde
- Cautionnary tale


### Thématique

Thématique : La difficulté de surmonter ses échecs
Ligne thématique : Tant qu'on cherche de fausses excuses (à l'extérieur de nous même) on continue à échouer 


### Personnages

#### Ekam

Objectif dramatique : 
- Réussir l'audition
- Motivation : 
	- Je suis le meilleur et je veux le prouver en réussissant l'audition. Pour cela je veux le meilleur sitar possible
- Comment il compte s'y prendre : 
	- Avoir le meilleur sitar 
- Désir : Réussir l'audition
- Besoin : Accepter l'échec


#### Padma




</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



# Concept art



</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



# Storyboard




</div></div>


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



# DA



</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



# RnD



</div></div>






