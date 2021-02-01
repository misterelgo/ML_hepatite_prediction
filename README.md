# ML_hepatite_prediction
Objectif : comparer, selon un protocole rigoureux, trois méthodes d’apprentissage automatique sur un jeu de données particulier.

# preprocessing des données:
On a décidé de supprimer la colonne “unnamed” qui représente l’index des lignes de notre dataset, donc ça n'a aucun
impact sur les prédictions. Ensuite pour traiter les données manquantes on a décidé de découper notre dataset par classe et de
remplacer les valeurs manquantes par la moyenne de chaque colonne. Après on a remarqué que la colonne “Sex” et “Category”
était de type catégorique(pas numérique) mais selon nos recherches on à compris que les algorithmes de machine learning et
notamment les algorithmes de régression logistique était plus performant avec des données de types numérique, nous avons donc
décidé de remplacer les valeurs de ces deux colonnes en valeurs numérique.
colonne “Sex” : on a deux catégories: “m” et “f”. On a donc décidé de remplacer les “m” par “1” pour représenter le sex
masculin et les “f” par “2” pour le sex féminin.
colonne “Category” : cette colonne représente nos classes(les prédictions). Étant donné qu’on à décidé de ramener notre
problème sous forme de classification binaire on était obligé de ramener les valeur de cette colonne qui étaient à la base classées
sur cinq catégories en deux catégories(malade ou pas malade). on a donc procédé comme suit:
1 - les “blood donnor” considéré comme les non malades sont représentés par “1”
2 - les autres categories (suspect blood donor, hepatitis, fibrosis, cirrhosis) sont donc considérés comme les malades et
sont représentés par “0”
# Découpage des données
On va découper notre jeu de données en trois parties. Une partie d’entraînement, une partie de validation et une partie de test.
Format: 60:20:20. Selon la répartition de nos données, on a un grand déséquilibre en fonction des catégories. Pour avoir des
résultats probants on va procéder à la stratification de nos données. Le découpage se fera par stratification sur l’attribut
“Category”.
# Choix des hyperparamètres
Réglage des hyperparamètres de chaque modèle à l'aide de GridSearchCV: L'idée principale est de créer une grille
d'hyperparamètres et d'essayer toutes leurs combinaisons. Celà nous permettra d’inspecter les meilleurs paramètres trouvés par
GridSearchCV dans l'attribut best_params_, et le meilleur estimateur dans l'attribut best_estimator_
# Validation des modèles et métriques de comparaison
Les modèles seront validés à partir de la méthode de la validation croisée. Enfin, nous utiliserons la matrice de confusion (à travers
les valeurs de l’exactitude, de la sensibilité...) afin d’apprécier les capacités de prédiction des trois modèles quant à la
reconnaissance d’un malade et non malade.
# Comparaison des algorithmes
Nous comparons nos modèles selon les éléments de performances suivantes :
Précision globale, matrices de confusions et Courbe ROC

# inconvénients des différents modèles:
- KNN : L'algorithme devient beaucoup plus lent à mesure que le nombre d'exemples d'apprentissage augmente.
- SVM : L'algorithme SVM ne convient pas aux grands ensembles de données.
- Régression Logistique : La limite de la régression logistique est qu'elle nécessite des échantillons de grande taille pour pouvoir
prétendre un niveau acceptable de stabilité
