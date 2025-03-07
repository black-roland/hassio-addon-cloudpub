# Home Assistant Add-on: CloudPub

Этот аддон предоставляет внешний доступ к Home Assistant и другим локальным ресурсам за NAT без «белого» IP. Это неофициальное дополнение для сервиса [CloudPub](https://cloudpub.ru/), который является альтернативой KeenDNS, Dataplicity, Ngrok, Cloudflared и другим подобным сервисам.

## Ключевые особенности

- **Простота**. Достаточно скопировать токен из личного кабинета, вставить его в настройки аддона и нажать «Запустить». Через секунду ваш Home Assistant станет доступен из интернета по автогенерируемой ссылке.
- **Поддержка HTTPS**. Внешние ссылки используют HTTPS, а значит трафик до сервера CloudPub зашифрован.
- **Проксирование TCP и UDP**. Поддерживается не только HTTP, но и другие протоколы, включая RTSP.
- **Серверы в России**. Потенциально более высокая стабильность и производительность для пользователей из России.

<img src="https://github.com/user-attachments/assets/9aa52fe2-0fda-40ce-a15e-e4c7702c8c19" alt="Логи аддона" height="400" />
<img src="https://github.com/user-attachments/assets/32bddd8d-7986-4640-a0d7-66c7fcf50eeb" alt="Сервисы в CloudPub" height="400" />

## Установка

Для установки аддона добавьте репозиторий в Home Assistant. Вы можете сделать это вручную, указав ссылку на репозиторий (`https://github.com/black-roland/hassio-addon-cloudpub`), или нажав кнопку ниже:

[![Добавить репозиторий в Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fblack-roland%2Fhassio-addon-cloudpub)

После добавления репозитория вы сможете установить дополнение в настройках Home Assistant.

## Подробная документация

Подробные инструкции по настройке и использованию аддона доступны в [DOCS.md](https://github.com/black-roland/hassio-addon-cloudpub/blob/master/cloudpub/DOCS.md).

## Поддержка автора

Если этот аддон оказался полезным, вы можете [угостить автора чашечкой кофе](https://mansmarthome.info/donate/#donationalerts). Ваша благодарность ценится!

#### Благодарности

Огромное спасибо всем, кто поддерживает этот проект:

![Спасибо](https://github.com/user-attachments/assets/44d227fd-b929-41c3-a25f-5b438390d41a)



