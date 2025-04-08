# Home Assistant Add-on: CloudPub

![Последняя версия][latest-version-shield]
![Проект поддерживается?][maintenance-shield]
![Активных инсталляций][reported-installations-shield]
![Скачиваний в неделю][weekly-downloads-shield]
[![На кофе][donate-shield]][donate-link]

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

![Спасибо][donors-list]

[latest-version-shield]: https://img.shields.io/github/package-json/v/black-roland/hassio-addon-cloudpub?filename=cloudpub%2Fconfig.json&style=flat-square&label=%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F
[maintenance-shield]: https://img.shields.io/maintenance/%D0%B4%D0%B0/2025?style=flat-square&label=%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%B8%D0%B2%D0%B0%D0%B5%D1%82%D1%81%D1%8F%3F
[reported-installations-shield]: https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fanalytics.home-assistant.io%2Faddons.json&query=6cd8d65a_cloudpub.total&style=flat-square&label=%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D0%B5%D0%B9&color=brightgreen&cacheSeconds=86400
[weekly-downloads-shield]: https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fmansmarthome.info%2Fgithub%2Fblack-roland%2Fhassio-addon-cloudpub%2Ftraffic.json&query=weekly.uniques&suffix=%20%D0%B2%20%D0%BD%D0%B5%D0%B4%D0%B5%D0%BB%D1%8E&style=flat-square&label=%D1%81%D0%BA%D0%B0%D1%87%D0%B8%D0%B2%D0%B0%D0%BD%D0%B8%D0%B9&color=brightgreen&cacheSeconds=86400
[donate-shield]: https://img.shields.io/badge/%D0%B4%D0%BE%D0%BD%D0%B0%D1%82-%D0%BD%D0%B0%20%D0%BA%D0%BE%D1%84%D0%B5-cc3336?style=flat-square&logo=coffeescript&labelColor=a67b5b
[donate-link]: https://mansmarthome.info/donate/#donationalerts
[donors-list]: https://github.com/user-attachments/assets/e0e85929-8608-4092-847a-33373f5070a4
