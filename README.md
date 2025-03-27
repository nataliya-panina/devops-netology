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
moi@ubu:~/devops-netology$ 

