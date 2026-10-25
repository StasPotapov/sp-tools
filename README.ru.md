# sp-tools

[Маркетплейс плагинов Claude Code](https://code.claude.com/docs/en/plugins/install) с моими
инструментами. Его подключают один раз, затем любой плагин из него ставят по имени.
[English version](README.md).

| Плагин | Что делает |
|---|---|
| [adbm](https://github.com/StasPotapov/adbm) | Агент управляет Android-устройствами и эмуляторами детерминированными командами вместо сырого adb и сравнивает экраны «до» и «после» |
| [present](https://github.com/StasPotapov/present) | Ведёт от идеи до офлайн-презентации в HTML: окно докладчика, прогон вслух, подгонка под время |
| [git-xfer](https://github.com/StasPotapov/git-xfer) | Переносит коммиты между двумя несвязанными git-репозиториями |

## Установка

В сессии Claude Code:

```
/plugin marketplace add StasPotapov/sp-tools
/plugin install adbm@sp-tools
```

Или из терминала:

```bash
claude plugin marketplace add StasPotapov/sp-tools
claude plugin install adbm@sp-tools
```

Что нужно на машине, написано в README каждого плагина. Например, adbm нужны `adb` и Pillow.

**Нет SSH-ключа для GitHub?** Claude Code клонирует по SSH, если работает `ssh -T git@github.com`.
Если ключа нет, задай в окружении `CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1`. Без этого установка
из `/plugin` и обновления падают.

## Обновления

Каждый плагин здесь указывает на тег релиза, например `v1.2.0`. Коммиты между релизами
к тебе не приходят.

- **Сами:** `/plugin` → **Marketplaces** → `sp-tools` → **Enable auto-update**. Тогда Claude Code
  проверяет новые релизы в фоне. Новая версия заработает после `/reload-plugins` или при следующем запуске.
- **Руками:** `/plugin marketplace update sp-tools`, затем `claude plugin update adbm@sp-tools` (в терминале).

## Переход с маркетплейса отдельного репозитория

Раньше каждый плагин был своим маркетплейсом (`adbm@adbm`, `present@present`, `git-xfer@git-xfer`).
Они работают и сейчас, но идут за веткой `main`, а не за релизами. Чтобы перейти:

```
/plugin uninstall adbm@adbm
/plugin marketplace remove adbm
/plugin install adbm@sp-tools
```

Обе установки сразу не держи: плагины с одним именем из двух маркетплейсов конфликтуют.

## Лицензия

Каталог — MIT. У каждого плагина своя лицензия в его репозитории.
