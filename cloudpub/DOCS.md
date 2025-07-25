# Документация для аддона CloudPub

## Настройка

### Получение токена

Токен (API-ключ) можно получить в [панели управления CloudPub](https://cloudpub.ru/dashboard/) в разделе «Привяжите приложение к аккаунту». Вы можете скопировать как сам токен, так и всю команду `./clo set token <токен>` целиком.

### Конфигурация аддона

Для настройки аддона укажите следующие параметры:
- **Токен**: Ваш авторизационный токен CloudPub (или команда для установки токена).
- **Сервисы**: Список сервисов для публикации. Каждый сервис должен содержать:
  - **Тип**: Тип сервиса (например, `http`, `https`, `tcp`, `udp`, `rtsp`, `1c`).
  - **Локальный адрес**: Локальный адрес и порт сервиса (например, `homeassistant:8123`).
  - **Имя**: (Опционально) Имя сервиса для удобства.

Пример конфигурации аддона:

```yaml
token: 7Ml…Ly4 # или просто "./clo set token 7Ml…Ly4"
clo_log_level: info
services:
  - name: homeassistant
    type: http
    local_addr: homeassistant:8123
  - name: mqtt
    type: tcp
    local_addr: core-mosquitto:1883 # в примере используется порт без поддержки SSL
  - name: router
    type: http
    local_addr: 192.168.1.1:80 # IP-адрес и порт веб-интерфейса роутера может отличаться
```

> [!TIP]
> Если вы используете аддон CloudPub впервые, то лучше начать с минимальной конфигурации: оставьте только `homeassistant`.

### Конфигурация Home Assistant

Поскольку Home Assistant по умолчанию блокирует запросы от прокси-серверов, добавьте следующие строки в `configuration.yaml`, чтобы разрешить клиенту CloudPub доступ к вашему Home Assistant:

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.30.33.0/24
```

Файл `configuration.yaml` можно отредактировать через аддон File Editor (устанавливается в разделе [Настройки → Дополнения](https://my.home-assistant.io/create-link/?redirect=supervisor_store)). Если настройки `http` уже были указаны ранее, то просто добавьте в существующий блок параметры `use_x_forwarded_for` и `trusted_proxies`.

> [!NOTE]
> После изменения `configuration.yaml` перезапустите Home Assistant, чтобы применить настройки.

## Использование

После настройки ваш Home Assistant будет доступен через публичный URL, предоставленный CloudPub. Ссылка доступна в журнале аддона. Управление туннелями и просмотр статистики доступны через [веб-интерфейс CloudPub](https://cloudpub.ru/dashboard/).

## Решение проблем

Это неофициальное дополнение для CloudPub. Если вы столкнулись с проблемами при использовании аддона, попробуйте сначала выполнить рекомендации ниже:

### Ошибка `400: Bad Request`

#### Проблема с конфигурацией `trusted_proxies`

Если вы получаете ошибку `400: Bad Request` при попытке открыть ссылку в CloudPub, то возможно, не применилась конфигурация `trusted_proxies`. Убедитесь, что в `configuration.yaml` есть следующие строки:

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.30.33.0/24
```

После внесения изменений перезагрузите систему.

#### Отступы в YAML

Если ошибка сохраняется, убедитесь, что `configuration.yaml` правильно структурирован. Особенно важно следить за правильностью отступов в YAML. Для валидации конфига можно использовать:
- Встроенный валидатор Home Assistant (Панель разработчика → YAML → Проверить конфигурацию);
- [Онлайн-валидаторы YAML](https://yamllint.com/);
- [Studio Code Server](https://github.com/hassio-addons/addon-vscode) с плагинами для валидации YAML.

#### Дублирование блока `http`

Пожалуйста, просмотрите конфигурационные файлы Home Assistant:
- Найдите все вхождения `http:`;
- Если их несколько — объедините настройки в один блок;
- Удалите лишние объявления.

### Совместимость с Dataplicity

CloudPub можно использовать совместно с интеграцией Dataplicity. Для этого добавьте `127.0.0.1/32` в `trusted_proxies`:

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.30.33.0/24 # доступ для CloudPub и других аддонов
    - 127.0.0.1/32   # для Dataplicity
```

Гипотетически CloudPub и Dataplicity могут конфликтовать. Признаки проблем:
1. Ошибка `400: Bad Request` при обращении к Home Assistant через CloudPub;
2. Ошибка `Received X-Forwarded-For header from an untrusted proxy 172.30.33.x` в журналах.

При появлении таких ошибок рекомендуется удалить Dataplicity.

### Включите отладочные логи

Перед тем как обращаться за помощью, попробуйте включить отладочные логи в настройках аддона. Это может помочь быстрее выявить причину проблемы.

```yaml
clo_log_level: debug
```

После этого перезапустите аддон и проверьте логи в интерфейсе Home Assistant.

### Обратитесь за помощью

Если проблема не решена, вы можете:
- Задать вопрос в [Discussions на GitHub](https://github.com/black-roland/hassio-addon-cloudpub/discussions/new?category=support). Пожалуйста, приложите логи и описание проблемы.
- Задать вопрос в [Telegram-чате](https://t.me/mansmarthome/236).

Если вы столкнулись с техническими проблемами, связанными непосредственно с работой сервиса CloudPub (а не аддона), например:
- Недоступность серверов CloudPub;
- Вопросы по работе веб-интерфейса;
- Проблемы с аккаунтом.

Рекомендуем обратиться в [официальный чат технической поддержки CloudPub](https://t.me/cloudpub_support). Там вы сможете получить актуальную информацию о статусе работы сервиса и оперативную помощь по вопросам, связанным с платформой CloudPub.
