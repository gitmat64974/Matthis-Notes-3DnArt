---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Instancer LOP/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.668+01:00","mtime":"2026-11-26T10:50:29.783+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SOLARIS]]","[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

Fonctionne exactement comme un copy to points SOP. Son fonctionnement est assez instinctif : les prototypes sont la ou les sources et les target points sont les points de duplication

*D'ailleurs dans la version 22 il est maintenant appelé copy to points LOP*


Parametres : 
- Method : Là on vient dire quelle est la méthode d'instanciation (Point instancer, reference, instanceable reference, etc)
- Prototype index : Là on vient dire quel source est instanciée (une seule, laquelle, plusieurs en random, selon le name attribute etc)


### Les différents types d'instancing

Point instancer : 
- L'intérêt est qu'il permet d'overrider simplement par la suite la geo instancée (ou un materiau etc) par une autre en la remplaçant simplement à l'endroit exact du scene graph tree

Copy : 
- Chaque geo est copiée entièrement avec les matériaux etc (*Si on veut etre plus précis c'est le fichier usd qui est référencé à chaque fois sur chaque copie, donc c'est comme si on avait utilisé un reference LOP pour chaque copie*). Donc si on veut overide, ça ne va le faire que sur une seule géo

Reference : 
- Les references instancées référencent la primitive définie comme étant la source (*et non le fichier usd de la source comme le mode copy*). Donc comme avec le point instancer, on peut facilement overide la geo ou le matériau etc instancé par un autre. Mais ce qu'il y a de plus que la point instancer, est qu'on peut également overide seulement une seule reference si l'on veut, donc comme le mode copy mais sans être aussi lourd

Instanceable reference : 
- Comme le mode reference, sauf que **les instances viennent référencer la source uniquement en globalité (sans prendre en compte les shaders, geos etc) en lui appliquant seulement des transformations**. Donc par défaut on ne peut override que comme le point instancer. Si on veut tout de même overide une instance en particulier : 
	- Configure primitive LOP pour désinstacer l'instance précise -> matériau ou geo d'overide -> Configure primitive LOP pour réinstancer l'instance précise

Ordre de rapidité : 
1. Point instancer
2. Instanceable reference
3. Reference
4. Copy

Instanceable reference : Le meilleur compromis entre rapidité et flexibilité

---



## Références


> [!example]- Flashcards
> ...




## Liens 




