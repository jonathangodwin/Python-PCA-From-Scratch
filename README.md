# Analyse en Composantes Principales (ACP) Normée "From Scratch"

Ce projet est une implémentation pédagogique d'une Analyse en Composantes Principales (ACP) normée, entièrement réalisée "from scratch" en Python dans un [Jupyter Notebook](acp_from_scratch.ipynb).

[cite_start]L'objectif principal est de décomposer et de comprendre chaque étape mathématique derrière l'ACP[cite: 1], depuis la préparation des données jusqu'à l'interprétation des résultats.

## 🎯 Objectif du Notebook

* **Comprendre** les fondements théoriques de l'ACP normée.
* **Implémenter** l'algorithme étape par étape sans utiliser de bibliothèques de haut niveau comme `scikit-learn`.
* **Appliquer** cette implémentation à un jeu de données réelles (`Temperatures.csv`).
* **Interpréter** les résultats : éboulis des valeurs propres, projection des individus et analyse des contributions.

## 📊 Jeu de Données

Le jeu de données utilisé est `Temperatures.csv`.
* **Individus** : 35 villes européennes.
* **Variables** : 12 températures moyennes mensuelles (de Janvier à Décembre).

L'objectif est de réduire la dimensionnalité de ces 12 variables tout en conservant un maximum d'information (plus de 80%).

## 🛠️ Dépendances

Ce notebook utilise les bibliothèques Python suivantes pour la manipulation de données et la visualisation :
* `numpy`
* `pandas`
* `matplotlib.pyplot`
* `scipy.stats`



## 🔬 Méthodologie "From Scratch"

Le notebook suit les étapes fondamentales de l'ACP normée :

1.  **Chargement et Exploration :** Lecture du fichier `Temperatures.csv` et analyse descriptive initiale des variables.
2.  **Standardisation (Centrage-Réduction) :** Création d'une fonction `scale_matrix` pour centrer et réduire les données. C'est une étape cruciale pour l'ACP *normée*, car les variables (mois) ont des variances différentes.
3.  **Calcul de la Matrice de Corrélation :** Implémentation d'une fonction `correlation_matrix` qui calcule la matrice de corrélation via la formule $\frac{1}{n-1} X^T X$ sur les données standardisées.
4.  **Décomposition (Valeurs et Vecteurs Propres) :** Utilisation de `np.linalg.eig` pour extraire les valeurs propres (l'inertie) et les vecteurs propres (les axes factoriels) de la matrice de corrélation.
5.  **Choix des Axes (Séboulis) :** Analyse de la contribution de chaque axe à l'inertie totale. Le premier axe explique à lui seul plus de 86% de la variance, mais nous gardons les deux premiers pour une meilleure visualisation.
6.  **Projection des Individus :** Calcul des coordonnées des 35 villes dans le nouvel espace factoriel (les composantes principales) en projetant les données standardisées sur les vecteurs propres.
7.  **Analyse des Individus et Variables :**
    * Visualisation des individus (villes) sur les premiers plans factoriels.
    * Calcul de la **contribution** des individus aux axes et de leur **qualité de représentation** (cos²).
    * Calcul des coordonnées des variables (mois) pour l'interprétation des axes (cercle des corrélations).

## 🚀 Comment l'utiliser ?

1.  Assurez-vous d'avoir Jupyter Notebook ou Jupyter Lab installé.
2.  Installez les dépendances requises :
    ```bash
    pip install numpy pandas matplotlib scipy
    ```
3.  Placez le fichier `Temperatures.csv` dans le même répertoire que le notebook.
4.  Lancez le notebook `acp_from_scratch.ipynb` et exécutez les cellules.
