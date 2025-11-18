# Modifications apportées au générateur de questions Scratch

**Date :** 18 novembre 2025
**Branche :** `claude/scratch-draw-square-01K7XSqAyGG1eyhhUEnBun3m`

## ⚠️ IMPORTANT : Commits non poussés

**2 commits sont sauvegardés localement** mais n'ont pas pu être poussés sur GitHub à cause d'erreurs réseau (erreur 504).

### Pour pousser les commits plus tard :

```bash
cd /home/user/autres
git push -u origin claude/scratch-draw-square-01K7XSqAyGG1eyhhUEnBun3m
```

### Si le push échoue, utilisez les fichiers patch :

Les fichiers suivants ont été créés :
- `0001-Ajouter-les-vraies-couleurs-Scratch-et-les-variables.patch`
- `0002-Ajouter-un-SVG-explicatif-pour-le-triangle-quilat-ra.patch`

Pour appliquer manuellement :
```bash
git am *.patch
```

---

## 📋 Résumé des modifications

### 1. Carré de côté 121 (fixe)
- **Fichier :** `Automatisme/generateur_questions.html` ligne 2997
- **Changement :** `const cote = 121;` (au lieu de `randInt(50, 150)`)
- **Commit :** `ad6f2e3`

### 2. Bibliothèque scratchblocks supprimée
- **Changement :** Suppression des liens externes vers scratchblocks.github.io
- **Avantage :** Fonctionne maintenant **sans connexion Internet**
- **Commit :** `ee31a64`

### 3. CSS personnalisé pour les blocs Scratch
- **Fichier :** `Automatisme/generateur_questions.html` lignes 592-670
- **Ajouts :**
  - `.scratch-blocks` - Conteneur principal
  - `.scratch-block` - Blocs génériques
  - `.scratch-block-control` - Blocs de contrôle (orange #FFAB19)
  - `.scratch-block-motion` - Blocs de mouvement (bleu #4C97FF)
  - `.scratch-block-pen` - Blocs stylo (vert #0FBD8C)
  - `.scratch-block-data` - Blocs de données (orange foncé #FF8C1A)
  - `.scratch-variable` - Variables en ovale orange
  - `.scratch-input` - Valeurs en rectangle blanc
  - `.scratch-question-mark` - Point d'interrogation en rouge
  - `.scratch-indent` - Indentation des blocs imbriqués

### 4. Fonction generateScratchBlocks réécrite
- **Fichier :** `Automatisme/generateur_questions.html` lignes 802-959
- **Support complet pour :**
  - ✅ Stylo (stylo en position d'écriture)
  - ✅ Contrôle (répéter, si...alors, sinon, end)
  - ✅ Mouvement (avancer, tourner)
  - ✅ Données (mettre, ajouter)
  - ✅ Apparence (dire)
  - ✅ Détection automatique variables vs nombres
  - ✅ Gestion de l'indentation multi-niveaux

### 5. Vraies couleurs Scratch 3.0
- **Commit :** `56810c7`
- **Couleurs officielles :**
  - Variables : `#FF8C1A` (orange foncé)
  - Motion : `#4C97FF` (bleu)
  - Control : `#FFAB19` (orange clair)
  - Pen : `#0FBD8C` (vert cyan)
  - Looks : `#9966FF` (violet)

### 6. Variables en ovale orange
- **Commit :** `56810c7`
- **Style :** `border-radius: 50%` pour créer des ovales
- **Couleur :** `#FF8C1A` (orange foncé de Scratch)
- **Exemples :** `x`, `côté`, `périmètre` → affichés en ovale orange

### 7. SVG explicatif pour le triangle équilatéral
- **Commit :** `0243f38`
- **Fonction :** `generateTriangleExplanationSVG()` lignes 1144-1212
- **Contenu du SVG :**
  - Triangle équilatéral avec angle intérieur 60° (vert)
  - Direction du lutin (flèches oranges)
  - Angle de rotation 120° (rouge)
  - Explication : "Pourquoi 120° et pas 60° ?"
  - Formules : `180° - 60° = 120°` et `360° ÷ 3 = 120°`
- **Intégration :** Réponse de la question triangle ligne 3322

---

## 🎯 Résultat final

### Avant :
- ❌ Nécessitait une connexion Internet
- ❌ Variables affichées comme `[x v]`
- ❌ Couleurs approximatives
- ❌ Blocs `si...alors` non supportés
- ❌ Explication confuse pour le triangle (60° vs 120°)

### Après :
- ✅ Fonctionne **sans Internet**
- ✅ Variables en **ovale orange** comme dans Scratch
- ✅ **Couleurs officielles** Scratch 3.0
- ✅ Support complet de tous les blocs nécessaires
- ✅ **SVG explicatif** montrant la différence 60° vs 120°
- ✅ Indentation correcte des blocs imbriqués
- ✅ Carré de côté **121** (fixe)

---

## 📁 Fichiers modifiés

- `Automatisme/generateur_questions.html` (seul fichier modifié)
  - Lignes CSS : 592-670
  - Fonction `generateScratchBlocks()` : 802-959
  - Fonction `generateTriangleExplanationSVG()` : 1144-1212
  - Question carré : ligne 2997
  - Question triangle : ligne 3322

---

## 🔧 Comment tester

1. Ouvrir `Automatisme/generateur_questions.html` dans un navigateur
2. Sélectionner le thème "Géométrie avec Scratch"
3. Générer des questions
4. Vérifier :
   - Les blocs Scratch s'affichent avec les bonnes couleurs
   - Les variables sont en ovale orange
   - Le carré utilise un côté de 121
   - La question du triangle affiche le SVG explicatif

---

## 📞 Contact

Si vous avez des questions ou besoin d'aide pour pousser les commits, n'hésitez pas !

**Commits à pousser :**
- `56810c7` - Ajouter les vraies couleurs Scratch et les variables en ovale orange
- `0243f38` - Ajouter un SVG explicatif pour le triangle équilatéral
