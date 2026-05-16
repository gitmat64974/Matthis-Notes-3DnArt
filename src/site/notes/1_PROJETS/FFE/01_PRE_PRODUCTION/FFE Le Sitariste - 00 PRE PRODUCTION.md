---
{"dg-publish":true,"permalink":"/1_PROJETS/FFE/01_PRE_PRODUCTION/FFE Le Sitariste - 00 PRE PRODUCTION/","dg-note-properties":{"MOC":null,"tags":null,"status":"En cours","weight":10,"type":"Projet","creation date":"2026-04-04","Startdate":"2026-04-04","endDate":"2026-06-04","tn_and_checkbox_tasks":0,"tn_and_checkbox_tasks_completed":0,"banner":"![plan_final.png](/img/user/Pi%C3%A8ces%20jointes/plan_final.png)","Personnes":["Matthis","Julie","Nerys","Ludo","Brayane","Enzo","Raphael","Berenice","Hugo","Elliot","Titouan"]}}
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
    sort:
      - property: file.ctime
        direction: DESC
    limit: 5
    columnSize:
      file.name: 327
      note.objectifs atteints: 364

```



## Documentation

- [[1_PROJETS/FFE/01_PRE_PRODUCTION/Documentation/FFE Le Sitariste - SYMBOLES|FFE Le Sitariste - SYMBOLES]]

- [[3_GARDEN/Notes permanentes/Théâtre en Inde|Théâtre en Inde]]
- [[3_GARDEN/Notes permanentes/Vêtements en Inde|Vêtements en Inde]]

- [[3_GARDEN/Notes permanentes/Mythologie hindoue|Mythologie hindoue]]


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
