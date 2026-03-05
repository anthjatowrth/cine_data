# 🎬 Movie Recommender App — IMDb & TMDB Data Pipeline

**Demo live :** [cinedata.streamlit.app](https://cinedata.streamlit.app/)

---

## 🧠 Présentation du projet

Ce projet consiste à construire un système complet de recommandation de films, depuis le traitement de données brutes jusqu'à leur exploitation dans une application interactive.

Il s'agit d'un projet end-to-end Data comprenant :

- ingestion et nettoyage de datasets réels (IMDb & TMDB)
- création d'un dataset enrichi
- feature engineering pour Machine Learning
- développement d'un moteur de recommandation basé sur la similarité
- mise en production dans une application Streamlit

L'objectif est de reproduire, à une échelle réaliste, la chaîne complète d'un produit data.

---

## 🚀 Description de l'application

L'application permet de :

- explorer un catalogue de films
- consulter des fiches détaillées
- obtenir des recommandations personnalisées
- naviguer entre les films similaires

---

## 🎯 Objectifs du projet

Ce projet vise à démontrer :

- la capacité à construire un pipeline data complet
- la maîtrise du feature engineering pour le NLP
- l'implémentation d'un moteur de recommandation basé contenu
- la mise en production d'un modèle ML dans une interface utilisateur

---

## 📊 Fonctionnalités principales : Pipeline Data Engineering

- nettoyage des données IMDb
- filtrage des films pertinents
- enrichissement avec TMDB
- extraction des informations clés (casting, réalisateurs…)
- fusion multi-sources
- production d'un dataset final prêt pour le ML

---

## 🤖 Moteur de recommandation

Le système de recommandation repose sur :

- un modèle Nearest Neighbors
- une similarité cosinus
- des features hybrides combinant :
  - texte (TF-IDF)
  - catégories (MultiLabelBinarizer)
  - variables numériques normalisées

Le moteur permet d'identifier des films similaires selon :

- genre
- casting
- réalisateurs
- popularité
- caractéristiques textuelles

---

## 🖥 Application Streamlit

L'interface propose :

- navigation dans un catalogue complet
- fiches films détaillées
- recommandations dynamiques
- design personnalisé avec CSS

---

## 📁 Structure du projet

```text
imdb-project-streamlit/
│
├── app.py                          # Entrée principale Streamlit
│
├── assets/
│   ├── style.css                   # Styles personnalisés UI
│   └── ...                        # Logos, images, badges
│
├── pages/                          # Pages de l'application
│   ├── Catalogue.py
│   ├── Film_details.py
│   └── Reco_ML.py
│
├── src/
│   ├── config.py
│   ├── pipeline.py                 # Orchestration du pipeline
│   ├── utils.py
│   ├── ui.py
│   ├── genre_translations.py
│   ├── quick_summary_function.py
│   │
│   ├── reco/                       # Moteur ML
│   │   └── engine.py
│   │
│   └── s01 → s10                   # Étapes pipeline data
│
├── data/
│   ├── raw/                        # Données brutes (non incluses)
│   └── interim/                    # Données intermédiaires du pipeline
│
├── requirements.txt
└── README.md
```

---

## ⚙️ Pipeline de traitement des données

Le pipeline comporte plusieurs étapes :

1. Chargement des données IMDb
2. Filtrage des titres pertinents
3. Nettoyage des ratings
4. Sélection des films principaux
5. Extraction des réalisateurs
6. Enrichissement du casting
7. Consolidation des informations
8. Création du dataset IMDb final
9. Nettoyage des données TMDB
10. Fusion des deux sources

Chaque étape produit des artefacts intermédiaires permettant la reproductibilité du processus.

---

## 🤖 Détails techniques du moteur de recommandation

**Features utilisées**

- genres
- pays
- popularité
- année de sortie
- réalisateurs
- texte (casting + description)

**Préparation des données**

- TF-IDF pour les données textuelles
- MultiLabelBinarizer pour les catégories
- StandardScaler pour les variables numériques

**Algorithme utilisé**

```
NearestNeighbors(metric="cosine")
```

Ce choix permet :

- de gérer efficacement les données sparse
- d'obtenir des recommandations pertinentes sur des données textuelles
- d'assurer des performances rapides en production

---

## 🛠 Installation locale

```bash
git clone https://github.com/anthjatowrth/imdb-project-streamlit.git
cd imdb-project-streamlit
```

**Créer l'environnement virtuel**

Sur Windows :
```bash
python -m venv .venv
.venv\Scripts\activate
```

Sur macOS / Linux / Git Bash :
```bash
python -m venv .venv
source .venv/bin/activate
```

**Installer les dépendances**

```bash
pip install -r requirements.txt
```

**Créer les dossiers de données**

```bash
mkdir -p data/raw data/interim data/output
```

---

## 📦 Données

Les datasets ne sont pas inclus dans le repo pour des raisons de taille. **Aucun téléchargement manuel n'est nécessaire** : le pipeline s'en charge automatiquement.

- **IMDb** — les scripts lisent directement en streaming depuis [https://datasets.imdbws.com/](https://datasets.imdbws.com/)
- **TMDB** — le fichier `tmdb_full.csv` est téléchargé automatiquement via `gdown` depuis [Google Drive](https://drive.google.com/file/d/1VB5_gl1fnyBDzcIOXZ5vUSbCY68VZN1v/view?usp=sharing) s'il n'est pas déjà présent dans `data/raw/`

Il suffit de lancer le pipeline (voir ci-dessous), tout le reste est géré automatiquement.

---

## ▶️ Lancer le pipeline de données

```bash
python src/pipeline.py
```

## ▶️ Lancer l'application

```bash
streamlit run app.py
```

---

## 🎓 Contexte du projet

Projet réalisé dans le cadre d'une formation Data Analyst à la Wild Code School.

---

## ✨ Points forts du projet

- pipeline data complet et reproductible
- fusion multi-sources réalistes
- feature engineering avancé
- moteur de recommandation performant
- application interactive déployée
- architecture modulaire professionnelle

---

## 👨‍💻 Auteur

Anthony — Data Analyst
