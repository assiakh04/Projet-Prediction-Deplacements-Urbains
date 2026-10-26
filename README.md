# Prédiction de la durée des déplacements urbains avec PySpark

## Présentation du projet

Ce projet a pour objectif d’analyser les comportements de mobilité urbaine et de construire un modèle de Machine Learning capable de prédire la durée d’un déplacement à partir d’informations disponibles avant ou au début du trajet.

La problématique étudiée est la suivante :

**Peut-on prédire la durée d’un déplacement urbain à partir des informations connues avant ou au début du trajet ?**

L’objectif est de fournir une estimation du temps de déplacement en fonction notamment de l’origine, de la destination, de l’heure de départ, du motif du déplacement et du moyen de transport.

## Technologies utilisées

- Python
- PySpark
- Spark MLlib
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

## Étapes du projet

Le projet suit les principales étapes suivantes :

1. Chargement et compréhension des données
2. Analyse de la qualité des données
3. Traitement des valeurs manquantes et des valeurs extrêmes
4. Nettoyage des données avec PySpark
5. Feature Engineering
6. Analyse exploratoire des déplacements
7. Préparation des données pour Spark MLlib
8. Entraînement de plusieurs modèles de régression
9. Comparaison et évaluation des modèles
10. Analyse des erreurs de prédiction
11. Analyse des principaux axes de mobilité

## Modèles étudiés

Trois modèles de régression ont été comparés :

- Régression linéaire
- Random Forest Regressor
- Gradient-Boosted Trees Regressor (GBT)

Les performances sont évaluées avec :

- RMSE
- MAE
- R²

## Résultats

Le modèle **Gradient-Boosted Trees (GBT)** obtient les meilleures performances.

Sur le jeu de test :

- **RMSE : 14,858 minutes**
- **MAE : 8,641 minutes**
- **R² : 0,488**

Le modèle présente donc une erreur absolue moyenne d’environ **8,6 minutes**.

Pour 50 % des déplacements, l’erreur est inférieure ou égale à environ **5 minutes**, et pour 90 % des déplacements, elle reste inférieure à environ **19,5 minutes**.

## Analyse mobilité

Une analyse complémentaire des liaisons origine–destination a été réalisée afin d’identifier les axes suffisamment fréquentés présentant les durées de déplacement les plus élevées.

Par exemple, la liaison **P09 → P08** présente une durée moyenne d’environ **31,3 minutes** sur 73 déplacements observés.

Cette analyse permet de transformer les résultats du modèle en informations potentiellement utiles pour un opérateur de transport ou un décideur en mobilité.

## Utilisation du modèle

Le modèle final peut estimer la durée d’un déplacement à partir de variables telles que :

- origine ;
- destination ;
- motif du déplacement ;
- moyen de transport ;
- jour ;
- sexe ;
- âge ;
- heure de départ.

## Fichier principal

Le notebook contenant l’ensemble du projet est :

`Projet_Prédiction_durée_Deplacements_urbains_.ipynb`

## Remarque sur les données

Le fichier source est au format Excel. Apache Spark ne lisant pas directement les fichiers `.xlsx`, les données sont initialement chargées avec Pandas puis immédiatement converties en DataFrame Spark.

Toutes les principales étapes de nettoyage, transformation, analyse et Machine Learning sont ensuite réalisées avec **PySpark**.

## Perspectives d’amélioration

Plusieurs améliorations pourraient être envisagées :

- intégrer la distance réelle entre l’origine et la destination ;
- ajouter des coordonnées géographiques ;
- tester davantage d’hyperparamètres ;
- utiliser une validation croisée ;
- développer une interface permettant à un utilisateur de saisir les informations de son trajet et d’obtenir directement une estimation de sa durée.
