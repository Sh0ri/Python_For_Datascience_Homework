---
# **First order theorem proving**

#### projet python

##### Violette Lefranc

---

## Jeu de données :



Tout l'enjeu de la recherche basée sur ce jeu de données est de tenter de prouver qu'il est possible de déterminer grâce au machine learning quelle méthode heuristique est la plus appropriée à un problème de logique de premier ordre.​

Dans le cadre de ce sujet, des chercheurs se sont penchés sur 5 méthodes heuristique qu'on nomme H1 à H5 (plus une témoin dont on attribue le nom H0).​

Afin de tester l'efficacité de ces techniques, un grand nombre de données de différents problèmes ont été récupérées de la librairie TPTP (thousands of Problem for Theorem Provers). A chaque problème, on va chercher à déterminer non seulement si un heuristique peut le résoudre rapidement mais également lequelle serait le plus efficace.​



Lors du téléchargement de la base de données, nous nous retrouvons avec 4 fichiers .csv... Ils sont tous organisé de la même manière:

+ 14 colonnes de static features
+ 37 colonnes de dynamic features. 
+ 6 dernières colonnes (5 pour all-data- raw) représentent les fonctions heuristiques.

| nom |description| nbrow | valeur heuristiques |
| ------ | ------ |----- |----- |
| all-data-raw  |Les données d'origines des 6118 jeu de problèmes pour tester l'efficacité des heurstiques|6118 |-100 si prend moins de 100 secondes à résoudre sinon prend le temps de résolution
| test | testing set|3059 | 1 si le meilleur -1 sinon
| train  | training set|1529 |1 si le meilleur -1 sinon
| valisation  | valisation set|1530 |1 si le meilleur -1 sinon

## Objectif :
On va donc chercher à prédire quel heuristique est le plus efficace selon le jeu de données. Cependant, il se trouve que faire des prédictions sur 6 colonnes n'est pas facile. ​

Nous allons donc créer une dernière colonne "results" qui prendra l'indice du meilleur heuristique (si H1 prend 1, "results" prend 1; si H2 prend 2 "results" prend 2, etc...)​

Cette colonne sera donc notre cible, nous chercherons à voir si nous pourrons prédire quel indice en sort.​


```js
def addResult(dt):
    if dt['H1'] == 1:
        return 1
    elif dt['H2'] == 1:
        return 2
    elif dt['H3'] == 1:
        return 3
    elif dt['H4'] == 1:
        return 4
    elif dt['H5'] == 1:
        return 5
    elif dt['H0'] == 1:
        return 0

dt['results']=dt.apply(addResult,axis=1)
dv['results']=dv.apply(addResult,axis=1)
dt.head()
```


Pour le dataset on décide de profiter du travail déjà effectué et donc de prendre le le Train.csv (qu'on appel dt) et Test.csv(du'on appelle dv). Ainsi nous n'aurons pas à faire le split_test et nous rajoutons la colonne results aux deux dataFrame​



```
X_train = dv.drop(['H1','H2','H3','H4','H5','H0','results'], axis = 1)
Y_train = dv.results

X_test=dt.drop(['H1','H2','H3','H4','H5','H0','results'], axis = 1)
Y_test = dt.results
```


