# vuesp.DDS6619

Счётчик DDS6619: напряжение, ток, мощность и накопленная энергия.

Проект собран на базе шаблона [Vuesp](https://github.com/bondrogeen/vuesp): прошивка PlatformIO + web UI на Vue 3 и `vuesp-components`.

## Документация

Подробное описание платы, распиновка, схема, ScriptRunner и ограничения — в [DOCS.md](./DOCS.md).

## Особенности

- Modbus RTU по UART 9600 8N1: RX GPIO6, TX GPIO5.
- Напряжение, ток, мощность, частота и накопленная энергия.
- Проверка CRC16, опрос данных раз в 5 секунд, энергии — раз в минуту.

## Плата и окружение

- PlatformIO env: `esp32-c3-devkitm-1`
- Прошивка: `platformio.ini`
- Web UI: `vue/`
- Файловая система: LittleFS, веб-сборка попадает в `data/www`

## Сборка

```bash
cd vue
npm ci
npm run build-web
```

Полная сборка (web + прошивка):

```bash
cd vue
npm run build
```

Либо отдельно:

```bash
~/.platformio/penv/bin/pio run
~/.platformio/penv/bin/pio run -t buildfs
```

## Возможности

- локальный веб-интерфейс без облака;
- настройка Wi-Fi, безопасности, GPIO и файловой системы;
- dashboard с плитками устройств;
- сценарии и автоматизация;
- обновление прошивки и файловой системы через веб-интерфейс.

## CI

GitHub Actions собирает web UI, прошивку и LittleFS для указанных env, запускает тесты ScriptRunner и публикует артефакты в релиз при пуше тега.

## Репозиторий

<https://github.com/bondrogeen/vuesp.DDS6619>
