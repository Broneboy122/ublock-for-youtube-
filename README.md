# Вырезание Shorts и затягивающей ленты из YouTube с помощью uBlock


Набор пользовательских фильтров для полного удаления Shorts из YouTube.   
Решение работает на уровне браузера, не требует сторонних приложений.

---
## Что делает набор

- Полностью скрывает блок Shorts с главной страницы YouTube.
- Удаляет кнопку Shorts из бокового меню навигации.
- Блокирует превью Shorts в результатах поиска и правой колонке рекомендаций.
- Ломает механизм бесконечного свайпа при переходе по прямой ссылке (интерфейс плеера Shorts скрывается).
- Не затрагивает домены `googlevideo.com` и основной API плеера — совместимо с ByeDPI и другими DPI-обходчиками.

---
## Требования
### На ПК подходит любой браузер.
### На телефоне необходим браузер, поддерживающий расширения: 
##### На базе Chromium: 
- Microsoft Edge, Samsung Internet, Яндекс Браузер.
##### На базе Firefox:
- Firefox, WebLibre, Fennec, IronFox, Iceraven, Waterfox, Tor Browser

> Как оно там на устройствах яблок, понятия не имею.

> **Важно:** uBlock Origin Lite (версия для Chrome Web Store после перехода на Manifest V3) поддерживает только базовые фильтры. Для полной функциональности рекомендуется классический uBlock Origin, доступный для бразеров на базе Firefox.

---

## Установка

### Шаг 0. Удаление истории просмотров

| ![1](1.png) | ![2](2.png) |
|:---:|:---:|
| **Шаг 1. «Вы» → «История»** | **Шаг 2. «Очистить» и «Не сохранять»** |

> Необходимо для отключения функции рекомендаций видео. После этого на главном экране больше не будет ленты.


### Шаг 1. Установка uBlock

В завимости от ядра вашего браузера, установка осуществляется из магазина расширений [Chrome](https://chromewebstore.google.com/detail/ublock-origin-lite/ddkjiahejlhfcafbddmgiahcphecmpfh?hl=ru) или [Firefox](https://addons.mozilla.org/ru/firefox/addon/ublock-origin/) 

| ![1](4.png) | ![2](3.png) |
|:---:|:---:|
| **В браузерах на базе Chromium** | **В браузерах на базе Firefox** |

### Шаг 2. Перейдите на вкладку «Мои фильтры»
[1](moz-extension://eaf97506-d675-4287-b54f-7179122edbc9/dashboard.html#1p-filters.html)
В верхней части окна выберите вкладку **Мои фильтры**.

![Вкладка Мои фильтры](images/02-settings.png)

### Шаг 3. Очистите старые правила

Если у вас уже были пользовательские фильтры — выделите весь текст и удалите его. Это важно для предотвращения конфликтов.

### Шаг 4. Вставьте набор фильтров

Скопируйте содержимое файла [`filters.txt`](filters.txt) и вставьте его в поле «Мои фильтры».

![Поле ввода фильтров](images/03-my-filters.png)

### Шаг 5. Примените изменения

Нажмите кнопку **Применить изменения** в левом верхнем углу. Убедитесь, что счётчик ошибок в правом верхнем углу показывает **0**.

![Применение изменений](images/04-result.png)

### Шаг 6. Перезагрузите страницу

Обновите вкладку YouTube или ВКонтакте через `Ctrl+F5` (жёсткая перезагрузка с очисткой кэша).

---

## Содержимое filters.txt

Ниже — актуальная версия набора фильтров. Блок кода ниже автоматически имеет кнопку копирования в правом верхнем углу на странице GitHub.
```code
||youtube.com/youtubei/v1/reel/$xhr
||youtube.com/s/player/*/shorts_$script
||youtube.com/s/desktop/*/shorts_$script
www.youtube.com##ytd-rich-section-renderer
www.youtube.com##ytd-reel-shelf-renderer
www.youtube.com##ytd-shorts
www.youtube.com##ytd-reel-item-renderer
www.youtube.com##ytd-rich-item-renderer:has(a[href*="/shorts/"])
www.youtube.com##ytd-grid-video-renderer:has(a[href*="/shorts/"])
www.youtube.com##ytd-video-renderer:has(a[href*="/shorts/"])
www.youtube.com##ytd-compact-video-renderer:has(a[href*="/shorts/"])
www.youtube.com##ytd-rich-item-renderer:has(span:has-text(Shorts))
www.youtube.com##ytd-rich-item-renderer:has(span:has-text(Шортсы))
www.youtube.com##ytd-guide-entry-renderer:has-text(Shorts)
www.youtube.com##ytd-guide-entry-renderer:has-text(Шортсы)
www.youtube.com##ytd-guide-entry-renderer[title="Shorts"]
www.youtube.com##ytd-guide-entry-renderer[title="Шортсы"]
m.youtube.com##ytd-rich-section-renderer
m.youtube.com##ytd-reel-shelf-renderer
m.youtube.com##ytd-shorts
m.youtube.com##ytd-reel-item-renderer
m.youtube.com##ytd-rich-item-renderer:has(a[href*="/shorts/"])
m.youtube.com##ytd-compact-video-renderer:has(a[href*="/shorts/"])
m.youtube.com##ytm-reel-shelf-renderer
m.youtube.com##ytm-shorts
m.youtube.com##ytm-pivot-bar-item-renderer:has-text(Shorts)
m.youtube.com##ytm-pivot-bar-item-renderer:has-text(Шортсы)
m.youtube.com##a[href*="/shorts/"]
www.youtube.com##ytd-watch-next-secondary-results-renderer
www.youtube.com##ytd-secondary
m.youtube.com##ytd-watch-next-secondary-results-renderer
m.youtube.com##.full-bleed-wn-thumbs.watch-content > .single-column-watch-next-modern-panels.scwnr-content > lazy-list
www.youtube.com##ytd-mini-guide-entry-renderer.ytd-mini-guide-renderer.style-scope:nth-of-type(2)
```
