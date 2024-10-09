# Credit_Risk_Modeling2

Ce projet vise à modéliser le risque de crédit en utilisant des données provenant du Lending Club. Il comprend une refonte complète de l'ancien modèle, avec une approche basée sur la normalisation des variables plutôt que l'utilisation de variables fictives ("dummy variables"). Cette refonte permet une meilleure gestion des données et une meilleure performance des modèles.

Les données utilisées sont disponibles sur Kaggle : [Lending Club Dataset](https://www.kaggle.com/datasets/wordsforthewise/lending-club?resource=download).

## Structure du Projet

Le projet est divisé en plusieurs étapes : prétraitement des données, modélisation du risque de défaut (PD), de la perte en cas de défaut (LGD), et de l'exposition en cas de défaut (EAD), ainsi que le calcul de la perte attendue (EL).

### 1. **Preprocess Database**
   - **Échantillonnage** : Réduction du fichier de base contenant 2 millions de lignes à un échantillon de 500 000 lignes pour accélérer le traitement.
   - **Division temporelle** : Séparation des données en deux périodes, avant et après 2018, afin de surveiller la performance des modèles dans le temps et d'évaluer leur robustesse sur des données futures.

### 2. **Preprocess Data**
   - **Normalisation des variables continues** : Toutes les variables continues sont normalisées dans un intervalle de [0, 1] pour assurer une cohérence dans l'échelle des données et améliorer la convergence des modèles.
   - **Transformation des variables catégorielles** : Les variables catégorielles sont transformées via le Weight of Evidence (WoE), puis normalisées pour mieux capturer l'information sans perdre la hiérarchie des catégories.

### 3. **Train PD Model**
   - **Modélisation de la Probabilité de Défaut (PD)** : Utilisation d'une régression logistique pour prédire la probabilité de défaut d'un emprunteur.
   - **Évaluation des performances** : 
     - **ROC AUC** : Mesure la capacité du modèle à classer correctement les emprunteurs par rapport à leur statut de défaut.
     - **Gini** : Indicateur de séparation entre les bons et les mauvais emprunteurs.
     - **Kolmogorov-Smirnov (KS)** : Mesure la distance maximale entre les distributions des emprunteurs en défaut et non en défaut.
   - **Monitoring des performances** : Utilisation des données postérieures à 2018 pour surveiller et valider les performances du modèle dans le temps.

### 4. **Train LGD Model**
   - **Modélisation de la Perte en Cas de Défaut (LGD)** : Application d'une régression Beta pour prédire la proportion de perte subie en cas de défaut d'un emprunteur.
   - **Évaluation des performances** : 
     - **MAE (Mean Absolute Error)** : Mesure l'erreur moyenne en valeur absolue.
     - **MSE (Mean Squared Error)** : Mesure l'erreur quadratique moyenne pour pénaliser les grandes erreurs.
     - **RMSE (Root Mean Squared Error)** : Racine carrée de la MSE pour ramener l'unité à celle des données.
     - **R² (Coefficient de Détermination)** : Indicateur de la proportion de variance expliquée par le modèle.

### 5. **Train EAD Model**
   - **Modélisation de l'Exposition en Cas de Défaut (EAD)** : Régression linéaire pour prédire le montant restant dû en cas de défaut d'un emprunteur.
   - **Évaluation des performances** : 
     - **MAE, MSE, RMSE, R²** : Utilisation des mêmes métriques que pour le modèle LGD pour évaluer la qualité des prédictions.

### 6. **Calculate EL (Expected Loss)**
   - **Calcul de la Perte Attendue (EL)** : La perte attendue est calculée en combinant les prédictions des trois modèles précédents (PD, LGD, EAD) :
     ```
     EL = PD × LGD × EAD
     ```
   Ce calcul permet d'estimer la perte moyenne que subirait le prêteur pour un portefeuille donné.

## Conclusion

Ce projet met en œuvre une modélisation complète du risque de crédit en utilisant la transformation WoE et les régressions logistique, beta et linéaire. Libre de droit.
