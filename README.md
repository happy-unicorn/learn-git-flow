# learn-git-flow

-----

Ключевые идеи, которые нужно запомнить о Gitflow:

* Данная модель отлично подходит для организации рабочего процесса на основе релизов.
* Gitflow предлагает создание отдельной ветки для исправлений ошибок в продуктовой среде.

Последовательность работы при использовании модели Gitflow:

1. Из master создается ветка develop.
1. Из develop создаются ветки feature.
1. Когда разработка новой функциональности завершена, она объединяется с веткой develop.
1. Из develop создается ветка release.
1. Когда ветка релиза готова, она объединяется с develop и master.
1. Если в master обнаружена проблема, из нее создается ветка hotfix.
1. Как только исправление на ветке hotfix завершено, она объединяется с develop и master.

-----

### Ветки master и develop

Вместо использования одной ветки master, в этой модели используется две ветки для записи истории проекта. В ветке master хранится официальная история релиза, а ветка develop служит в качестве интеграционной ветки для новых функций. Также, удобно тегировать все коммиты в ветке master номером версии.

Первым шагом является создание ветки develop от ветки master. Проще всего это сделать одному разработчику, локально создав пустую ветку и отправив ее в центральный репозиторий:

```bash
$ git branch develop
$ git push -u origin develop
```

В этой ветке будет находиться вся история проекта, в то время как master содержит частичную историю. Остальные разработчики теперь должны клонировать центральный репозиторий и создать отслеживающую ветку для ветки develop.

При использовании библиотеки расширений git-flow, для создания ветки develop можно выполнить git flow init в существующем репозитории:

```bash
$ git flow init
Initialized empty Git repository in ~/project/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [master]
Branch name for "next release" development: [develop]
How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
$ git branch
* develop
  master
```
