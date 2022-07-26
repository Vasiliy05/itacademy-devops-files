# Домашнее задание

- В репозитории `devops-hometasks` создайте директорию `task-02`
- Создайте Vagrantfile, основанный на Debian 10
- Внутри виртуальной машины настройте LXC-контейнеры, основанные на CentOS:
  - с установленным статическим сайтом
  - с установленным динамическим сайтом
- Данные этого домашнего задания должны размещаться в каталоге `task-02` вашего git-репозитория.

# Полезные ссылки

- [Сайт проекта LXC/LXD](https://linuxcontainers.org/)
- [Мануал по конфигурации](https://linuxcontainers.org/lxc/manpages/man5/lxc.container.conf.5.html)
- [Информация и примеры использования LXC](https://saturn.ffzg.hr/rot13/index.cgi?action=display_html;page_name=lxc)
- [Использование контейнеров LXC в Debian/Ubuntu](https://www.opennet.ru/tips/2413_lxc_container_chroot_limit_debian_cgroup.shtml)
- [LXD REST API](https://linuxcontainers.org/lxd/rest-api/)
- [Репозиторий cheese-release](https://centos.pkgs.org/7/cheese-x86_64/cheese-release-7-1.noarch.rpm.html)


# Настройка непривилегированных сессий

## Конфигурация по умолчанию

* Удалите gnupg и переустановите gnupg2
```
apt remove gnupg
apt install --reinstall gnupg2
apt install dirmngr
```

* В файл ~/.bashrc добавьте переменную окружения
```
export DOWNLOAD_KEYSERVER="hkp://keyserver.ubuntu.com"
```

* В домашней директории пользователя создайте директорию `.config/lxc`, в неё скопируйте файл /etc/lxc/default.conf

  1. Измените значение *lxc.apparmor.profile* на *unconfined*
  1. Добавьте в файл настройки отображения *uid* и *gid* (значения должны совпадать со значениями в /etc/subuid и /etc/subgid):
    ```
    lxc.idmap = u 0 100000 65536
    lxc.idmap = g 0 100000 65536
    ```

* В файл /etc/sysctl.conf добавьте параметр
```
kernel.unprivileged_userns_clone=1
```

* В файле /etc/default/grub найдите строку GRUB_CMDLINE_LINUX_DEFAULT и добавьте к значению ` systemd.legacy_systemd_cgroup_controller=yes`. Пример того, как будет выглядеть строка конфигурации:
```bash
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 systemd.legacy_systemd_cgroup_controller=yes"
```
Для того, чтобы изменения были применены, необходимо выполнить команду `update-grub`.

* После предыдущих двух изменений необходимо перезагрузить ОС


## Настройка сети

В файл /etc/lxc/lxc-usernet необходимо добавить строку
```
your-username veth lxcbr0 10
```

* Задайте настройки сети по умолчанию в файле */etc/default/lxc-net*:
```bash
USE_LXC_BRIDGE="true"
LXC_BRIDGE="lxcbr0"
LXC_ADDR="10.0.3.1"
LXC_NETMASK="255.255.255.0"
LXC_NETWORK="10.0.3.0/24"
LXC_DHCP_RANGE="10.0.3.2,10.0.3.254"
LXC_DHCP_MAX="253"
LXC_DHCP_CONFILE=""
LXC_DOMAIN=""
```

* Включите службу lxc-net
```bash
systemctl enable lxc-net
systemctl start lxc-net
```

* Настройте сеть в вашей конфигурации по умолчанию (~/.config/lxc/default.conf)
```
lxc.net.0.type  = veth
lxc.net.0.flags = up
lxc.net.0.link  = lxcbr0
```


# Команды lxc
- `lxc-create -n c1 -t download`
- `lxc-ls`
- `lxc-ls -f`
- `lxc-start c1`
- `lxc-info c1`
- `lxc-attach c1`
- `lxc-autostart`
- `lxc-autostart -a`
- `lxc-autostart -s`

