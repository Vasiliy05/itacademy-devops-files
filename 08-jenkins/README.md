# Скрипт для сборки проекта

```bash
export GOPATH=$WORKSPACE/go
export PATH="$PATH:$(go env GOPATH)/bin"

go get github.com/tools/godep
go get github.com/smartystreets/goconvey
go get github.com/GeertJohan/go.rice/rice
go get github.com/wickett/word-cloud-generator/wordyapi
go get github.com/gorilla/mux

sed -i "s/1.DEVELOPMENT/1.$BUILD_NUMBER/g" static/version

GOOS=linux GOARCH=amd64 go build -o ./artifacts/word-cloud-generator -v 

md5sum artifacts/word-cloud-generator
gzip artifacts/word-cloud-generator
ls -l artifacts/
```

# Домашнее задание

- В репозитории `devops-hometasks` создайте директорию `task-06`
- C помощью Vagrant создайте виртуальную машину `jenkins.vm` основанную на Debian 10
- На машине jenkins.vm установите Jenkins. Для настройки Jenkins можно использовать роль [ansible-jenkins](https://github.com/emmetog/ansible-jenkins).
  - Необходимые плагины должны устанавливаться автоматически
  - Конфигурация системы должна производиться автоматически
  - Задача должна создаваться и настраиваться автоматически

# Полезные ссылки

- [Установка Jenkins](https://jenkins.io/doc/book/installing/)
- [Настройка агентов Jenkins](https://kamaok.org.ua/?p=2929)
- [Репозиторий приложения](https://github.com/wickett/word-cloud-generator)
- [Библиотека ролей для ansible](https://galaxy.ansible.com)
- [Роль для настройки jenkins](https://github.com/emmetog/ansible-jenkins)
- [Jenkins Wiki](https://wiki.jenkins.io/display/JENKINS/)
- [Установка Jenkins без настройки в браузере](https://blog.nimbleci.com/2016/10/11/how-to-deploy-jenkins-completely-pre-configured/)    
