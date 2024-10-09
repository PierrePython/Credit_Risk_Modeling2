# Credit_Risk_Modeling2

Ce projet consiste à modéliser le risque de crédit en utilisant des données du Lending Club.
https://www.kaggle.com/datasets/wordsforthewise/lending-club?resource=download

J'ai fait une refonte de l'ancien modèle en travaillant avec des données normalisées au lieu des "dummys variables".

J'ai changé la construction des différents fichiers.

## preprocess_database

    - Echantillonage du fichier de base (2M de lignes), pour garder 500K lignes.
    - Redivision des données antérieur à 2018 et postérieur à 2018 dans le but de monitorer les données avec ultérieurement.

## preprocess_data

    - Modification des données en normalisant les variables continues
    - Tranformation des variables catégorielles en leur WoE puis en les normalisants.

## train_PD_model

    - Régression logistique
    - Evaluation de la perfomance avec ROC AUC, Gini, Kolmogorov-Smirnov, 
    - Monitoring avec les données postérieur à 2018

## train_LGD_model

    - Régression beta
    - Evaluation de la perfomance avec MAE, MSE, RMSE et R²

## train_EAD_model

    - Régression linéaire
    - Evaluation de la perfomance avec MAE, MSE, RMSE et R²

## calculate_EL
    
    - Calcul de EL
