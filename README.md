# Exercice 1 — Analyse Exploratoire des Données (EDA) sur le Dataset Ames Housing

## Description du projet

Ce projet est un exercice pratique d'**Analyse Exploratoire des Données (EDA)** appliqué au dataset **Ames Housing**. L'objectif est de maîtriser les fondamentaux de l'EDA, de la visualisation et du feature engineering sur un jeu de données immobilier réel.

---

## Le Dataset : Ames Housing

Le fichier `AmesHousing.csv` contient des données sur la vente de maisons individuelles à **Ames, Iowa (USA)** entre 2006 et 2010.

| Caractéristique | Détail |
|---|---|
| **Nombre d'observations** | ~2930 maisons |
| **Nombre de variables** | 82 colonnes |
| **Variable cible** | `SalePrice` (prix de vente en dollars) |
| **Types de variables** | Quantitatives continues, discrètes, qualitatives nominales et ordinales |

---

## Objectifs d'apprentissage

À la fin de cet exercice, vous serez capable de :

1. **Comprendre la structure des données** — Explorer les dimensions, types de colonnes et premières lignes
2. **Évaluer la qualité des données** — Identifier les valeurs manquantes, doublons, types inappropriés
3. **Calculer des statistiques descriptives** — Maîtriser les indicateurs classiques (moyenne, écart-type) ET robustes (médiane, MAD, IQR)
4. **Visualiser les distributions** — Histogrammes, boxplots, diagrammes en barres avec annotations
5. **Détecter les valeurs aberrantes** — Comparer la méthode IQR et le z-score modifié
6. **Formuler des hypothèses métier** — Transformer des observations en hypothèses testables

---

## Variables ciblées

L'exercice se concentre sur **5 variables clés** :

| Variable | Description | Type |
|---|---|---|
| `Gr Liv Area` | Surface habitable (pieds carrés) | Quantitative continue |
| `SalePrice` | Prix de vente (dollars) | Quantitative continue |
| `Lot Area` | Surface du terrain (pieds carrés) | Quantitative continue |
| `Year Built` | Année de construction | Quantitative discrète |
| `Overall Qual` | Note globale de qualité (1 à 10) | Ordinale |

---

## Structure de l'exercice

Le notebook est organisé en **6 sections** progressives :

### Section 1 — Imports et chargement
- Importer les bibliothèques nécessaires (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`)
- Charger le fichier CSV dans un DataFrame
- Vérifier le bon chargement avec `head()`

### Section 2 — Aperçu général et qualité des données
- **2.1 Structure** : dimensions, types, `info()`, `describe()`
- **2.2 Valeurs manquantes** : comptage, pourcentage, colonnes les plus impactées
- **2.3 Doublons** : vérification des lignes dupliquées
- **2.4 Sélection** : création d'un sous-ensemble avec les 5 variables ciblées

### Section 3 — Statistiques descriptives univariées
- **3.1 Statistiques classiques** : moyenne, écart-type, min, max
- **3.2 Statistiques robustes** : médiane, Q1, Q3, IQR, MAD (calculé manuellement)
- **3.3 Forme des distributions** : skewness (asymétrie) et kurtosis (aplatissement)
- **3.4 Tableau récapitulatif** : synthèse dans un DataFrame unique

### Section 4 — Visualisations
- **4.1 Variables continues** : histogramme + boxplot côte à côte avec lignes moyenne/médiane
- **4.2 Variables discrètes** : diagrammes en barres
- **4.3 Analyse comparative** : interprétation des graphiques vs statistiques calculées

### Section 5 — Détection d'outliers
- **5.1 Méthode IQR** : bornes [Q1 - 1.5×IQR, Q3 + 1.5×IQR]
- **5.2 Z-score modifié** : formule $Z_{\text{modifié}} = 0.6745 \times \frac{x - \text{médiane}}{\text{MAD}}$, seuil > 3.5
- **5.3 Comparaison** : tableau et visualisation colorée par statut outlier

### Section 6 — Hypothèses métier
- Formuler 3 hypothèses testables au format structuré (énoncé, variables, méthode de vérification, justification)

---

## Concepts clés du cours

### Statistiques classiques vs robustes

| Mesure | Classique | Robuste |
|---|---|---|
| Centralité | Moyenne | Médiane |
| Dispersion | Écart-type | MAD, IQR |
| Détection d'outliers | Z-score | Z-score modifié |

Les statistiques **robustes** résistent aux valeurs extrêmes, contrairement aux classiques qui sont sensibles aux outliers.

### Asymétrie (Skewness)
- **Positive** (> 0) : queue étalée à droite, moyenne > médiane
- **Négative** (< 0) : queue étalée à gauche, moyenne < médiane
- **Nulle** (≈ 0) : distribution symétrique

### Aplatissement (Kurtosis)
- **Leptokurtique** (> 0) : queues épaisses, plus de valeurs extrêmes
- **Mésokurtique** (≈ 0) : comparable à la loi normale
- **Platykurtique** (< 0) : queues fines, moins de valeurs extrêmes

---

## Prérequis techniques

### Bibliothèques Python nécessaires

```bash
pip install pandas numpy matplotlib seaborn scipy
```

### Fichiers du projet

```
eda/
├── README.md                          ← Ce fichier
├── AmesHousing.csv                    ← Le dataset
├── EDA_AmesHousing.ipynb              ← Le notebook à compléter
└── E1 - Analyse Exploratoire...ipynb  ← L'énoncé original (référence)
```

---

## Critères d'évaluation

| Critère | Détail |
|---|---|
| **Exécution** | Le notebook s'exécute de bout en bout sans erreur (`Restart & Run All`) |
| **Structure** | Chaque section est clairement délimitée par un titre Markdown |
| **Visualisations** | Chaque graphique a un titre, des labels d'axes et des légendes |
| **Interprétations** | Chaque bloc de code est suivi d'une interprétation en Markdown |
| **Hypothèses** | 3 hypothèses testables présentées dans un tableau structuré |
| **Tableau récapitulatif** | La section 3.4 contient un DataFrame complet de toutes les statistiques |

---

## Conseils pratiques

- **Lisez l'énoncé de chaque section** avant de coder
- **Interprétez systématiquement** chaque résultat dans une cellule Markdown
- **Comparez toujours** statistiques classiques et robustes pour comprendre l'impact des outliers
- **Annotez vos graphiques** : un graphique sans titre ni labels n'est pas exploitable
- Utilisez `np.percentile()` pour les quartiles et `np.median(np.abs(x - np.median(x)))` pour le MAD
- Le facteur 0.6745 dans le z-score modifié correspond à `scipy.stats.norm.ppf(0.75)`
