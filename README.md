# 🏠 Prédiction des Réclamations sur des Bâtiments
## Projet de Fouille de Données – 2025–2026

---

## 📌 Contexte
Ce projet a été réalisé dans le cadre du module **Fouille de Données** à  
**l’Institut International de Technologie de Sfax (IIT)**.

L’objectif est de développer un **modèle de prédiction des réclamations (sinistres)** sur des bâtiments assurés, afin d’aider les compagnies d’assurance à :
- Anticiper les risques,
- Améliorer la tarification,
- Optimiser la gestion des contrats.

---

## 👥 Réalisé par
- **JARBOUI Nour Houda**


🎓 2ème année Génie Informatique  
👨‍🏫 Encadré par : **Dr. Taoufik Ben Abdallah**

---

## 📂 Structure du projet

---

## 📊 Jeu de données
Le jeu de données contient des informations décrivant des bâtiments assurés :
- Variables numériques (superficie, score de risque, année, etc.)
- Variables catégorielles (type de structure, zone géographique, localité…)
- Variable cible binaire : **Claim**  
  - 1 : au moins une réclamation  
  - 0 : aucune réclamation  


---

## 🔍 Méthodologie

### 1️⃣ Exploration des données (EDA)
- Analyse de la structure du jeu de données
- Identification des **colonnes avec valeurs manquantes**
- Détection d’un **déséquilibre des classes (imbalanced data)**
- Visualisation des distributions pour guider le nettoyage

---

### 2️⃣ Prétraitement des données
Les principales étapes de prétraitement sont :

- Suppression des lignes non pertinentes
- Normalisation (KDE + segmentation automatique)
- Standardisation :
  - `coverage_period → coverage_period_scaled`
  - `area_m2 → area_m2_scaled`
- Gestion des valeurs manquantes :
  - Médiane pour les variables numériques
  - Mode ou valeur *unknown* pour les variables catégorielles
- Encodage :
  - Label Encoding (`is_residential`, `has_garden`, `locality`)
  - One-Hot Encoding pour les variables catégorielles
- Découpage de certaines variables :
  - `is_finished_and_fenced → is_finished, is_fenced`

---

### 3️⃣ Gestion du déséquilibre des classes
Le jeu d’entraînement est déséquilibré.  
Une approche d’**échantillonnage hybride (Hybrid Sampling)** a été utilisée :
- Combinaison de sur-échantillonnage et sous-échantillonnage
- Amélioration de la capacité du modèle à prédire la classe minoritaire

Tous les prétraitements appris sur le **jeu d’entraînement** sont appliqués **à l’identique sur le jeu de test**.

---

### 4️⃣ Sélection des descripteurs
- Utilisation d’un **RandomForestClassifier**
- Optimisation via **RandomSearch**
- Extraction des **importances des variables (Feature Importance)**

---

### 5️⃣ Modélisation
Plusieurs techniques d’apprentissage supervisé ont été testées.  
Le modèle final repose sur une **technique ensembliste : le Stacking**, permettant de combiner plusieurs modèles pour améliorer les performances.

---

### 6️⃣ Validation et évaluation
- Comparaison des modèles à l’aide du **F1-score (Train / Test)**
- Analyse :
  - Underfitting
  - Overfitting
- Sélection du modèle offrant le meilleur compromis entre performance et généralisation

---

## 📈 Résultats
- Le **Stacking** présente les meilleures performances globales
- Le prétraitement et la gestion du déséquilibre ont un impact significatif
- Les résultats montrent une bonne capacité de généralisation sur le jeu de test

---

## 🧠 Conclusion et perspectives
Ce projet a permis de mettre en œuvre une chaîne complète de fouille de données :
EDA → Prétraitement → Modélisation → Validation.

### Perspectives :
- Intégration de nouvelles variables externes
- Optimisation avancée des hyperparamètres
- Exploration de modèles plus complexes (Deep Learning)

---

## 🛠️ Technologies utilisées
- Python
- Pandas, NumPy
- Matplotlib / Seaborn
- Scikit-learn
- Imbalanced-learn
- Jupyter Notebook

