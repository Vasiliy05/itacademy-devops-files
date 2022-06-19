# Домашнее задание

- В репозитории `devops-hometasks` создайте директорию `task-02`
- В поддиректории 01 создайте Vagrantfile, который конфигурирует виртуальную машину (одну) c помощью ansible:
  - Настройте виртуальную машину таким образом, чтобы на хост-машине при обращении на адрес http://localhost:8080 открывался статический HTML файл (**index.html**), а при обращении на адрес http://localhost:8081 - динамический сайт (**index.php**)

- В поддиректории 02 создайте Vagrantfile, который конфигурирует три виртуальных машины c помощью ansible:
  - машина со статическим сайтом
  - машина с динмамическим сайтом
  - машина с nginx настроенным в качестве reverse proxy для первых двух машин


# Полезные ссылки

- [Документация Ansible](https://docs.ansible.com/ansible/latest/)
- [Плейлист на YouTube](https://www.youtube.com/playlist?list=PLg5SS_4L6LYufspdPupdynbMQTBnZd31N)
- [Reverse Proxy](https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-web-server-and-reverse-proxy-for-apache-on-one-ubuntu-18-04-server-ru)

# Команды ansible
- `ansible-playbook -i inventory playbook.yaml`
- `ansible-galaxy collection install community.general`
- `ansible -i inventory all -m ping`
- `ansible -i inventory all -m apt -a "name=curl state=present" -b`
- `ansible -i inventory/hosts 192.168.50.5 -m setup`
- `ansible-vault encrypt inventory`
- `ansible-vault view inventory`
- `ansible-vault decrypt inventory`
- `ansible-vault edit inventory`
- `ansible-vault encrypt_string`
- `ansible-playbook -i inventory playbook.yaml --ask-vault-pass`
- `ansible-playbook -i inventory playbook.yaml --vault-password-file password.txt`
- `ansible-inventory --list -i ansible.hosts -y`
- `ansible-inventory --graph -i ansible.hosts`
