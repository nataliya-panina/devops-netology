# devops-netology
# Первоначальная настройка
```
git config --global user.name nataliya-panina
git config --global user.email nataliya.panina@free.fr
```
# git status
moi@ubu:~/devops-netology$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

rien à valider, la copie de travail est propre

moi@ubu:~/devops-netology$ git status 
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Modifications qui ne seront pas validées :
  (utilisez "git add <fichier>..." pour mettre à jour ce qui sera validé)
  (utilisez "git restore <fichier>..." pour annuler les modifications dans le répertoire de travail)
	modifié :         README.md

aucune modification n'a été ajoutée à la validation (utilisez "git add" ou "git commit -a")

moi@ubu:~/devops-netology$ git diff
diff --git a/README.md b/README.md
index 647b370..4c88500 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,25 @@
-# devops-netology
\ No newline at end of file
+# devops-netology
+# Первоначальная настройка
+```
+git config --global user.name nataliya-panina

moi@ubu:~/devops-netology$ git diff --staged
moi@ubu:~/devops-netology$ git add README.md 
moi@ubu:~/devops-netology$ git diff
moi@ubu:~/devops-netology$ git diff --staged
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
+```
+# git status
+moi@ubu:~/devops-netology$ git status
moi@ubu:~/devops-netology$ git commit -m "First commit"
[main df0e3ba] First commit
 1 file changed, 40 insertions(+), 1 deletion(-)
 rewrite README.md (100%)
