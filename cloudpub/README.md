# Home Assistant Add-on: CloudPub

![Последняя версия][latest-version-shield]
![Активных инсталляций][reported-installations-shield]
![Проект поддерживается?][maintenance-shield]

Этот аддон предоставляет внешний доступ к Home Assistant и другим локальным ресурсам за NAT без «белого» IP. Это неофициальное дополнение для сервиса [CloudPub](https://cloudpub.ru/), который является альтернативой KeenDNS, Dataplicity, Ngrok, Cloudflared и другим подобным сервисам.

## Ключевые особенности

- **Простота**. Достаточно скопировать токен из личного кабинета, вставить его в настройки аддона и нажать «Запустить». Через секунду ваш Home Assistant станет доступен из интернета по автогенерируемой ссылке.
- **Поддержка HTTPS**. Внешние ссылки используют HTTPS, а значит трафик до сервера CloudPub зашифрован.
- **Проксирование TCP и UDP**. Поддерживается не только HTTP, но и другие протоколы, включая RTSP для камер наблюдения.
- **Серверы в России**. Потенциально более высокая стабильность и производительность для пользователей из России.
- **Бесплатно для Home Assistant**. Для удаленного доступа к панели управления Home Assistant *не нужен PRO-тариф* — [достаточно бесплатного тарифа CloudPub](https://cloudpub.ru/plans/). PRO требуется для продвинутых функций: MQTT, RTSP, TCP/UDP и других не-HTTP протоколов.

<img src="https://github.com/user-attachments/assets/9aa52fe2-0fda-40ce-a15e-e4c7702c8c19" alt="Логи аддона" width="400" />
<img src="https://github.com/user-attachments/assets/32bddd8d-7986-4640-a0d7-66c7fcf50eeb" alt="Сервисы в CloudPub" width="400" />

## Установка

Для установки аддона добавьте репозиторий в Home Assistant. Вы можете сделать это вручную, указав ссылку на репозиторий (`https://github.com/black-roland/hassio-addon-cloudpub`), или нажав кнопку ниже:

[![Установить аддон в Home Assistant](https://my.home-assistant.io/badges/supervisor_addon.svg)](https://my.home-assistant.io/redirect/supervisor_addon/?repository_url=https%3A%2F%2Fgithub.com%2Fblack-roland%2Fhassio-addon-cloudpub&addon=6cd8d65a_cloudpub)

После добавления репозитория вы сможете установить дополнение в настройках Home Assistant.

## Настройка

Подробные инструкции по настройке и использованию аддона доступны в [DOCS.md](https://github.com/black-roland/hassio-addon-cloudpub/blob/master/cloudpub/DOCS.md).

### Быстрый старт

1. Установите аддон.
2. Настройте Home Assistant. Добавьте в `configuration.yaml`:
   ```yaml
   http:
     use_x_forwarded_for: true
     trusted_proxies:
       - 172.30.33.0/24
   ```
   Сохраните и **перезапустите** Home Assistant.
3. Получите ваш [ключ API в личном кабинете CloudPub](https://cloudpub.ru/dashboard/) и укажите его в [настройках аддона](https://my.home-assistant.io/redirect/supervisor_addon/?repository_url=https%3A%2F%2Fgithub.com%2Fblack-roland%2Fhassio-addon-cloudpub&addon=6cd8d65a_cloudpub) на вкладке «Конфигурация».
4. Запустите аддон и проверьте логи на наличие публичного URL.
5. Готово! Ваш HA теперь доступен из интернета.

## Получение помощи

Подробная документация по решению проблем доступна в [DOCS.md](https://github.com/black-roland/hassio-addon-cloudpub/blob/master/cloudpub/DOCS.md#%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BF%D1%80%D0%BE%D0%B1%D0%BB%D0%B5%D0%BC).

Куда обращаться за помощью:

- По вопросам работы аддона: задавайте вопросы в [**GitHub Discussions**](https://github.com/black-roland/hassio-addon-cloudpub/discussions). Велика вероятность, что на ваш вопрос уже есть ответ.
- По вопросам работы сервиса CloudPub (обрывы связи, серверы, аккаунт): обращайтесь в [**официальную поддержку CloudPub**](https://cloudpub.ru/dashboard/support/).

## Доступные версии

Аддон доступен в двух вариантах:

- **CloudPub Client** — стабильная версия. Скачивается из надёжного реестра контейнеров и устанавливается за несколько секунд.
- **CloudPub Client (Canary)** — тестовая версия. Устанавливается дольше и может упасть с ошибкой из-за блокировки GitHub Container Registry.

Рекомендуется использовать стабильную версию.

## Поддержка автора

Если этот аддон оказался полезным, вы можете [угостить автора чашечкой кофе](https://mansmarthome.info/donate/?utm_source=github&utm_medium=referral&utm_campaign=cloudpub#donationalerts). Ваша благодарность ценится!

#### Благодарности

Огромное спасибо всем, кто поддерживает этот проект:

<img src="https://github.com/user-attachments/assets/70724e4b-7a38-416c-b388-a4a92676fd46" align="top" alt="Спасибо" />
<img src="https://github.com/user-attachments/assets/c918ee7c-b323-4141-b524-87815ffe7365" align="top" alt="Спасибо" />

## Уведомление

Данный аддон является неофициальным и не связан с CloudPub. CloudPub — это сервис, предоставляемый его разработчиками.

Аддон не является официальным продуктом CloudPub и не поддерживается командой CloudPub. Ответственность за изменения в API CloudPub или возможное прекращение работы сервиса не лежит на разработчике аддона.

Информация о тарифах CloudPub предоставлена исключительно в справочных целях. Актуальные условия, цены и ограничения всегда доступны на официальном сайте [CloudPub](https://cloudpub.ru/plans/).

[latest-version-shield]: https://img.shields.io/github/package-json/v/black-roland/hassio-addon-cloudpub?filename=cloudpub%2Fconfig.json&style=flat-square&label=%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F&cacheSeconds=86400
[reported-installations-shield]: https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fanalytics.home-assistant.io%2Faddons.json&query=6cd8d65a_cloudpub.total&style=flat-square&label=%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D0%B5%D0%B9&color=brightgreen&cacheSeconds=86400
[maintenance-shield]: https://img.shields.io/maintenance/%D0%B4%D0%B0/2026?style=flat-square&label=%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%B8%D0%B2%D0%B0%D0%B5%D1%82%D1%81%D1%8F%3F
