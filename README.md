Apps-role
=========

Ansible role для установки Wordpress.
Состоит из следующих действий:
- Установка и настройка mysql - [mysql.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/mysql.yml).
- Создание базы данных и пользователя, добавления разрешенных адресов для подключения - [database.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/database.yml)
- Установка и настройка web-сервера nginx - [nginx.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/nginx.yml).
- Установка необходимых пакетов php - [php.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/php.yml).
- Установка Wordpress [wordpress.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/wordpress.yml).
- Установка certbot и получение сертификата [certificate.yml](https://github.com/roman-serdyukov/wordpress-nginx-mysql/blob/main/tasks/certificate.yml)

Requirements
------------

Работоспособность протестирована на Ubuntu 20.04 и 22.04.


Role Variables
--------------

- domain_zones:   имя поддомена
- my_domain:      доменное имя
- email:          адрес электронной почты для запроса сертификата
- mysql_host:     сервер mysql
- wp_version:     версия Wordpress
- php_ver:        версия PHP
- php_pack:       cписок пакетов PHP для установки
- Имена пользователей, баз данных и пароли в папке "vars" (приведены здесь только для демонстрации)

Example Playbook
----------------
```
- name: Install apps server
  hosts: servers
  roles:
    - wordpress-nginx-mysql
```

Before start
----------------

- Указать имя Вашего домена в my_domain.
- Указать Ваш поддомен или удалить связи с переменной domain_zones.
- Указать адрес электронной почты в email.
- Убрать "--test-cert" для продуктового сервера в certificate.yml.
- Перенести в grpup_vars и изменить на Ваши значения mysql_user, mysql_db, mysql_pass.  

License
-------

MIT

Author Information
------------------

Сердюков Роман
reserdukov@gmail.com