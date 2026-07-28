# Политика безопасности

## Сообщение об уязвимостях

Безопасность проекта является крайне важной. Если вы обнаружили уязвимость, пожалуйста, сообщите о ней конфиденциально, чтобы у меня было время на её устранение до того, как она станет общеизвестной.

**Пожалуйста, не создавайте публичные issues на GitHub для сообщений об уязвимостях.**

### Процесс сообщения

1. **Отправьте email** по адресу `security@roland.black`.
2. **Опишите проблему** как можно более подробно. Предпочтительно указать:
   - Тип уязвимости (например, XSS, утечка данных, RCE);
   - Полные шаги для воспроизведения проблемы;
   - Возможное воздействие (impact);
   - Любые идеи по исправлению или смягчению последствий.
3. **Вы получите ответ** в течение 72 часов с подтверждением получения и предварительной оценкой проблемы.
4. После оценки я сообщу о планируемых сроках исправления.
5. После устранения уязвимости я опубликую информацию о ней (advisory) и, при желании, с благодарностью укажу ваше имя.

Для конфиденциальных сообщений вы можете зашифровать письмо с помощью моего GPG-ключа (`91FB1459D08E67FE2C8E559274B3D86908C47BDF`):

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEZesUshYJKwYBBAHaRw8BAQdAnDJlQRn9YgRyCT3On0hGVtQXWNfbPc+I9WVJ
2nF3tDS0JEJsYWNrIFJvbGFuZCA8c2VjdXJpdHlAcm9sYW5kLmJsYWNrPoiZBBMW
CgBBFiEEkfsUWdCOZ/4sjlWSdLPYaQjEe98FAmpo2xcCGwMFCQz1nDwFCwkIBwIC
IgIGFQoJCAsCBBYCAwECHgcCF4AACgkQdLPYaQjEe98FSAEAwPq8Xf9XewI5xS47
ocxtw/JVZHLDvgiXD23RHkJSlUwBAMf3xM4nLJUZkFO1fPs7b5Yh/9L8AEXB7sZ7
/RmgHpwEtCBCbGFjayBSb2xhbmQgPG1haWxAcm9sYW5kLmJsYWNrPoicBBMWCgBE
AhsDBQsJCAcCAiICBhUKCQgLAgQWAgMBAh4HAheABQkM9Zw8FiEEkfsUWdCOZ/4s
jlWSdLPYaQjEe98FAmpo26QCGQEACgkQdLPYaQjEe9+k0gD/ZH6q15imj4m3klxA
o217bgmIM1V1fyzU/xHypLIuxOoBAIwjfd2jwMzQDaEze5+AZ312CG+rEAdH9gw0
MZSLcwcAtBdVQjBKQlggPG1haWxAdWIwamJ4LnJ1PoiZBBMWCgBBAhsDBQsJCAcC
AiICBhUKCQgLAgQWAgMBAh4HAheAFiEEkfsUWdCOZ/4sjlWSdLPYaQjEe98FAml6
r24FCQz1nDwACgkQdLPYaQjEe99YGAD+MObNABaVgufcpGfuR2dCa2j333l0+Gmk
I1EtYo+AeJAA/RTgmkycJ685fghCFjqw7DOPbUEvKNUbjk0YrtTmAVQLuDMEaXqy
CxYJKwYBBAHaRw8BAQdAm27auIiSQV4qhNVilJmxi30GzuTT9q2fBlfB9TCpWLSI
9QQYFgoAJhYhBJH7FFnQjmf+LI5VknSz2GkIxHvfBQJperILAhsCBQkDwmcAAIEJ
EHSz2GkIxHvfdiAEGRYKAB0WIQS9UMT2YgOKn1m2lY7eGm9lVL/agwUCaXqyCwAK
CRDeGm9lVL/ag1FvAP9s6FPi5wKrOYHzxridhlKNrdIuDuRCXvDNaDgJl6TnlgD/
eMgz3wlRn8twr23Svv25gYqsto/pZNEKodARJdgBVAS5XgEA3gJ6360rtjdtF/Mq
Pht+cq35OlY4uqqDcBF2VVQ7jKkA/3LXt88/5VUP7cqcTxEqRP50coa8CJ+iLol8
DOY93t0PuDgEajQRsxIKKwYBBAGXVQEFAQEHQIyPeGpqE6+qWvp5rE10a0mqhCLJ
/KI8EZy0p5/VihAbAwEIB4h+BBgWCgAmFiEEkfsUWdCOZ/4sjlWSdLPYaQjEe98F
Amo0EbMCGwwFCQPCZwAACgkQdLPYaQjEe99VlAEAqax3xp1Yj7LXN5nzpUemZkoS
BD0XuVURiBNfrlx1DTcA/3CFSyET/Ph7e5/VPVDaygkiEczBLi4bsb0RAe54CIcE
=YW9U
-----END PGP PUBLIC KEY BLOCK-----
```

Если у вас нет GPG, вы можете просто отправить письмо в открытом виде, но шифрование рекомендуется для особо чувствительной информации.

## Область действия (scope)

Данная политика безопасности относится **исключительно** к коду и контейнеру данного аддона (Home Assistant Add-on: CloudPub).

Проблемы в следующих компонентах должны быть сообщены **непосредственно их maintainers/разработчикам**:

- **Сервис CloudPub (клиент и инфраструктура)**: [cloudpub.ru/dashboard/support/](https://cloudpub.ru/dashboard/support/);
- **Home Assistant**: [www.home-assistant.io/security/](https://www.home-assistant.io/security/);
- **Базовый Docker-образ (`ghcr.io/hassio-addons/debian-base`)**: [github.com/hassio-addons/addon-debian-base](https://github.com/hassio-addons/addon-debian-base?tab=security-ov-file).
