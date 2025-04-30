# Домашнее задание к занятию «Инструменты Git»
## Цель задания

В результате выполнения задания вы:

    научитесь работать с утилитами Git;
    потренируетесь решать типовые задачи, возникающие при работе в команде.

## Инструкция к заданию

    Склонируйте репозиторий с исходным кодом Terraform.
    Создайте файл для ответов на задания в своём репозитории, после выполнения прикрепите ссылку на .md-файл с ответами в личном кабинете.
    Любые вопросы по решению задач задавайте в чате учебной группы.

## Задание

В клонированном репозитории:

    Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
    Ответьте на вопросы.

    Какому тегу соответствует коммит 85024d3?  
    Сколько родителей у коммита b8d720? Напишите их хеши.  
    Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.  
    Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).  
    Найдите все коммиты, в которых была изменена функция globalPluginDirs.  
    Кто автор функции synchronizedWriters?  

В качестве решения ответьте на вопросы и опишите, как были получены эти ответы.
---

## Решение
```
mkdir git-tools
cd git-tools
git clone https://github.com/hashicorp/terraform
```
 Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.  
---
 ```
 git show aefea
 Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Jun 18 10:29:58 2020 -0400

    Update CHANGELOG.md

diff --git a/CHANGELOG.md b/CHANGELOG.md
index 86d70e3e0d..588d807b17 100644
--- a/CHANGELOG.md
+++ b/CHANGELOG.md
@@ -27,6 +27,7 @@ BUG FIXES:
 * backend/s3: Prefer AWS shared configuration over EC2 metadata credentials by default ([#25134](https://github.com/hashicorp/terraform/issues/25134))
 * backend/s3: Prefer ECS credentials over EC2 metadata credentials by default ([#25134](https://github.com/hashicorp/terraform/issues/25134))
 * backend/s3: Remove hardcoded AWS Provider messaging ([#25134](https://github.com/hashicorp/terraform/issues/25134))
+* command: Fix bug with global `-v`/`-version`/`--version` flags introduced in 0.13.0beta2 [GH-25277]
 * command/0.13upgrade: Fix `0.13upgrade` usage help text to include options ([#25127](https://github.com/hashicorp/terraform/issues/25127))
 * command/0.13upgrade: Do not add source for builtin provider ([#25215](https://github.com/hashicorp/terraform/issues/25215))
 * command/apply: Fix bug which caused Terraform to silently exit on Windows when using absolute plan path ([#25233](https://github.com/hashicorp/terraform/issues/25233))
 ```

1.    Какому тегу соответствует коммит 85024d3?  
---
```
git log 85024d3

commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)
Author: tf-release-bot <terraform@hashicorp.com>
Date:   Thu Mar 5 20:56:10 2020 +0000

    v0.12.23
```
Коммит 85024d3 соответствует тэгу v0.12.23

2.    Сколько родителей у коммита b8d720? Напишите их хеши.  
---
```
git show 85024d3^
```
У этого коммита один родитель:
```
commit 4703cb6c1c7a00137142da867588a5752c54fa6a
Author: Kristin Laemmert <mildwonkey@users.noreply.github.com>
Date:   Thu Mar 5 15:27:37 2020 -0500
```

3.    Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.  
---
```
git log v0.12.23..v0.12.24 --oneline
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release
```

4.    Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).  
---
```
git grep -p 'func providerSource'
provider_source.go=import (
provider_source.go:func providerSource(configs []*cliconfig.ProviderInstallation, services *disco.Disco) (getproviders.Source, tfdiags.Diagnostics) {
```
```
git log -L :'func providerSource':provider_source.go
commit 8c928e83589d90a031f811fae52a81be7153e82f
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Thu Apr 2 18:04:39 2020 -0700

    main: Consult local directories as potential mirrors of providers
    
    This restores some of the local search directories we used to include when
    searching for provider plugins in Terraform 0.12 and earlier. The
    directory structures we are expecting in these are different than before,
    so existing directory contents will not be compatible without
    restructuring, but we need to retain support for these local directories
    so that users can continue to sideload third-party provider plugins until
    the explicit, first-class provider mirrors configuration (in CLI config)
    is implemented, at which point users will be able to override these to
    whatever directories they want.
    
    This also includes some new search directories that are specific to the
    operating system where Terraform is running, following the documented
    layout conventions of that platform. In particular, this follows the
    XDG Base Directory specification on Unix systems, which has been a
    somewhat-common request to better support "sideloading" of packages via
    standard Linux distribution package managers and other similar mechanisms.
    While it isn't strictly necessary to add that now, it seems ideal to do

diff --git a/provider_source.go b/provider_source.go
--- /dev/null
+++ b/provider_source.go
@@ -0,0 +19,5 @@
+func providerSource(services *disco.Disco) getproviders.Source {
```

5.    Найдите все коммиты, в которых была изменена функция globalPluginDirs.  
---
```
git log -SglobalPluginDirs --oneline

7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package
```

6.    Кто автор функции synchronizedWriters?  
---
```
git log -SsynchronizedWriters
commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Wed May 3 16:25:41 2017 -0700

    main: synchronize writes to VT100-faker on Windows
```
автор функции synchronizedWriters - Martin Atkins <mart@degeneration.co.uk>