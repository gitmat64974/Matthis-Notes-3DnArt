---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/11e cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2026-01-23"}}
---



## Applicatif Houdini : Simu de flèches


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

![](https://i.imgur.com/VtPUdYF.png)

On va créer un éméteur pour les flèches qui sera une grid, symbolisant une ligne d'archers

On va créer une velocity qui sera égale d'abord à la normale des points définie par le node normal juste avant : 

```C
v@v = v@N;

// régler la velocité initiale
v@v *= ch('velocity_mult');
```

#### POP Network

On ajoute un popnet

On ajoute une force de gravité

POP Source : 
On ajoute de la variance dans la velocité : cela se passe dans l'onglet attributes 

On vient régler le nombre de particules et leur espérance de vie : (valeurs arbitraires)
- Const birth rate : 10
- life expectancy : 20


---

Le setup de simu de flèches : 

![Pasted image 20260123162758.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260123162758.png)

---

Ensuite on se sert de ces flèches comme trigger d'anim de mort par exemple

-> Voir [[3_GARDEN/Notes permanentes/Crowd Houdini|Crowd Houdini]]



</div></div>
 



