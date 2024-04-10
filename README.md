# sbg-tp7
# Préparation du dépôt local
|Quel est le résultat de la commande suivante :
'' $ git status ''
Ce résultat indique que :

Le fichier change-me a été modifié.
Le fichier delete-me a été supprimé.
Un nouveau fichier add-me est présent mais non suivi (non ajouté à l'index).
Aucun changement n'a été ajouté pour le prochain commit.

-------------------------------------------------------------------------------
# Ajout des modifications avec git add .
|Exécutez la commande suivante :
'' $ git add .''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Ce résultat indique que les modifications apportées aux fichiers change-me et delete-me ont été ajoutées à l'index pour le prochain commit. De plus, le nouveau fichier add-me a également été ajouté à l'index. Ces changements sont prêts à être inclus dans le prochain commit.

|Exécutez la commande suivante pour annuler le git add . :
'' $ git reset ''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Cela indique que les fichiers change-me et delete-me ont été modifiés mais ne sont pas encore ajoutés à l'index. De plus, le fichier add-me est toujours non suivi. Aucun changement n'a été ajouté pour le prochain commit.

-----------------------------------------------------------
# Ajout des modifications avec git add -u
|Exécutez la commande suivante :
'' $ git add -u ''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Ce résultat indique que les modifications apportées aux fichiers change-me et delete-me ont été ajoutées à l'index pour le prochain commit. Cependant, le fichier add-me reste non suivi et n'a pas été ajouté à l'index.

|excutez la commande suivante pour annuler le git add -u :
'' $ git reset ''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Cela indique que les modifications apportées aux fichiers change-me et delete-me ne sont plus en attente d'être ajoutées à l'index. De plus, le fichier add-me est toujours répertorié comme non suivi. Aucun changement n'a été ajouté pour le prochain commit.

-------------------------------------------------------------------------------------------
# Ajout des modifications avec git add -A
|Exécutez la commande suivante :
'' $ git add -A ''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Ce résultat indique que les modifications apportées aux fichiers change-me et delete-me ont été ajoutées à l'index pour le prochain commit. De plus, le nouveau fichier add-me a également été ajouté à l'index. Ces changements sont prêts à être inclus dans le prochain commit.

|Exécutez la commande suivante pour annuler le git add -A :
'' $ git reset ''
|Quel est le résultat de la commande suivante :
'' $ git status ''

Cela indique que les modifications apportées aux fichiers change-me et delete-me ne sont plus en attente d'être ajoutées à l'index. De plus, le fichier add-me est répertorié comme non suivi. Aucun changement n'a été ajouté pour le prochain commit.

------------------------------------------------------------------------------
# Modification en profondeur du dépôt
# Mise en place

|Placez-vous à la racine de votre dépôt (normalement, vous y êtes déjà...) et exécutez les commandes suivantes :
$ mkdir levelone-a
$ mkdir levelone-b
$ echo Created at $(date) > levelone-a/change-me
$ echo Created at $(date) > levelone-b/change-me
$ echo Delete me > levelone-a/delete-me
$ echo Delete me > levelone-b/delete-me

|Quel est le résultat de la commande suivante :
$ find . -type d -path  "*/.*" -prune -o -print | sed -e "s/[^-][^\/]*\//  | /g" -e "s/| \([^ ]\)/|-- \1/"
 |-- add-me
  |-- levelone-b
  |   |-- delete-me
  |   |-- change-me
  |-- README.md
  |-- levelone-a
  |   |-- delete-me
  |   |-- change-me
  |-- change-me

Un fichier add-me.
Deux répertoires levelone-a et levelone-b, chacun contenant un fichier change-me et un fichier delete-me.
Un fichier README.md.
Un fichier change-me supplémentaire à la racine du dépôt

---------------------------------------------------------------------------------------  
# Déplacez-vous ensuite dans le répertoire « levelone-a ».
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Le résultat de la commande git status -uall après s'être déplacé dans le répertoire levelone-a indique ce qui suit :

Des modifications ont été apportées aux fichiers change-me et delete-me qui se trouvent dans le répertoire parent (.. fait référence au répertoire parent).
Il y a des fichiers non suivis dans le répertoire parent (../add-me) ainsi que dans le répertoire actuel (change-me et delete-me).
Il y a également des fichiers non suivis dans le répertoire levelone-b (à savoir change-me et delete-me).
Aucun changement n'a été ajouté à l'index pour le prochain commit.

|Ajoutez les nouveaux fichiers de « levelone-a » avec :
''$ git add . ''
'' git commit -m "initial levelone-a" ''
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Cela indique que votre branche locale est en avance d'un commit par rapport à la branche distante main. Il n'y a aucun changement non suivi ou non ajouté à l'index dans votre répertoire de travail.

-----------------------------------------------------------------------------------
# Modification du dépôt
Ensuite exécutez successivement les commandes suivantes :
'' $ echo Changed at $(date) >> change-me ''
'' $ rm delete-me '' 
'' $ echo Added at $(date) > add-me ''

|Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Le résultat de la commande git status -uall après avoir exécuté les commandes pour modifier le dépôt dans le répertoire levelone-a indique ce qui suit :

La branche locale est en avance d'un commit par rapport à la branche distante main.
Les fichiers change-me et delete-me ont été modifiés dans le répertoire parent ainsi que dans le répertoire actuel levelone-a.
Les fichiers add-me dans le répertoire parent et add-me dans le répertoire actuel levelone-a sont non suivis.
Les fichiers change-me et delete-me dans le répertoire levelone-b sont également non suivis.
Aucun changement n'a été ajouté à l'index pour le prochain commit.

--------------------------------------------------------------------------------
# Ajout des modifications avec git add .
Exécutez la commande suivante :
'' $ git add . ''
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Cela indique que les modifications apportées aux fichiers change-me et delete-me dans le répertoire actuel levelone-a, ainsi que le nouveau fichier add-me, ont été ajoutées à l'index pour le prochain commit. Cependant, les modifications apportées aux fichiers change-me et delete-me dans le répertoire parent (.. fait référence au répertoire parent) sont toujours non stagées, tout comme les fichiers non suivis dans le répertoire levelone-b.

| Exécutez la commande suivante pour annuler le git add . :
'' $ git reset ''
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Le résultat de la commande git reset montre que les modifications apportées aux fichiers change-me et delete-me dans le répertoire parent, ainsi que dans le répertoire actuel levelone-a ont été annulées. Cependant, ces modifications restent dans l'état de travail non stagé.

Le résultat de la commande git status -uall indique que ces modifications non stagées subsistent. De plus, des fichiers non suivis sont également présents dans les répertoires parent et levelone-b. Aucun changement n'a été ajouté à l'index pour le prochain commit.

------------------------------------------------------------------------------------------
# Ajout des modifications avec git add -A
|Exécutez la commande suivante :
'' $ git add -A ''
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''
Exécutez la commande suivante pour annuler le git add -A :

Cela indique que les modifications apportées aux fichiers change-me et delete-me dans les répertoires parent (..) et actuel (levelone-a), ainsi que le nouveau fichier add-me dans le répertoire actuel levelone-a et les nouveaux fichiers change-me et delete-me dans le répertoire levelone-b, ont tous été ajoutés à l'index pour le prochain commit. De plus, le fichier delete-me a été renommé de delete-me à levelone-b/delete-me.

'' $ git reset ''
Quel est le résultat de la commande suivante :
'' $ git status -uall ''

Le résultat de la commande git status -uall indique que ces modifications non stagées subsistent. De plus, des fichiers non suivis sont également présents dans les répertoires parent et levelone-b. 

--------------------------------------------------------------------------------------
# Utilisation des branches
Nous allons utiliser le répertoire « levelone-b » pour cette étape. Déplacez-vous dans ce dernier.
|Quel est le résultat de la commande suivante :
'' $ git status -uall ''
Le résultat de la commande git status -uall montre ce qui suit :

Nous sommes actuellement sur la branche "main".
Notre branche locale est en avance par rapport à la branche "main" sur le dépôt distant ("origin/main") d'un commit.
Il y a des modifications non stagées dans notre répertoire de travail.
Les fichiers change-me et delete-me dans le répertoire parent (..) ont été modifiés et supprimés.
Les fichiers change-me et delete-me dans le répertoire levelone-a ont également été modifiés et supprimés.
Il y a des fichiers non suivis dans le répertoire de travail, y compris add-me dans le répertoire parent (..) et levelone-a/add-me, ainsi que change-me et delete-me dans le répertoire actuel (levelone-b).

----------------------------------------------------------------------------------------
# Créer une nouvelle branche « dev »
Pour cela utilisez la commande suivante :
'' $ git branch dev ''
Pour visualiser les branches disponibles vous pouvez utiliser la commande :
'' $ git branch ''
|Précisez quel est le résultat de son exécution ?

Cela signifie que deux branches sont disponibles dans votre dépôt : "dev" (nouvelle branche créée) et "main" (branche par défaut). L'astérisque (*) indique la branche actuellement active, qui est "main" dans cet exemple.

----------------------------------------------------------------------------------------------------------
# Changer de branche pour aller sur « dev »

On se déplace sur la branche « dev » avec :
'' $ git checkout dev ''
M       change-me
D       delete-me
M       levelone-a/change-me
D       levelone-a/delete-me
Switched to branch 'dev'

|Vous devriez avoir alors comme résultat un message d'erreur. Que dit-il (en français) ? Avez-vous effectivement changé de branche ?
error: pathspec 'dev' did not match any file(s) known to git

Ce message d'erreur indique que Git n'a pas trouvé de référence (branche ou fichier) correspondant au nom "dev". Cela peut se produire si la branche "dev" n'a pas été créée localement ou si elle n'existe pas dans le dépôt distant.

|Quel est le contenu du fichier « levelone-b/change-me » ?
dlouisy5@cloudshell:~/sbg-tp7/levelone-b (vernal-dispatch-417015)$ ls
change-me  delete-me
dlouisy5@cloudshell:~/sbg-tp7/levelone-b (vernal-dispatch-417015)$ cat change-me 
Created at Wed 10 Apr 2024 01:41:34 PM UTC

Pour pouvoir changer de branche, nous allons utiliser la commande « stash » de Git. Exécutez :

'' $ git stash ''
puis de nouveau :
'' $ git checkout dev ''
Quel est le résultat de chacune de ces deux commandes ?
dlouisy5@cloudshell:~/sbg-tp7/levelone-b (vernal-dispatch-417015)$ git stash
Saved working directory and index state WIP on dev: 5c4d717 initial levelone-a
dlouisy5@cloudshell:~/sbg-tp7/levelone-b (vernal-dispatch-417015)$ git checkout dev
Already on 'dev'
dlouisy5@cloudshell:~/sbg-tp7/levelone-b (vernal-dispatch-417015)$ 

Quel est le résultat de la commande suivante :
'' $ git status -uall ''
|Qu'y-a-t'il de changé depuis la dernière utilisation de cette commande ?

-------------------------------------------------------------------------------------
# Revenir à la branche principale « main »
Exécutez :
'' $ git checkout dev ''
Quel est le résultat de la commande :

'' $ git status -uall ''
|Quel est le contenu des fichiers « levelone-a/change-me » et « levelone-a/delete-me » ?

Exécutez :
$ git stash pop
Que s'est-il passé ?

La commande git stash pop a réussi à appliquer les modifications qui étaient précédemment stashées. Voici ce qui s'est passé :

Les fichiers levelone-a/delete-me et delete-me ont été supprimés car ils faisaient partie des modifications stashées.
Vous êtes maintenant sur la branche "dev".
Le message indique que les modifications stashées ont été appliquées avec succès.
Cependant, les fichiers modifiés ../change-me et ../levelone-a/change-me ainsi que les fichiers supprimés ../delete-me et ../levelone-a/delete-me sont toujours présents dans votre répertoire de travail mais ne sont pas encore stagés pour le prochain commit.
Il y a également des fichiers non suivis dans votre répertoire de travail, dont le répertoire actuel ./.

Quel est le résultat de la commande :
'' $ git status -uall ''

-------------------------------------------------------
# Retourner à la branche « dev »
Ajoutez les modifications des fichiers de « levelone-a » en vous déplacant dans ce répertoire puis en exécutant :
$ git add .
git commit -m "modifications levelone-a"

dlouisy5@cloudshell:~/sbg-tp7/levelone-a (vernal-dispatch-417015)$ git commit -m "modifications levelone-a"
[dev d494f00] modifications levelone-a
 3 files changed, 2 insertions(+), 1 deletion(-)
 create mode 100644 levelone-a/add-me
 delete mode 100644 levelone-a/delete-me
 
Retourner enfin à la branche « dev ».

--------------------------------------------------------------------------
# Modifier « levelone-b » dans « dev »
Ensuite exécutez successivement les commandes suivantes :

$ echo Changed at $(date) >> change-me
$ rm delete-me
$ echo Added at $(date) > add-me
Quel est le résultat de la commande suivante :
$ git status -uall
Ajoutez et validez vos modifications dans « levelone-b ».

On branch dev
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   ../change-me
        deleted:    ../delete-me
        modified:   change-me
        deleted:    delete-me
        untracked:  add-me

no changes added to commit (use "git add" and/or "git commit -a")


Quel est le contenu de « levelone-b » ? Quel est le contenu des fichiers présents dans « levelone-b » ?
Contenu du répertoire "levelone-b" :
Fichier "change-me" :
Changed at <date>
Fichier "delete-me" : (supprimé)
Fichier "add-me" :
Added at <date>

----------------------------------------------------------------------------------------------------
# Retour sur la branche « main »
Retourner sur la branche « main ».
Quel est le contenu de « levelone-b » ? Quel est le contenu des fichiers présents dans « levelone-b » ?
Contenu de "levelone-b" sur la branche "main":
Fichier "change-me" : Contenu modifié par la branche "dev"
Fichier "delete-me" : Fichier supprimé par la branche "dev"
Fichier "add-me" : Fichier ajouté par la branche "dev"

# Retour sur la branche « dev»
Retourner sur la branche « dev ».
Quel est le contenu de « levelone-b » ? Quel est le contenu des fichiers présents dans « levelone-b » ?
Contenu de "levelone-b" sur la branche "dev":
Fichier "change-me" : Contenu modifié par la branche "dev"
Fichier "delete-me" : Fichier supprimé par la branche "dev"
Fichier "add-me" : Fichier ajouté par la branche "dev"

Sur la branche "main":
Fichier "change-me" : Modifié par la branche "dev".
Fichier "delete-me" : Supprimé par la branche "dev".
Fichier "add-me" : Ajouté par la branche "dev".
Ensuite, après être revenu à la branche "dev", le contenu de "levelone-b" reste le même :

Sur la branche "dev":
Fichier "change-me" : Modifié par la branche "dev".
Fichier "delete-me" : Supprimé par la branche "dev".
Fichier "add-me" : Ajouté par la branche "dev".

-------------------------------------
# Fusionner les modifications de « dev » dans « main »
Retourner sur la branche « main ».
Exécutez :
$ git merge -m "first merge" dev
Quel est le résultat de la commande suivante après la fusion :
$ git status -uall

On branch main
nothing to commit, working tree clean

Contenu de "levelone-b" après la fusion :
Fichier "change-me" : Modifié par la branche "dev" et fusionné dans "main".
Fichier "delete-me" : Supprimé par la branche "dev" et fusionné dans "main".
Fichier "add-me" : Ajouté par la branche "dev" et fusionné dans "main".

Quel est le contenu de « levelone-b » ? Quel est le contenu des fichiers présents dans « levelone-b » ?Retourner sur la branche « main ».
Contenu de "levelone-b" après la fusion :
Fichier "change-me" : Contenu modifié par la branche "dev" et fusionné dans "main".
Fichier "delete-me" : Fichier supprimé par la branche "dev" et fusionné dans "main".
Fichier "add-me" : Fichier ajouté par la branche "dev" et fusionné dans "main".
Le contenu de "levelone-b" reflète maintenant les modifications fusionnées de la branche "dev" dans la branche "main".

------------------------------------------------
# Finale
Placez-vous à la racine du dépôt.
Exécutez :
$ git add -A

