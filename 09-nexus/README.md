# Скрипт для развертывания приложения на сервере

```bash
sudo service wordcloud stop

curl -X GET "http://192.168.33.90:8081/repository/word-cloud-build/1/word-cloud-generator/1.$BUILD_NUMBER/word-cloud-generator-1.$BUILD_NUMBER.gz" -o /opt/wordcloud/word-cloud-generator.gz
ls -l /opt/wordcloud
gunzip -f /opt/wordcloud/word-cloud-generator.gz
chmod +x /opt/wordcloud/word-cloud-generator

sudo service wordcloud start
```

## systemd servie /etc/systemd/system/wordcloud.service

```bash
[Unit]
Description=Word Cloud Generator

[Service]
WorkingDirectory=/opt/wordcloud
ExecStart=/opt/wordcloud/word-cloud-generator
Restart=always

[Install]
WantedBy=multi-user.target
```

# Интеграционные тесты
```bash
res=`curl -s -H "Content-Type: application/json" -d '{"text":"ths is a really really really important thing this is"}' http://192.168.33.80:8888/version | jq '. | length'`
if [ "1" != "$res" ]; then
  exit 99
fi

res=`curl -s -H "Content-Type: application/json" -d '{"text":"ths is a really really really important thing this is"}' http://192.168.33.80:8888/api | jq '. | length'`
if [ "7" != "$res" ]; then
  exit 99
fi
```

# Домашнее задание

- Добавьте к Vagrantfile еще 3 машины:
  - nexus.vm
  - staging.vm
  - production.vm
- На машине nexus.vm установите Nexus3. Для установки и настройки используйте роль [nexus3-oss](https://github.com/ansible-ThoTeam/nexus3-oss).
  - Создается репозиторий для хранения артефактов сборки
  - Создается отдельный пользователь для загрузки данных в репозиторий
  - Создается отдельный пользователь для скачивания данных из репозитория
- На машинах staging.vm и production.vm создайте условия для установки и настройки службы word-cloud-generator

# Полезные ссылки

- [Nexus3 downloads](https://help.sonatype.com/repomanager3/product-information/download/download-archives---repository-manager-3)
