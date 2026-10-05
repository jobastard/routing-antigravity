# Google Antigravity

Официальный routing-пак для **Kagurabachi VPN** (Marketplace).

Направляет трафик **Google Antigravity** (IDE, CLI и Language Server) через ваш
VPN-сервер в регионе, где Antigravity доступен, не трогая остальной трафик —
в том числе вход в Google-аккаунт.

Это НЕ модификация самой IDE: binaries Antigravity остаются нетронутыми.
Пак работает поверх официального приложения и вашего сервера sing-box.

---

## Что маршрутизируется

| Сервис | Домены | Процессы |
| --- | --- | --- |
| **Antigravity API** | `cloudcode-pa.googleapis.com`, `daily-cloudcode-pa.googleapis.com` | `Antigravity.exe`, `language_server.exe`, `agy.exe` |
| **Сайт Antigravity** | `antigravity.google` | — |

- `cloudcode-pa.googleapis.com` — основной API агентов и моделей (именно его
  проверяет региональный гейт Antigravity).
- `daily-cloudcode-pa.googleapis.com` — daily/staging-канал API.
- Процессы покрывают весь трафик IDE, включая серверы артефактов, если он
  пойдёт мимо перечисленных доменов.
- `accounts.google.com` и прочие сервисы Google **намеренно не
  маршрутизируются** — вход и обычные сайты работают напрямую.

---

## Установка

1. Откройте Kagurabachi VPN → **Маркет**
2. Найдите пак **Google Antigravity** (`routing-antigravity`)
3. Установите и **включите** пак
4. Выберите сервер в стране, где Antigravity доступен (США, Европа, Япония…)
5. Переведите туннель в режим **Выкл** — правила плагинов применяются
   именно в этом режиме, поверх системного прокси
6. Включите набор **Google Antigravity** в разделе маршрутизации
7. Запустите Antigravity и войдите в аккаунт

Альтернатива: скачайте `routing-antigravity.zip` из
[Releases](https://github.com/jobastard/routing-antigravity/releases)
и установите вручную.

---

## Важно

- **Нужен сервер в поддерживаемом регионе.** Пак лишь направляет трафик
  Antigravity через ваш активный сервер sing-box; сам по себе он регион
  не меняет. Если ограничение завязано на страну Google-аккаунта, а не на
  IP, пак не поможет — это ограничение на стороне Google.
- Аккаунт Google, который вы используете, остаётся под вашими рисками:
  использование Antigravity из неподдерживаемого региона противоречит
  условиям сервиса Google.
- Вход в Google (`accounts.google.com`) идёт напрямую, поэтому пак не
  перехватывает и не видит ваш пароль или токены.

---

## Файлы пака

```
manifest.json   # id, version, capability: routing
routing.json    # services + bundles
README.md       # эта страница
```

Только данные. Исполняемого кода в пакете нет.

## Лицензия и доверие

Официальный пак аккаунта `jobastard`. Устанавливайте через Маркет клиента —
проверяются URL релиза и SHA-256 архива.
