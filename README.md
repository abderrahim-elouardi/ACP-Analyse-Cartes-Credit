# ACP - Analyse des Cartes de Crédit

## Description du Projet

Ce projet réalise une **Analyse en Composantes Principales (ACP)** complète sur des données de cartes de crédit afin de segmenter les clients en profils comportementaux distincts. L'objectif est d'identifier des groupes de clients ayant des comportements d'utilisation similaires pour faciliter des stratégies marketing ciblées et une meilleure compréhension du portefeuille client.

### Objectifs

- Réduire la dimensionnalité des données de cartes de crédit
- Identifier les composantes principales expliquant la variance du comportement client
- Segmenter les clients en clusters homogènes
- Interpréter et caractériser chaque profil client

---

## Structure du Projet

```
ACP-Analyse-Cartes-Credit/
│
├── data/
│   ├── raw/                      # Données brutes originales
│   │   └── CC GENERAL (1).csv
│   └── processed/                # Données traitées à chaque étape
│       ├── credit_card_clean.csv
│       ├── credit_card_clean_standardised.csv
│       ├── matrice_corr.csv
│       ├── data_after_ACP.csv
│       ├── clustered_data.csv
│       └── data_pour_Interprétation_des_profils_obtenus.csv
│
├── R/                            # Scripts d'analyse (ordre séquentiel)
│   ├── 01_analyse_exploratoire/
│   ├── 02_pretraitement/
│   ├── 03_centrage_reduction/
│   ├── 04_correlation/
│   ├── 05_test_adequation_acp/
│   ├── 06_acp_calcul/
│   ├── 07_choix_composantes/
│   ├── 08_segmentation_clustering/
│   └── 09_interpretation_profils/
│
├── docs/                         # Documentation HTML générée
│   └── index.html
│
└── README.md
```

---

## Workflow d'Analyse

### Analyse Exploratoire
**Script:** [`R/01_analyse_exploratoire/analyse_exploratoire.Rmd`](R/01_analyse_exploratoire/analyse_exploratoire.Rmd)

- Chargement des données nettoyées
- Statistiques descriptives (moyenne, médiane, mode, écart-type, variance)
- Analyse de l'asymétrie (skewness)
- Visualisations : histogrammes, boxplots, diagrammes en barres
- Détection des valeurs aberrantes

### Prétraitement des Données
**Script:** [`R/02_pretraitement/01_pretraitement.Rmd`](R/02_pretraitement/01_pretraitement.Rmd)

- Suppression de la colonne identifiant (CUST_ID)
- Vérification des types de variables
- Détection et traitement des valeurs manquantes
- Gestion des doublons
- Traitement des outliers avec la méthode IQR (Interquartile Range)

### Centrage et Réduction
**Script:** [`R/03_centrage_reduction/04_centrage_reduction.Rmd`](R/03_centrage_reduction/04_centrage_reduction.Rmd)

- **Centrage** : mise à l'échelle des données (moyenne = 0)
- **Réduction** : standardisation des variables (écart-type = 1)
- Génération du fichier `credit_card_clean_standardised.csv`

### Analyse de Corrélation
**Script:** [`R/04_correlation/05_correlation.Rmd`](R/04_correlation/05_correlation.Rmd)

- Calcul de la matrice de corrélation
- Visualisation avec heatmap colorée
- Identification des variables fortement corrélées
- Export de la matrice pour analyses ultérieures

### Tests d'Adéquation de l'ACP
**Script:** [`R/05_test_adequation_acp/test_adequation_acp.Rmd`](R/05_test_adequation_acp/test_adequation_acp.Rmd)

**Test KMO (Kaiser-Meyer-Olkin)**
- Mesure la qualité des corrélations entre variables
- Interprétation : KMO > 0.6 → données adaptées à l'ACP

**Test de Bartlett**
- Vérifie l'hypothèse de corrélation entre variables
- p-value < 0.05 → corrélations significatives

### Calcul de l'ACP
**Script:** [`R/06_acp_calcul/06_acp_calcul.Rmd`](R/06_acp_calcul/06_acp_calcul.Rmd)

---

## Technologies et Packages R Utilisés

### Packages Principaux

```r
# Manipulation de données
library(dplyr)
library(tidyr)

# Visualisation
library(ggplot2)
library(corrplot)
library(ggcorrplot)

# ACP et analyse multivariée
library(FactoMineR)
library(factoextra)
library(psych)

# Clustering
library(factoextra)  # Pour fviz_nbclust, fviz_cluster

# Statistiques
library(e1071)  # Pour skewness

# Tableaux et rapports
library(kableExtra)
library(magrittr)
```

---

## Installation et Utilisation

### Prérequis

- R version ≥ 4.0.0
- RStudio (recommandé)

### Installation des Packages

```r
# Installation des packages nécessaires
install.packages(c(
  "ggplot2", "dplyr", "tidyr", "reshape2",
  "FactoMineR", "factoextra", "psych",
  "corrplot", "ggcorrplot",
  "e1071", "kableExtra", "magrittr", "here"
))
```

### Exécution de l'Analyse

1. **Cloner le projet**
   ```bash
   git clone https://github.com/votre-repo/ACP-Analyse-Cartes-Credit.git
   cd ACP-Analyse-Cartes-Credit
   ```

2. **Ouvrir le projet dans RStudio**
   - Double-cliquer sur `ACP-Analyse-Cartes-Credit.Rproj`

3. **Exécuter les scripts dans l'ordre**
   - Commencer par `01_analyse_exploratoire`
   - Suivre la numérotation jusqu'à `09_interpretation_profils`

4. **Consulter les résultats**
   - Les fichiers HTML générés se trouvent dans chaque dossier d'analyse
   - Les données traitées sont dans `data/processed/`

---

## Résultats Attendus

### Fichiers de Sortie

| Fichier | Description |
|---------|-------------|
| `credit_card_clean.csv` | Données nettoyées (sans outliers ni NA) |
| `credit_card_clean_standardised.csv` | Données standardisées (centrées-réduites) |
| `matrice_corr.csv` | Matrice de corrélation entre variables |
| `data_after_ACP.csv` | Données projetées sur les composantes principales |
| `clustered_data.csv` | Données avec labels de clusters |
| `data_pour_Interprétation_des_profils_obtenus.csv` | Moyennes par cluster |

### Visualisations Clés

- Histogrammes et boxplots des variables
- Heatmap de corrélation
- Cercle des corrélations (contribution des variables)
- Graphique des valeurs propres (scree plot)
- Diagramme du coude pour le clustering
- Visualisation des clusters dans l'espace ACP
- Comparaison des profils par groupe

---

## Méthodologie

### Justification de l'ACP

L'ACP est choisie pour :
- **Réduire la dimensionnalité** : passer de 15+ variables à 2-3 composantes principales
- **Éliminer la multicolinéarité** : créer des axes indépendants
- **Faciliter l'interprétation** : visualisation en 2D/3D
- **Améliorer le clustering** : travailler sur des dimensions décorrélées

### Pipeline d'Analyse

```
Données Brutes
    ↓
Nettoyage (NA, outliers, doublons)
    ↓
Standardisation (Z-score)
    ↓
Tests d'adéquation (KMO, Bartlett)
    ↓
ACP (réduction de dimension)
    ↓
Sélection du nombre de composantes
    ↓
K-means Clustering
    ↓
Interprétation des profils
```

---

## Contribution

Les contributions sont les bienvenues ! 

Pour contribuer à ce projet, veuillez consulter le guide complet : **[CONTRIBUTING.md](CONTRIBUTING.md)**

Contributions rapides :
1. Forkez le projet
2. Créez une branche (`git checkout -b feature/amelioration`)
3. Committez vos changements (`git commit -m 'feat: ajout fonctionnalité'`)
4. Poussez vers la branche (`git push origin feature/amelioration`)
5. Ouvrez une Pull Request

---
---

## Auteurs

- **EL OUARDI Abderrahim & AOUAD Abdelkarim **

---

**Dernière mise à jour :** Février 2026
