---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Cascadeur IA/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[ANIMATION]]","[[3D]]"],"source":["Chaine YT Cascadeur","Site cascadeur"],"Projets":["[[Edna and Maurice projet MIKE]]"],"tags":["note_permanente"],"creation date":"2025-09-29","aliases":null}}
---

---

## La note 

Cascadeur IA est un logiciel d’animation 3D autonome conçu pour simplifier et accélérer la création d’animations de personnages grâce à des outils basés sur l’intelligence artificielle et la physique, sans nécessiter de capture de mouvement traditionnelle. 

Il est particulièrement adapté pour les animateurs, studios de jeux, studios de cinéma, et créateurs indépendants souhaitant créer des animations expressives et physiquement réalistes rapidement

> [!success]- Fiche mémo complète sur la vidéo [Everything About Cascadeur (FULL-FREE-Course!) - YouTube](https://youtu.be/vPwVGuYEk2o?si=PqAXcuaMT3BfCk80)
> # 📝 Fiche Mémo Cascadeur IA - Guide Pratique
> 
> ## 🎯 Fondamentaux & Contrôles de Base
> 
> ## Navigation & Interface
> 
> - **Contrôles souris** : Alt + clic gauche, bouton molette pour navigation 3D standard
>     
> - **Modes d'affichage** : Basculer entre rig traditionnel, mesh et wireframe
>     
> - **Gizmos** : Position, rotation, échelle sur les contrôleurs sélectionnés
>     
> - **Outliner** : Hiérarchie des objets à droite
>     
> 
> ## Système de Contrôleurs
> 
> - **Contrôleurs bleus** = résistent au mouvement automatique
>     
> - **Contrôleurs non-bleus** = suivent automatiquement les mouvements
>     
> - **Désactiver résistance** : Clic gauche + Shift + Z
>     
> - **Sélection multiple** : Shift + clic ou double-clic (joint + enfants)
>     
> 
> ## ⚙️ Configuration & Rigging
> 
> ## Rigging Automatique Rapide
> 
> 1. Importer FBX → Mode Rig → Dire "Oui"
>     
> 2. L'IA devine automatiquement l'emplacement des os
>     
> 3. Ajuster manuellement si nécessaire (glisser-déposer)
>     
> 4. Vérifier mains et os de twist → Générer
>     
> 
> ## Réglage des Os de Twist
> 
> - **Accès** : Mode Box → Sélectionner os twist → Panneau "Twist"
>     
> - **Valeurs recommandées** :
>     
>     - Os proche du poignet : 50%
>         
>     - Os éloigné : 25%
>         
> 
> ## 🎬 Animation & Timeline
> 
> ## Gestion des Keyframes
> 
> - **Keyframes bleus** = sauvegarde automatique des modifications
>     
> - **Déplacer frame** : Clic molette + glisser
>     
> - **Dupliquer frame** : Shift + clic molette + glisser
>     
> - **Ajuster timeline** : Bouton d'échelle automatique
>     
> 
> ## Interpolation & Transitions
> 
> - **Transitions plates** par défaut
>     
> - **Lissage** : Sélectionner frames → Bézier Clamp
>     
> - **Ajouter/Supprimer frames** : Touches + / - du clavier
>     
> 
> ## 🔧 Fonctions Avancées
> 
> ## Physique Automatique
> 
> - **Activer** : Physics → AutoPhysics ON
>     
> - **Mouvement secondaire** : Sélectionner parties → Cocher "Secondary Motion"
>     
> - **Réglages** : Blending local (0-100), Dampening pour relaxation
>     
> 
> ## Position Globale vs Locale
> 
> - **Globale** : Copie exacte un-à-un
>     
> - **Locale** : Position relative maintenue (doigts, armes)
>     
> 
> ## Verrouillage & Contraintes
> 
> - **Verrouiller pose** : Auto Pose Lock State
>     
> - **Verrouiller joints** : Sélectionner + R (déverrouiller = R à nouveau)
>     
> - **Point d'ancrage fulcrum** : Alt + clic gauche sur joint
>     
> 
> ## 🎭 Techniques Spécialisées
> 
> ## Animations Aériennes
> 
> - **Problème flottement** : Physics → Désactiver Physics Corrector
>     
> 
> ## Rotations/Spins
> 
> 1. Sélectionner intervalle → Alt + F (key tout)
>     
> 2. Mode Interval Edit → Linear
>     
> 3. Rotation par chunks < 180°
>     
> 
> ## Ajustement Multi-Frame
> 
> 4. Sélectionner frames → Mode Interval Edit
>     
> 5. Ajuster position → Sortir du mode
>     
> 6. Modification appliquée sur tout l'intervalle
>     
> 
> ## Étirement Timeline
> 
> - **Compresser/Étendre** : Sélectionner frames + Ctrl + T + glisser
>     
> 
> ## 🔄 Outils de Copie & Synchronisation
> 
> ## Tween Machine
> 
> - **Glisser gauche** : Copie frame précédente
>     
> - **Glisser droite** : Copie frame suivante
>     
> - **Milieu** : Mélange partiel
>     
> - **Usage** : Cohérence pieds au sol, armes figées
>     
> 
> ## Position Relative (Armes 2 mains)
> 
> 1. Frame correcte → Double-clic main → Alt + clic droit autre main
>     
> 2. Local → Relative → C (copier)
>     
> 3. Frame cassée → Ctrl + V (coller)
>     
> 
> ## Copie Entre Personnages
> 
> 4. Mode Box → Double-clic poignet → Shift-clic (désélectionner)
>     
> 5. Clic droit Set Pivot → Ctrl + C
>     
> 6. Personnage cible → Même process + Mode Local + Relative → Ctrl + V
>     
> 
> ## 🎪 Physique & Ragdoll
> 
> ## Configuration Ragdoll
> 
> - **Activation** : Physics → Work on Interval
>     
> - **Paramètres** :
>     
>     - **Stiffness Multiplier** : Rigidité des joints
>         
>     - **Dampening** : Vitesse d'arrêt des mouvements
>         
>     - **Floor Friction** : Adhérence au sol
>         
>     - **Floor Bounciness** : Rebond au sol
>         
> 
> ## Processus Ragdoll
> 
> 1. Définir intervalle → Configurer paramètres
>     
> 2. Snap to AutoPhysics → Bake movements
>     
> 3. Connexion Bézier → Physique OFF → Reset AI Physics
>     
> 
> ## 🗂️ Gestion des Pistes & Contraintes
> 
> ## Pistes (Tracks)
> 
> - **Ajouter** : Sélectionner os → Add Track
>     
> - **Supprimer** : Sélectionner piste → Remove
>     
> - **Nettoyage** : Alt + double-clic pour voir connexions
>     
> 
> ## Contraintes Parent
> 
> 1. Mode Rig → Rechercher joints à connecter
>     
> 2. Shift + clic boule bleue joint suiveur
>     
> 3. Additional Actions → Connect
>     
> 
> ## Armes 2 Mains
> 
> 4. Mode Point → Double-clic main suiveuse → Shift + clic parent
>     
> 5. Commands → Constraints → Points → Choisir parent
>     
> 6. Activer contrainte sur frames désirées
>     
> 
> ## 🎨 Workflow Motion Capture
> 
> ## Phases de Nettoyage MoCap
> 
> 7. **Phase 1** : Import données (FBX) dans Cascadeur
>     
> 8. **Phase 2** : Nettoyage brut (suppression keyframes inutiles)
>     
> 9. **Phase 3** : Emphase (exagération wind-up et frame principale)
>     
> 
> ## Structure Animation (5 parties)
> 
> 10. **Début** : Position initiale
>     
> 11. **Wind-up** : Préparation mouvement
>     
> 12. **Frame principale** : Pose clé
>     
> 13. **Cool-down** : Retour
>     
> 14. **Fin** : Position finale
>     
> 
> ## Optimisations MoCap
> 
> - **Recentrage** : Sélectionner frames → Centrer masse → Orienter forward
>     
> - **Durée** : Raccourcir wind-up (touches -), allonger cool-down (touches +)
>     
> - **Ancrage** : Fulcrum Point pour pieds au sol
>     
> 
> ## 🛠️ Astuces Pratiques
> 
> ## Raccourcis Essentiels
> 
> - **Z / Shift + Ctrl + Z** : Undo/Redo
>     
> - **R** : Lock/Unlock joints
>     
> - **F** : Garder frame physics
>     
> - **Alt + F** : Key interval complet
>     
> - **Ctrl + T** : Étirer timeline
>     
> 
> ## Points d'Attention
> 
> - **Mode Point** obligatoire pour contraintes
>     
> - **Frames prioritaires** : Forcer pose exacte contre IA
>     
> - **Unbaking** : Convertir animation dense en keyframes
>     
> - **Pivot manuel** : Clic droit pour changer point de rotation
>     
> 
> ## 🔗 Intégrations
> 
> ## Export Unreal Engine
> 
> 1. Snap to AutoPhysics
>     
> 2. Export animation
>     
> 3. Replace skeleton vers Unreal 5 Mannequin
>     
> 
> ## Armes IK/FK
> 
> - **Setup** : Import rig arme avec os → Add joints → Quick Rigging
>     
> - **Masses physiques** : Ajuster selon répartition poids réelle
>     
> - **Basculement** : IK (arme libre) / FK (suit main)
>     
> 
> ## 💡 Bonnes Pratiques
> 
> - Toujours **tester en jeu** après export
>     
> - **Sauvegarder poses mains** dans fichier dédié
>     
> - Utiliser **références vidéo** importées pour traçage
>     
> - **Physics Corrector OFF** pour animations spéciales
>     
> - **Combinaison AI + manuel** : Utiliser IA comme guide, peaufiner manuellement
>     

### Pipeline Autophysics

[Physics Pipeline \| Everything You Need to Know about AutoPhysics in Cascadeur - YouTube](https://youtu.be/QPPIxzbH1o8?si=zdqoMZu8uKU-1vsJ)
##### ⚡ Pipeline Rapide

- **1. Créer les poses clés** : Blocage manuel avec les contrôleurs (blocking).
- **2. Interpoler** : Auto ou manuelle (Bezier Clamp), IK/FK selon le mouvement. (tous ces paramètres sont juste au dessus de la timeline)
- **3. Vérifier les points d’appui (fulcrum)** : Pieds/surface => centres de masse bien alignés.

##### 🔧 Application Physique IA

> [!tip]+ Filtres Principaux (Sliders à ajuster)
> - **Main Physics** : Trajectoire générale, équilibre et jumps
> - **Smooth Trajectory** : Fluidité des arcs (squats, envol)
> - **Smooth Rotation** : Lissage des rotations globales
> - **Compensation Motion** : Ajout de balancements (ex : bras ou torse pour stabiliser)
> - **Separation Motion** : Séparation dynamique des parties du corps (plus vivant)
> - **Secondary Motion** : Retard et déphasage des membres (surtout bras)

- **AutoPhysics ON** : Corrige trajectoires, crée courbe balistique naturelle pour les sauts/vols.
    - Centre de masse : suit une courbe physique réaliste (paramétrable).
    - Réglable : Slider pour déviation entre animation originale et physique.
- Marquer les frames prioritaires pour forcer le maintien de poses clés lors de corrections physiques (icone à côté de l'activation de la physique)
- **Snaper/Baker** l’animation physique quand satisfait pour édition ou export 
	- Avant de snap / bake (icone à côté de l'activation de la physique) : Activer le fixing interpolation on change interval (bouton punaise juste au dessus de la timeline)


---
### Inbetweening

Génère automatiquement les animations entre des poses clés (keyframes), en gardant les poses clés intactes.

**IA fulcrum points** : Points d’appui détectés automatiquement, ce qui améliore la stabilité (pieds qui glissent moins).

**Styles multiples** : Possibilité de choisir différents styles de mouvement (marche, course, saut…).

##### Utilisation

- Sélectionner toutes les frames entre A et B.
- Cliquer sur le bouton **Inbetweening**.

- Mode **S** : pour lecture/visualisation rapide.
- Modifier les poses des keyframes si le mouvement n’est pas fluide (ex : transformer une pose statique en étape/milieu de marche).
- Régénérer l’inbetweening à chaque changement de keyframe.

##### AutoPhysics & Réalisme

- Après inbetweening, activer **AutoPhysics** pour corriger les trajectoires (ex : ballistique/jump).
- Réglages complémentaires : ajuster la friction, rebond… dans les paramètres Physics pour un réalisme accru.

- Pour ajuster la vitesse globale sans changer la nature du mouvement, utilisez le mode étirement (stretching)

- Une fois satisfait, « snap » (appliquer) l’animation corrigée par la physique.

> [!tip]+ 💡Conseils pratiques pour l'inbetweening
> - L’inbetweening IA ne tient pas compte de la physique, **toujours appliquer AutoPhysics après génération**.
> - Les résultats dépendent principalement de la qualité des poses clés et du timing.
> - En cas de mouvements cassés ou saccadés, ajouter ou ajuster les keyframes intermédiaires.
> - Utilisez la visualisation de la trajectoire du centre de masse pour vérifier la fluidité et la cohérence physique.

---

Cette fiche te permet d’optimiser la création d’animations fluides avec l’IA d’inbetweening de Cascadeur 2025.2, en utilisant au mieux ses nouveautés.[youtube](https://www.youtube.com/watch?v=6cLiI9vEgdM)

1. [https://www.youtube.com/watch?v=6cLiI9vEgdM](https://www.youtube.com/watch?v=6cLiI9vEgdM)

## Références

Vidéo ultra complète sur tout ce qu'il y a à savoir : 
- [Everything About Cascadeur (FULL-FREE-Course!) - YouTube](https://youtu.be/vPwVGuYEk2o?si=PqAXcuaMT3BfCk80)

Animer 2 persos dans cascadeur : 
- [How to Animate 2 Characters in Cascadeur \| Contact Pair Animation - YouTube](https://youtu.be/gumcvLfNnDM)


> [!example]- Flashcards
> ...




## Liens 




