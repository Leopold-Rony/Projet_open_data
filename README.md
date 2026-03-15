# ⚡ Projet Open Data : Le DPE face à la réalité énergétique

## 🎯 Contexte et Objectifs du Projet
Ce projet de Data Science vise à confronter la théorie à la réalité dans le domaine de l'immobilier et de l'énergie. Le Diagnostic de Performance Énergétique (DPE) prédit la consommation théorique d'un logement (classes de A à G). Mais cette théorie se vérifie-t-elle sur les factures réelles des ménages ?

À travers le croisement de bases de données de l'ADEME (DPE) et d'ENEDIS (Consommation réelle), nous explorons la fracture territoriale, la précarité énergétique et les biais comportementaux des habitants d'Île-de-France et de Nouvelle-Aquitaine.

**Trois grands enseignements de notre étude :**
1. **La Précarité Subie :** Les passoires thermiques (F et G) consomment en réalité beaucoup moins que prévu car les habitants coupent le chauffage pour des raisons financières.
2. **L'Effet Rebond :** Les logements très récents (post-2012, classes A et B) ont tendance à surconsommer par rapport à la théorie, par confort.
3. **La Fracture Territoriale :** L'urbanisme (Paris intra-muros vs Grande Couronne) dicte la facture énergétique.

---

## 📂 Structure du Dépôt (Pipeline Data)

Le projet est structuré selon un pipeline de Data Science complet, de l'ingénierie des données brutes jusqu'à la modélisation spatiale.

### DOSSIER notebooks_IDF

### 🛠️ 1. Data Engineering
* **`1_preparation_donnees.ipynb`** : Importation des bases massives (ADEME, ENEDIS), nettoyage textuel complexe (Regex, standardisation des adresses), gestion des valeurs aberrantes et jointures de tables.

### 📊 2. Exploration et Visualisation (EDA)
* **`02_Data_Analysis_et_Viz.ipynb`** : Démonstration du paradoxe de la classe G (Barplots) et analyse de l'impact de la mitoyenneté (Appartements vs Maisons via Boxplots). Mise en évidence de l'effet rebond avec des graphiques superposés (Théorie vs Réalité).

### 🤖 3. Machine Learning (Apprentissage Non Supervisé)
* **`03_1_Modelisation_KMeans.ipynb`** : Segmentation automatique (K-Means) de 50 000 logements. Choix du nombre de clusters via la *Méthode du Coude*.
* **`03_2_Modelisation_CAH.ipynb`** : Classification Ascendante Hiérarchique (CAH) avec critère de Ward sur échantillon. Tracé du Dendrogramme confirmant la typologie en 3 profils distincts.
* **`03_3_Modelisation_ACP.ipynb`** : Analyse en Composantes Principales (ACP). Réduction de dimension, projection des individus, barycentres des classes DPE et tracé du Cercle des Corrélations (Biplot).

### 🗺️ 4. Analyse Spatiale
* **`04_Cartographie_et_Presentation.ipynb`** : Création de cartes choroplèthes d'Île-de-France avec `GeoPandas` (consommation au m² par département, concentration des passoires thermiques).
* **`OpenData_vf.ipynb` (Nouvelle-Aquitaine)** : Notebook compagnon pour l'analyse et la cartographie par points GPS sur la région Nouvelle-Aquitaine.

---

## 🚀 Installation et Utilisation

### Prérequis
Ce projet nécessite Python 3 et les librairies suivantes :
```bash
pip install pandas numpy matplotlib seaborn scikit-learn geopandas scipy rapidfuzz