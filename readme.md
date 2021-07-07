# Evaluation: workers

Le rendu de l'exercice se fera via git. Pensez bien à commit à chaque fin d'exercice.
Vous pouvez utiliser tous les outils que vous voulez pendant l'évalutions.

Ce fera surtout sur l'utilisation de docker et docker-compose.

## Présentation

L'objectif du code fourni est de simuler un pattern <a href="https://en.wikipedia.org/wiki/Master/slave_(technology)">master/slave</a>.

On a donc 2 serveurs :

- le planner qui gère les tâches à exécuter
- le worker qui exécute les tâches

### Les tâches

Pour éviter de complexifier le code on va seulement faire des multiplications et des additions, le worker prend artificiellement du temps pour simuler un temps de travail.
Les workers ne peuvent pas effectuer plusieurs tâches à la fois, ils renvoient une erreur 403 si on leur donne une nouvelle tâche alors que leur tâche en cours n'est pas fini.

### Les variables d'environment

Pour configurer plus facilement les serveurs il est possible d'utiliser les variables d'environment. (voir directement dans les readme des deux projets)

## Exercices

### Exercice 1: Dockeriser les Serveurs

Première étape lancer une exécution de 4 tâches avec un planner et un worker dans des container docker.

On commit!

### Exercice 2: Plusieurs workers

On veut pouvoir lancer plusieurs workers pour un seul planner pour pralléliser et accélérer l'exécution.
Pour ça il vous faudra modifier le code du planner (la ligne 12) :

```js
let workers = ['http://localhost:8080']
```

Pour qu'il dispatche les tâches à chaque workers.

On commit!

### Exercice 3: Spécialisation des workers

Par défaut les workers peuvent exécuter toutes tâches. On peut cependant imaginer que certains workers sont spécialisé dans une seule tâche.
Pour ça voir les variables d'environment du worker.

- lancez des workers spécialisés et observez le comportement du planner.
- corrigez les erreurs en modifiant le code du planner.

On commit!

### Exercice 4: Nombre de worker dynamique

On repasse avec des workers généraliste.
On veut maintenant pouvoir ajouter un nombre dynamique de worker pendant l'exécution du planner.

Les nouveaux workers fraichement lancés doivent s'enregistrer auprés du planner pour pouvoir reçevoir des tâches.

Trouvez un moyen de lancer un planner et une dizaine de workers pour exécuter rapidement une cinquantaine de tâches en une seule commande.

On commit!

### Exercice 5: On mélange tout

En réutilisant le code fais ci-dessus :
Créez une configuration qui exécute une centaine de tâches dispatchées parmi :

- 10 workers généralistes
- 10 workers spécialisés en multiplications
- 10 workers spécialisés en additions

On commit!

Pensez à m'envoyer un lien vers votre git sur slack ou par mail: arthur.escriou@gmail.com
