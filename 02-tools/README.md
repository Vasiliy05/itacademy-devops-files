# Домашнее задание (не оценивается)

- Инициализируйте локальный git-репозиторий
- Создайте файл README.md с описанием проекта
- Создайте следующие ветки
  - master (2 коммита)
  - dev из ветки master (2 коммита из master + 2 дополнительных)
  - features/dosmth (коммиты из dev + 1 дополнительный)
  - hotfix/bugfix (2 коммита из master + 1 дополнительный)
- Разыграйте следующие сценарии:
  - Релиз:
	- Все коммиты (кроме хотфикса) должны попасть в master
  - Выпуск исправления:
	- Изменения из hotfix/bugfix должны сначала попасть в master, а потом и в остальные ветки

# Домашнее задание (не оценивается)
- Зарегистрироваться на [GitHub](https://github.com/)
  - Добавить на GitHub SSH-ключ
  - Создать на GitHub репозиторий
  - Синхронизировать ваш локальный репозиторий с репозиторием в GitHub
- GitLab CE *
  - Установите локально (VirtualBox) GitLab CE
  - Синхронизируйте ваши локальные репозитории с вашей версией GitLab

# Домашнее задание
- Создайте Vagrantfile для создания виртуальной машины VirtualBox с установленной ОС Debian 10.
- Настройте виртуальную машину таким образом, чтобы на хост-машине при обращении на адрес http://localhost:8080 открывался статический HTML файл **index.html**, а при обращении на адрес http://localhost:8081 - динамический сайт **index.php**. Для работы динамического сайта нужен PHP любой версии.
- Создайте на GitHub репозиторий devops-hometasks. Поместите полученный Vagrantfile и все необходимые для его работы файлы в директорию task-01 в этом репозитории. Ссылку на репозиторий отправьте мне.
- Директорию `.vagrant` внесите в `.gitignore`.

# Домашнее задание
- Создайте и опубликуйте на [Vagrant Cloud](https://vagrantcloud.com/) образ Vagrant, удовлетворяющий требованиям:
  - Основан на centos/8
  - Включает установленный apache2
  - Включает установленный php
  - Включает установленный mysql-server
- Переработайте первое домашнее задание, основываясь на вашем образе. В вашем репозитории создайте ветку `feature-01`. Загрузите переработанное 1-е домашнее задание в каталог `task-01` в ветке `feature-01`.
- Так же в директории `task-01` создайте `README.md` файл, в который пропишите ссылку на ваш Vagrant образ в Vagrant Cloud.
- На комит поставьте тег `01.beta`.

# Полезные ссылки

- [Как работать с ветвлением](https://gist.github.com/digitaljhelms/4287848)
- [Погружение в Git](http://gitimmersion.com)
- [Github](https://github.com)
- [GitLab](https://gitlab.com)
- [GitLab CE](https://about.gitlab.com/install/?version=ce)
- [Bitbucket](https://bitbucket.org)
- [Установка собственного Bitbucket сервера](https://confluence.atlassian.com/bitbucketserver/bitbucket-server-installation-guide-867338382.html)
- [Hello-world project on GitHub](https://guides.github.com/activities/hello-world/)
- [Работа с репозиторием на GitHub](https://github.com/andreiled/mipt-cs-4sem/wiki/\%D0\%9F\%D0\%BE\%D1\%88\%D0\%B0\%D0\%B3\%D0\%BE\%D0\%B2\%D0\%B0\%D1\%8F-\%D0\%B8\%D0\%BD\%D1\%81\%D1\%82\%D1\%80\%D1\%83\%D0\%BA\%D1\%86\%D0\%B8\%D1\%8F-\%D0\%BF\%D0\%BE-\%D1\%80\%D0\%B0\%D0\%B1\%D0\%BE\%D1\%82\%D0\%B5-\%D1\%81-git-\%D0\%B8-github-\%D0\%B4\%D0\%BB\%D1\%8F-\%D1\%81\%D1\%82\%D1\%83\%D0\%B4\%D0\%B5\%D0\%BD\%D1\%82\%D0\%BE\%D0\%B2)
- [Видеокурс по Git и GitHub](https://www.youtube.com/results?search_query=\%23loftblogGit)
- [Ещё инструкция по GitHub](https://habr.com/ru/post/125799/)
- [Как работать с GitLab](https://losst.ru/kak-polzovatsya-gitlab)
- [Установка GitLab на Ubuntu](https://1cloud.ru/help/linux/ustanovka-gitlab-na-ubuntu)
- [Vagrant образы](https://app.vagrantup.com/boxes/search)
- [Документация](https://www.vagrantup.com/docs/)
- [Примеры конфигураций](https://github.com/patrickdlee/vagrant-examples)
- [Инструкция по сборке базового образа](https://www.vagrantup.com/docs/boxes/base.html)
- [Утилита Packer](https://www.packer.io)

# Команды git
- `git branch branch1`
- `git branch`
- `git checkout branch1`
- `git checkout -b branch2`
- `git stash`
- `git stash -u`
- `git stash list`
- `git stash show stash@{0}`
- `git stash apply stash@{1}`
- `git stash drop stash@{1}`
- `git stash clear`
- `git stash pop`
- `git log --all --graph --online`
- `git merge master`
- `git rebase master`
- `git branch -d branch2`
- `git tag v1`
- `git tag`
- `git show v1`
- `git tag --delete v1`
- `git help merge`
- `git remote add origin git@github.com:Fenikks/git_demo.git`
- `git remote -v`
- `git remote rename origin test`
- `git push -u origin master`
- `git remote show origin`
- `git clone`
- `git pull`

# Команды vagrant
- `vagrant init`
- `vagrant up`
- `vagrant ssh`
- `vagrant suspend`
- `vagrant halt`
- `vagrant destroy`
- `vagrant status`
- `vagrant global-status`
