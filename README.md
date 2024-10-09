# Credit_Risk_Modeling2

Ce projet consiste à modéliser le risque de crédit en utilisant des données du Lending Club.
https://www.kaggle.com/datasets/wordsforthewise/lending-club?resource=download

J'ai fait une refonte de l'ancien modèle en travaillant avec des données normalisées au lieu des "dummys variables".

J'ai changé la construction des différents fichiers.

## preprocess_database

Ce fichier a pour but de construire le traité la base de données sur lequel le modèle à été entrainé. Il était de 2 millions de lignes, j'ai décidé de garder seulement 500 milles lignes. Nous l'avons ensuite rediviser avec les données antérieur à 2018 et postérieur à 2018 dans le but de monitorer les données.

## preprocess_data

Nous avons modifié les données en normalisant les variables continues directement et en transformant les variables catégorielles en leur WoE puis en les normalisants.

## train_PD_model
## train_LGD_model
## train_EAD_model
## calculate_EL
