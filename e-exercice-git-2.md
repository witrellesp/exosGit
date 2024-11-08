# Exercice : Fusionner deux branches Git et gérer les conflits de fusion

**Objectif :**
- Apprendre à fusionner deux branches et à résoudre des conflits de fusion.
- Comprendre les implications des stratégies de résolution de conflits ours et theirs.
- Réfléchir aux situations où la résolution manuelle des conflits est préférable.

**Instructions :**
Veuillez executer les actions git demandées (elle doivent être exécutées dans l'ordre craniologique).

Pour chaque action demandée, veuillez mentionner dans ce fichier la ou les commandes effectuées, sous cette forme:

```sh
... ma ou mes commandes ici ...
```

**Créez le contexte suivant :**

Créez un dossier de projet Git et initialisez-le :
```bash
mkdir exercice_git_merge
cd exercice_git_merge
```

Et executer les commandes suivantes :

> Copier toutes les lignes ci-dessous et collez-les dans votre terminal git-bash, puis executer - enter.

```bash
git init
echo "Ligne d'origine dans la branche main" > exemple.txt
git add exemple.txt
git commit -m "Initial commit on main branch"
git checkout -b feature/a
echo "Modification spécifique à la branche feature/a" >> exemple.txt
git add exemple.txt
git commit -m "Modification dans feature/a"
git checkout main
git checkout -b feature/b
echo "Modification spécifique à la branche feature/b" >> exemple.txt
git add exemple.txt
git commit -m "Modification dans feature/b"
```

```sh

```
**Fusion des branches et gestion des conflits :**

1. Retournez sur la branche `main` et essayez de fusionner `feature/a`. Cette étape devrait se faire sans conflits.
```sh
git merge feature/a
```

2. Maintenant, essayez de fusionner `feature/b` dans main.
```sh
$ git merge feature/b
Auto-merging exemple.txt
CONFLICT (content): Merge conflict in exemple.txt
Automatic merge failed; fix conflicts and then commit the result.
```

> Une erreur dans la console est apparue. Que signifie-t-elle ? 
This option forces conflicting hunks to be auto-resolved cleanly by favoring our version. Changes from the other tree that do not conflict with our side are reflected in the merge result. For a binary file, the entire contents are taken from our side.


**Gestion des conflits avec les stratégies **ours** et **theirs** :


3. Résolvez le conflit en utilisant la stratégie `ours`.

```sh
git merge -s ours feature/b

git checkout --ours exemple.txt
```

> Que fait la stratégie `ours`?
Va priorisé les changements de la branche  où on est.



4. Résolvez le conflit avec la stratégie `theirs`, pour ce faire vous devez revenir l’état initial, puis fusionnez `feature/b` avec la stratégie `theirs`.

> Que fait la stratégie `theirs`?

**Résolution manuelle des conflits :**

5. Pour résoudre le conflit manuellement, recommencez la fusion sans option de stratégie et éditez le fichier `exemple.txt` pour combiner les modifications souhaitées.

> Quand cela peut-il être pertinant de résoudre un conflit manuellement ?

**Questions de réflexion :**

6. Lors de la fusion avec la stratégie `ours` ou `theirs`, existe-t-il un risque de perdre des parties de code ou de fichier ?
