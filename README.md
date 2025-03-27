# devops-netology
## Первоначальная настройка
```
git config --global user.name nataliya-panina
git config --global user.email nataliya.panina@free.fr
```
## git status
```
git status
```
```
Sur la branche main
Votre branche est à jour avec 'origin/main'.

rien à valider, la copie de travail est propre
```
## После изменеия файла

git status 
```

Sur la branche main
Votre branche est à jour avec 'origin/main'.

Modifications qui ne seront pas validées :
  (utilisez "git add <fichier>..." pour mettre à jour ce qui sera validé)
  (utilisez "git restore <fichier>..." pour annuler les modifications dans le répertoire de travail)
	modifié :         README.md

aucune modification n'a été ajoutée à la validation (utilisez "git add" ou "git commit -a")
```
git diff

```
diff --git a/README.md b/README.md
index 647b370..4c88500 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,25 @@
-# devops-netology
\ No newline at end of file
+# devops-netology
+# Первоначальная настройка
```

git diff --staged

## Добавление файла в индекс
```
git add README.md 
git diff
git diff --staged
```
```
diff --git a/README.md b/README.md
index 647b370..5cd540e 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,40 @@
-# devops-netology
\ No newline at end of file
+# devops-netology
+# Первоначальная настройка
+```
+git config --global user.name nataliya-panina
+git config --global user.email nataliya.panina@free.fr
```

## Коммит
```
git commit -m "First commit"
```
```
[main df0e3ba] First commit
 1 file changed, 40 insertions(+), 1 deletion(-)
 rewrite README.md (100%)
moi@ubu:~/devops-netology$ git commit -m "First commit"
[main c645f33] First commit
 1 file changed, 22 insertions(+), 2 deletions(-)
moi@ubu:~/devops-netology$ git status
Sur la branche main
Votre branche est en avance sur 'origin/main' de 2 commits.
  (utilisez "git push" pour publier vos commits locaux)

rien à valider, la copie de travail est propre
```
```
git diff
git diff --staged
```

## .gitignore
```
touch .gitignore
git status
```
```
Sur la branche main
Votre branche est en avance sur 'origin/main' de 2 commits.
  (utilisez "git push" pour publier vos commits locaux)

Modifications qui ne seront pas validées :
  (utilisez "git add <fichier>..." pour mettre à jour ce qui sera validé)
  (utilisez "git restore <fichier>..." pour annuler les modifications dans le répertoire de travail)
        modifié :         README.md

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
        .gitignore

aucune modification n'a été ajoutée à la validation (utilisez "git add" ou "git commit -a")
```
```
git add .
```

