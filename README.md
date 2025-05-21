# 🔧 Projet : Analyse et Prédiction de la Dégradation d’un Roulement (Bearing) à partir de Séries Temporelles

Ce projet vise à construire un système d’analyse prédictive permettant de suivre l’évolution de l’état de santé d’un roulement mécanique, d’estimer sa Remaining Useful Life (RUL), et de prévenir les pannes en utilisant des techniques d’analyse statistique, de réduction de dimension et de deep learning.

---

## 🧠 Objectifs du Projet

L’objectif principal de ce projet est de développer une approche combinée pour :

- Explorer les séries temporelles extraites de capteurs de vibration ou température.
- Identifier les signes précurseurs de défaillance d’un roulement.
- Appliquer des techniques statistiques (PCA, ARIMA).
- Implémenter et comparer plusieurs architectures de réseaux de neurones (MLP, RNN, LSTM, GRU).
- Prédire la durée de vie restante (RUL) du roulement.

---

## 🗂️ Contenu du projet

| Fichier | Description |
|--------|-------------|
| `notebook.ipynb` | Notebook principal contenant l’analyse exploratoire, les modèles et la visualisation |
| `README.md` | Ce fichier |
| `data/` | Dossier attendu contenant les fichiers CSV de séries temporelles |
| `models/` | (optionnel) Sauvegardes des modèles entraînés |
| `plots/` | (optionnel) Graphiques générés |

---

## 🔧 Technologies & Bibliothèques utilisées

- **Python 3.8+**
- **Bibliothèques principales :**
  - `numpy`, `pandas` – Manipulation de données
  - `matplotlib`, `seaborn` – Visualisation
  - `scikit-learn` – Prétraitement, PCA, métriques
  - `statsmodels` – Modélisation ARIMA, tests de stationnarité
  - `tensorflow`, `keras` – Deep learning

---

## 🔬 Méthodologie

### 1. Chargement et exploration des données
- Importation des fichiers CSV contenant les données de capteurs.
- Visualisation des tendances, moyennes mobiles et densités.
- Vérification des valeurs manquantes, lissage et normalisation.

### 2. Analyse statistique
- **Tests de stationnarité** : ADF (Augmented Dickey-Fuller) et KPSS.
- **Analyse de corrélation** : Heatmaps, ACF/PACF.
- **Réduction de dimension** : PCA (Principal Component Analysis).
- Visualisation des composantes principales.

### 3. Modélisation ARIMA
- Identification des paramètres (p, d, q) via ACF/PACF.
- Entraînement et validation du modèle ARIMA.
- Prédiction de la série future.

### 4. Réseaux de neurones pour la prédiction
- **Préparation des données** : Fenêtrage, reshaping.
- **MLP (Multi-Layer Perceptron)** : Réseau dense basique.
- **RNN (Recurrent Neural Network)** : Pour la dépendance temporelle.
- **LSTM (Long Short-Term Memory)** : Pour mieux gérer la mémoire longue.
- **GRU (Gated Recurrent Unit)** : Alternative plus rapide à LSTM.
- Compilation des modèles, entraînement avec `early stopping`, et visualisation des courbes de perte.

### 5. Évaluation des performances
- **Métriques utilisées** :
  - MAE (Mean Absolute Error)
  - RMSE (Root Mean Square Error)
  - MAPE (Mean Absolute Percentage Error)
- Visualisation :
  - Comparaison des prédictions vs vraies valeurs
  - Analyse des résidus
  - Courbes d’apprentissage

### 6. Estimation de la RUL (Remaining Useful Life)
- Définition de seuil de dégradation
- Prédiction de la durée de vie restante pour chaque séquence temporelle
- Visualisation de la RUL réelle et prédite

---

## 🧪 Exemple de visualisations générées

- Graphiques des signaux bruts (température, vibration, etc.)
- PCA 2D et 3D des séries temporelles
- Prédiction ARIMA vs réalité
- Courbes de prédiction LSTM et GRU
- Évolution de la RUL estimée

---

## 💡 Résultats & Interprétation

| Modèle | MAE | RMSE | MAPE |
|--------|-----|------|------|
| ARIMA  | 3.42 | 4.05 | 8.2% |
| MLP    | 2.76 | 3.21 | 6.4% |
| RNN    | 2.61 | 3.10 | 6.1% |
| LSTM   | 2.31 | 2.89 | 5.7% |
| GRU    | **2.19** | **2.74** | **5.4%** |

Le modèle GRU donne les meilleures performances dans notre contexte, avec une meilleure gestion de la séquence temporelle.

---

## 🔄 Flux de travail complet

```mermaid
graph TD;
  A[Chargement des données] --> B[Analyse exploratoire]
  B --> C[Test de stationnarité]
  C --> D[PCA]
  D --> E[Modélisation ARIMA]
  D --> F[Préparation deep learning]
  F --> G{Choix du modèle}
  G --> G1[MLP]
  G --> G2[RNN]
  G --> G3[LSTM]
  G --> G4[GRU]
  G1 --> H[Évaluation]
  G2 --> H
  G3 --> H
  G4 --> H
  E --> H
  H --> I[Prédiction RUL]
