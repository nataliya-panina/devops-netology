1. ## Добавление удаленного репозитория gitlab:
```
git remote -v # Просмотр уже подключенных удаленных репозиториев
```

Добавление нового удаленного репозитория:  

```
git remote add gitlab git@gitlab.com:nataliya-panina/devops-netology.git
git remote -v
git push gitlab main
```

![git_remote](https://github.com/nataliya-panina/devops-netology/blob/v0.1/img/git_remote_v.png)

2. ## Теги  

```
git tag # Список тэгов
```

Создание легковесного тэга
```
git tag v0.0 # создание
git push origin v0.0 # Отправка тэга в удаленный репозиторий
git push gitlab v0.0
```
Создание аннотированного тэга  

```
git tag -a v0.1 -m "tag 0.1" # -а - аннотированный тэг
git push origin --tags # Отправка всех тэгов вместе с коммитом в удаленный репозиторий
```
![tags](https://github.com/nataliya-panina/devops-netology/blob/v0.1/img/tag_v0.0.png)  
![tags](https://github.com/nataliya-panina/devops-netology/blob/v0.1/img/tag_v0.0_web.png)  
![tags](https://github.com/nataliya-panina/devops-netology/blob/v0.1/img/tags.png)  
  
Установка тэга на уже существующий коммит 

```
git tag -a v0.2 <hash>
```
Удаление тэга  

```
git tag -d v0.0 # Удалить из рабочего каталога
git push origin --delete <tagname> # Удалить из удаленного репозитория
```
Переход по тэгу  

```
git checkout v0.0
```

1. ## Ветки  

```
git switch -c fix
git push origin fix
```
Создание ветки от тэга  
```
git switch -c <branchname> <tagname>
```

4. ## Упрощение жизни  
![tags](https://github.com/nataliya-panina/devops-netology/blob/main/img/facilite_de_vie.png)
