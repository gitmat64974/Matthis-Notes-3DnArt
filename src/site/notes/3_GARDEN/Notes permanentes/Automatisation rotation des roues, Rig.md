---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Automatisation rotation des roues, Rig/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[RIG]]"],"source":["notes Julie"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-12-12","aliases":["rotation des roues automatique en fonction de la translation du véhicule, rig maya"]}}
---

## La note 

1. Créer deux locators parentés au Ctrl_Chassis (1 roue avant, 1 roue arrière)
    Les caler au milieu des roues, avec le LRA des roues
    
2. Créer **controleurs** à côté des roues
    
3. Nod editor : load les deux locators et les deux controleurs des roues (+ enlever les shapes) + le Ctrl_Gen
    
4. **Constraint** parent entre Locators et Grp_Roues
    
5. 1 tour de roue = 360°
    
    Ctrl T pour diamètre roue
    
    Formule automatisation :
    
    > $$(Distance Parcourue / Circonférence) * 360$$
    
6. Créer un **multiply Divide** :
    
    - Mode divide
        
    - Input 1 : TZ Ctrl_Gen
        
    - Input 2 : Taper circonférence roue
        
7. Créer un autre **Multiply divide**
    
    - Mode multiply
        
    - Input 1 : 360
        
    - Input 2 : Connecter output X Multiply divide 1 à input2X (résultat 1er Md)
        
    - OutputX : Le connecter au RX du Loc roues avant et du Loc roues arrières (Si roues avant et arrières ont la même taille)
        

---

### **Le faire avec Ctrl_Fly :**

1. Ajouter nod Ctrl_Fly dans nod editor
2. Créer nod addDoubleLinear + le mettre entre Ctrl_Gen (input 2) et 1er mD
    
    (Ctrl_Fly = input 1)
    
3. Activer/ désactiver roues du fly :
    
    - Input 1 : TZ Ctrl_Fly
        
    - Input 0 : **Créer un Multiply divide : 0*1**
        
    - Output blend = Input 1 du addDoubleLinear
        
    - $\rightarrow$ Attribut blender : 0 = non/ 1 = oui
        
4. Créer un attribut en boolean dans Ctrl_Fly pour activer/ désactiver roues du fly
    
    Connecter cet attribut à l’attribut blender du blendTwoAttr
    

---

### **PB si rotation du foodtruck : Gimbal lock**

1. Créer nod decomposeMatrix
    
    Connecter World inverse matrix [0] (Ctrl_Gen) à InputMatrix nod decomposeMatrix
    
2. Multiply : mettre -360 à la place de 360 (ou entre matrix et add, mettre mD à * -1)
    

---

_Souhaitez-vous que je génère un résumé des connexions nodales sous forme de tableau pour clarifier le flux ?_


## Références


> [!example]- Flashcards
> ...




## Liens 




