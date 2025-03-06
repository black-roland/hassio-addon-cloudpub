# Home Assistant Add-on: CloudPub

Этот аддон предоставляет внешний доступ к Home Assistant и другим локальным ресурсам за NAT без «белого» IP. Это неофициальное дополнение для сервиса [CloudPub](https://cloudpub.ru/), который является альтернативой KeenDNS, Dataplicity, Ngrok, Cloudflared и другим подобным сервисам.

## Ключевые особенности

- **Простая настройка**: Скопируйте токен из личного кабинета CloudPub, вставьте его в настройки аддона и нажмите «Запустить». Через секунду ваш Home Assistant станет доступен из интернета по уникальной ссылке, сгенерированной CloudPub.
- **Поддержка HTTPS**: При использовании HTTPS администрация CloudPub не имеет доступа к проксируемому трафику. Хотя по умолчанию аддон использует HTTP для простоты.
- **Проксирование TCP и UDP портов**: Поддержка не только HTTP/HTTPS, но и других протоколов, включая RTSP с камер видеонаблюдения.
- **Серверы в России**: Потенциально более высокая стабильность и производительность для пользователей из России.

<img src="https://github.com/user-attachments/assets/9aa52fe2-0fda-40ce-a15e-e4c7702c8c19" alt="Логи аддона" height="400" />
<img src="https://github.com/user-attachments/assets/32bddd8d-7986-4640-a0d7-66c7fcf50eeb" alt="Сервисы в CloudPub" height="400" />

## Установка

Для установки аддона добавьте репозиторий в Home Assistant. Вы можете сделать это вручную, указав ссылку на репозиторий (`https://github.com/black-roland/hassio-addon-cloudpub`), или нажав кнопку ниже:

[![Добавить репозиторий в Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fblack-roland%2Fhassio-addon-cloudpub)

После добавления репозитория вы сможете установить дополнение в настройках Home Assistant.

## Настройка

### Получение токена

Токен можно получить в [панели управления CloudPub](https://cloudpub.ru/dashboard/). Скопируйте только сам токен, без команды `./clo set token ` в начале.

### Конфигурация аддона

Для настройки аддона укажите следующие параметры:

- **Токен**: Ваш авторизационный токен CloudPub.
- **Сервисы**: Список сервисов для публикации. Каждый сервис должен содержать:
  - **Тип**: Тип сервиса (например, `http`, `https`, `tcp`, `udp`, `rtsp`).
  - **Локальный адрес**: Локальный адрес и порт сервиса (например, `homeassistant:8123`).
  - **Имя**: (Опционально) Имя сервиса для удобства.

Пример конфигурации:

```yaml
token: "ваш_токен_здесь"
services:
  - type: http
    local_addr: homeassistant:8123
    name: homeassistant
```

### Конфигурация Home Assistant

Поскольку Home Assistant по умолчанию блокирует запросы от прокси-серверов, добавьте следующие строки в `configuration.yaml`, чтобы разрешить клиенту CloudPub доступ к вашему Home Assistant:

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.30.33.0/24
```

Это позволит Home Assistant корректно обрабатывать запросы, проходящие через CloudPub.

## Использование

После настройки ваш Home Assistant будет доступен через публичный URL, предоставленный CloudPub. Ссылка доступна в журнале аддона. Управление туннелями и просмотр статистики доступны через [веб-интерфейс CloudPub](https://cloudpub.ru/dashboard/).

## Поддержка автора

Если этот аддон оказался полезным, вы можете [угостить автора чашечкой кофе](https://mansmarthome.info/donate/#donationalerts). Ваша благодарность ценится!

#### Благодарности

Список донатеров пока пуст, но я буду рад добавить ваше имя сюда! 😊
