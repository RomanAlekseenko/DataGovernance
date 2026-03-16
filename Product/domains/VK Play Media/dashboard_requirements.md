# Требования к дашбордам: VK Play Media

Связанные документы:
* [README домена](README.md)
* [План работ](to_do.md)
* [Вопросы к команде](questions_for_team.md)
* [Карта дашбордов](dashboard_map.md)

## Назначение документа
Документ фиксирует прикладные требования к дашбордам домена VK Play Media в формате:
* дашборд;
* виджет;
* метрика;
* источник;
* grain;
* owner;
* примечание.

Документ используется как рабочая спецификация для аналитиков, BI-команды и data engineering.

## Условные обозначения
* `grain` - минимальный уровень детализации, на котором должен быть доступен виджет.
* `owner` - основная роль, которая использует виджет как рабочий инструмент.

## 1. Executive Overview

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `VK Play Media Executive Overview` | Охват раздела | [Уникальные посетители](../../metrics/vk_play_media/аудиторные/уникальные_посетители.md) | `dds_mytracker/hits` | день | C-level | Показывать тренд и сравнение с прошлым периодом |
| `VK Play Media Executive Overview` | Охват чтения | [Уникальные читатели](../../metrics/vk_play_media/аудиторные/уникальные_читатели.md) | `dds_mytracker/hits` | день | C-level | Показывать рядом с посетителями |
| `VK Play Media Executive Overview` | Конверсия в чтение | [Доля читателей от посетителей](../../metrics/vk_play_media/аудиторные/доля_читателей_от_посетителей.md) | `dds_mytracker/hits` | день | C-level | Основной bridge между visitor и reader |
| `VK Play Media Executive Overview` | Объем потребления | [Просмотры материалов](../../metrics/vk_play_media/потребление_контента/просмотры_материалов.md) | `dds_mytracker/hits` | день | C-level | Без deep drill-down |
| `VK Play Media Executive Overview` | Качество чтения | [Доля дочитываний](../../metrics/vk_play_media/потребление_контента/доля_дочитываний.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день | C-level | Основная quality-метрика consumption |
| `VK Play Media Executive Overview` | Вовлеченность | [Engagement Rate](../../metrics/vk_play_media/вовлеченность/коэффициент_вовлеченности.md) | `dds_mytracker/custom_events` + `dds_mytracker/hits` | день | C-level | В агрегированном виде |
| `VK Play Media Executive Overview` | Продуктовое влияние | [Переходы в продуктовый контур из материала](../../metrics/vk_play_media/переходы_в_продуктовый_контур/переходы_в_продуктовый_контур_из_материала.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день | C-level | Абсолютное значение |
| `VK Play Media Executive Overview` | Конверсия в продукт | [CTR из материала в продуктовый контур](../../metrics/vk_play_media/эффективность_контента/ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день | C-level | Показывать рядом с переходами |
| `VK Play Media Executive Overview` | Session-level влияние | [Session CTR в продуктовый контур после посещения Media](../../metrics/vk_play_media/эффективность_контента/session_ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день | C-level | Не смешивать с material CTR |
| `VK Play Media Executive Overview` | Выпуск контента | [Опубликованные материалы](../../metrics/vk_play_media/контентное_производство/опубликованные_материалы.md) | CMS | день | C-level | После подтверждения полей CMS |
| `VK Play Media Executive Overview` | Вклад свежего контента | [Свежесть контента](../../metrics/vk_play_media/контентное_производство/свежесть_контента.md) | CMS + просмотры | день | C-level | После подтверждения даты первой публикации |

## 2. Product Dashboards

### 2.1 Audience Funnel

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Audience Funnel` | Все посетители | [Уникальные посетители](../../metrics/vk_play_media/аудиторные/уникальные_посетители.md) | `dds_mytracker/hits` | день | Product Manager | Основной верх воронки |
| `Audience Funnel` | Все читатели | [Уникальные читатели](../../metrics/vk_play_media/аудиторные/уникальные_читатели.md) | `dds_mytracker/hits` | день | Product Manager | Основной нижний шаг воронки чтения |
| `Audience Funnel` | Конверсия visit -> read | [Доля читателей от посетителей](../../metrics/vk_play_media/аудиторные/доля_читателей_от_посетителей.md) | `dds_mytracker/hits` | день | Product Manager | Основной funnel KPI |
| `Audience Funnel` | Новая visitor-аудитория | [Новые посетители](../../metrics/vk_play_media/аудиторные/новые_посетители.md) | `dds_mytracker/hits` | день | Product Manager | Анализировать вместе с новыми читателями |
| `Audience Funnel` | Новая reader-аудитория | [Новые читатели](../../metrics/vk_play_media/аудиторные/новые_читатели.md) | `dds_mytracker/hits` | день | Product Manager | |
| `Audience Funnel` | Доля новых читателей | [Доля новых читателей](../../metrics/vk_play_media/аудиторные/доля_новых_читателей.md) | `dds_mytracker/hits` | день | Product Manager | Структура reader-аудитории |
| `Audience Funnel` | Вернувшиеся посетители | [Вернувшиеся посетители](../../metrics/vk_play_media/аудиторные/вернувшиеся_посетители.md) | `dds_mytracker/hits` | день | Product Manager | |
| `Audience Funnel` | Вернувшиеся читатели | [Вернувшиеся читатели](../../metrics/vk_play_media/аудиторные/вернувшиеся_читатели.md) | `dds_mytracker/hits` | день | Product Manager | |
| `Audience Funnel` | Доля вернувшихся читателей | [Доля вернувшихся читателей](../../metrics/vk_play_media/аудиторные/доля_вернувшихся_читателей.md) | `dds_mytracker/hits` | день | Product Manager | Структура reader-аудитории |

### 2.2 Content Consumption

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Content Consumption` | Все просмотры | [Просмотры материалов](../../metrics/vk_play_media/потребление_контента/просмотры_материалов.md) | `dds_mytracker/hits` | день, материал | Product Manager | Базовый объем consumption |
| `Content Consumption` | Уникальный охват материалов | [Уникальные просмотры материалов](../../metrics/vk_play_media/потребление_контента/уникальные_просмотры_материалов.md) | `dds_mytracker/hits` | день, материал | Product Manager | |
| `Content Consumption` | Глубина на читателя | [Материалов на читателя](../../metrics/vk_play_media/потребление_контента/материалов_на_читателя.md) | `dds_mytracker/hits` | день | Product Manager | |
| `Content Consumption` | Абсолютные дочитывания | [Дочитывания](../../metrics/vk_play_media/потребление_контента/дочитывания.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | |
| `Content Consumption` | Доля дочитываний | [Доля дочитываний](../../metrics/vk_play_media/потребление_контента/доля_дочитываний.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, материал | Product Manager | Основной quality KPI |
| `Content Consumption` | Время чтения | [Среднее время чтения](../../metrics/vk_play_media/потребление_контента/среднее_время_чтения.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | Требует подтверждения active read rule |
| `Content Consumption` | Scroll depth | [Средняя глубина скролла](../../metrics/vk_play_media/вовлеченность/средняя_глубина_скролла.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | Использовать вместе с дочитываниями |

### 2.3 Engagement

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Engagement` | Лайки | [Лайки](../../metrics/vk_play_media/вовлеченность/лайки.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | |
| `Engagement` | Комментарии | [Комментарии](../../metrics/vk_play_media/вовлеченность/комментарии.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | |
| `Engagement` | Репосты | [Репосты](../../metrics/vk_play_media/вовлеченность/репосты.md) | `dds_mytracker/custom_events` | день, материал | Product Manager | |
| `Engagement` | Итоговая вовлеченность | [Engagement Rate](../../metrics/vk_play_media/вовлеченность/коэффициент_вовлеченности.md) | `dds_mytracker/custom_events` + `dds_mytracker/hits` | день, материал | Product Manager | Основной агрегированный KPI |

### 2.4 Conversion to Product

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Conversion to Product` | Переходы с кликом | [Переходы в продуктовый контур из материала](../../metrics/vk_play_media/переходы_в_продуктовый_контур/переходы_в_продуктовый_контур_из_материала.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт, материал | Product Manager | Основной click-confirmed KPI |
| `Conversion to Product` | Session-level переходы | [Переходы в продуктовый контур после посещения Media](../../metrics/vk_play_media/переходы_в_продуктовый_контур/переходы_в_продуктовый_контур_после_посещения_media.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт | Product Manager | Более широкий эффект |
| `Conversion to Product` | Material CTR | [CTR из материала в продуктовый контур](../../metrics/vk_play_media/эффективность_контента/ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт, материал | Product Manager | Не сравнивать напрямую с session CTR |
| `Conversion to Product` | Session CTR | [Session CTR в продуктовый контур после посещения Media](../../metrics/vk_play_media/эффективность_контента/session_ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт | Product Manager | Session-level знаменатель |

### 2.5 Content Performance

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Content Performance` | Просмотры на материал | [Просмотры на материал](../../metrics/vk_play_media/эффективность_контента/просмотры_на_материал.md) | просмотры + публикации | материал | Product Manager | Требует publication source для полноты |
| `Content Performance` | Лучшие категории | [Топ категорий](../../metrics/vk_play_media/эффективность_контента/топ_категорий.md) | составная витрина | категория | Product Manager | После подтверждения справочника категорий |
| `Content Performance` | Лучшие авторы | [Топ авторов](../../metrics/vk_play_media/эффективность_контента/топ_авторов.md) | составная витрина | автор | Product Manager | После подтверждения author source |
| `Content Performance` | Read quality по материалам | [Доля дочитываний](../../metrics/vk_play_media/потребление_контента/доля_дочитываний.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | материал | Product Manager | |
| `Content Performance` | Product conversion по материалам | [CTR из материала в продуктовый контур](../../metrics/vk_play_media/эффективность_контента/ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | материал | Product Manager | |

### 2.6 Publishing Control

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Publishing Control` | Объем выпуска | [Опубликованные материалы](../../metrics/vk_play_media/контентное_производство/опубликованные_материалы.md) | CMS | день | Product Manager / Editorial Lead | После подтверждения полей CMS |
| `Publishing Control` | Структура выпуска | [Материалы по категориям](../../metrics/vk_play_media/контентное_производство/материалы_по_категориям.md) | CMS | день, категория | Product Manager / Editorial Lead | После подтверждения категорийного справочника |
| `Publishing Control` | Вклад свежего контента | [Свежесть контента](../../metrics/vk_play_media/контентное_производство/свежесть_контента.md) | CMS + просмотры | день, категория | Product Manager / Editorial Lead | После подтверждения даты первой публикации |

### 2.7 Revenue Impact

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Revenue Impact` | Direct revenue from Media | [Выручка после переходов из Media](../../metrics/vk_play_media/выручка/выручка_после_переходов_из_media.md) | transactions + transitions | день, продукт, материал | Product Manager / Monetization | После подтверждения атрибуции |
| `Revenue Impact` | Paying users from Media | [Платящие пользователи после переходов из Media](../../metrics/vk_play_media/выручка/платящие_пользователи_после_переходов_из_media.md) | transactions + transitions | день, продукт | Product Manager / Monetization | |
| `Revenue Impact` | Purchase conversion | [Конверсия из перехода в покупку](../../metrics/vk_play_media/выручка/конверсия_из_перехода_в_покупку.md) | transactions + transitions | день, продукт, материал | Product Manager / Monetization | |
| `Revenue Impact` | Revenue per transition | [Средняя выручка на переход](../../metrics/vk_play_media/выручка/средняя_выручка_на_переход.md) | transactions + transitions | день, продукт, материал | Product Manager / Monetization | |
| `Revenue Impact` | Session-level revenue | [Выручка после посещения Media](../../metrics/vk_play_media/выручка/выручка_после_посещения_media.md) | transactions + visits | день, продукт | Product Manager / Monetization | Не смешивать с click-confirmed revenue |

## 3. Analyst Dashboards

### 3.1 Metric QA / Data Quality

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Metric QA / Data Quality` | Полнота hits | event volume | `dds_mytracker/hits` | день, час | Analyst / DE | Технический QA-виджет |
| `Metric QA / Data Quality` | Полнота custom events | event volume | `dds_mytracker/custom_events` | день, час | Analyst / DE | Технический QA-виджет |
| `Metric QA / Data Quality` | События без `device_id` | quality check | event logs | день | Analyst / DE | Не отдельная продуктовая метрика |
| `Metric QA / Data Quality` | События без `material_id` | quality check | event logs | день | Analyst / DE | Не отдельная продуктовая метрика |
| `Metric QA / Data Quality` | Связность аудиторных KPI | [Уникальные посетители](../../metrics/vk_play_media/аудиторные/уникальные_посетители.md), [Уникальные читатели](../../metrics/vk_play_media/аудиторные/уникальные_читатели.md) | `dds_mytracker/hits` | день | Analyst / DE | Проверка readers <= visitors |
| `Metric QA / Data Quality` | Связность consumption KPI | [Просмотры материалов](../../metrics/vk_play_media/потребление_контента/просмотры_материалов.md), [Уникальные просмотры материалов](../../metrics/vk_play_media/потребление_контента/уникальные_просмотры_материалов.md) | `dds_mytracker/hits` | день | Analyst / DE | Проверка unique views <= views |

### 3.2 Audience Diagnostics

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Audience Diagnostics` | Visitor trend | [Уникальные посетители](../../metrics/vk_play_media/аудиторные/уникальные_посетители.md) | `dds_mytracker/hits` | день | Analyst | |
| `Audience Diagnostics` | Reader trend | [Уникальные читатели](../../metrics/vk_play_media/аудиторные/уникальные_читатели.md) | `dds_mytracker/hits` | день | Analyst | |
| `Audience Diagnostics` | Conversion visit -> read | [Доля читателей от посетителей](../../metrics/vk_play_media/аудиторные/доля_читателей_от_посетителей.md) | `dds_mytracker/hits` | день, платформа, источник | Analyst | |
| `Audience Diagnostics` | New reader share | [Доля новых читателей](../../metrics/vk_play_media/аудиторные/доля_новых_читателей.md) | `dds_mytracker/hits` | день, платформа, источник | Analyst | |
| `Audience Diagnostics` | Returned reader share | [Доля вернувшихся читателей](../../metrics/vk_play_media/аудиторные/доля_вернувшихся_читателей.md) | `dds_mytracker/hits` | день, платформа, источник | Analyst | |

### 3.3 Material Diagnostics

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Material Diagnostics` | Таблица материалов | [Просмотры материалов](../../metrics/vk_play_media/потребление_контента/просмотры_материалов.md) | `dds_mytracker/hits` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [Уникальные просмотры материалов](../../metrics/vk_play_media/потребление_контента/уникальные_просмотры_материалов.md) | `dds_mytracker/hits` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [Дочитывания](../../metrics/vk_play_media/потребление_контента/дочитывания.md) | `dds_mytracker/custom_events` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [Доля дочитываний](../../metrics/vk_play_media/потребление_контента/доля_дочитываний.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [Среднее время чтения](../../metrics/vk_play_media/потребление_контента/среднее_время_чтения.md) | `dds_mytracker/custom_events` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [Engagement Rate](../../metrics/vk_play_media/вовлеченность/коэффициент_вовлеченности.md) | `dds_mytracker/custom_events` + `dds_mytracker/hits` | материал | Analyst | |
| `Material Diagnostics` | Таблица материалов | [CTR из материала в продуктовый контур](../../metrics/vk_play_media/эффективность_контента/ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | материал | Analyst | |

### 3.4 Transition Diagnostics

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Transition Diagnostics` | Click-confirmed transitions | [Переходы в продуктовый контур из материала](../../metrics/vk_play_media/переходы_в_продуктовый_контур/переходы_в_продуктовый_контур_из_материала.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, материал, продукт | Analyst | |
| `Transition Diagnostics` | Session transitions | [Переходы в продуктовый контур после посещения Media](../../metrics/vk_play_media/переходы_в_продуктовый_контур/переходы_в_продуктовый_контур_после_посещения_media.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт | Analyst | |
| `Transition Diagnostics` | Material CTR | [CTR из материала в продуктовый контур](../../metrics/vk_play_media/эффективность_контента/ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, материал, продукт | Analyst | |
| `Transition Diagnostics` | Session CTR | [Session CTR в продуктовый контур после посещения Media](../../metrics/vk_play_media/эффективность_контента/session_ctr_в_продуктовый_контур.md) | `dds_mytracker/hits` + `dds_mytracker/custom_events` | день, продукт | Analyst | |

### 3.5 Publishing Diagnostics

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Publishing Diagnostics` | Публикации по времени | [Опубликованные материалы](../../metrics/vk_play_media/контентное_производство/опубликованные_материалы.md) | CMS | день | Analyst / Editorial | После подтверждения полей CMS |
| `Publishing Diagnostics` | Публикации по категориям | [Материалы по категориям](../../metrics/vk_play_media/контентное_производство/материалы_по_категориям.md) | CMS | день, категория | Analyst / Editorial | После подтверждения категорийного справочника |
| `Publishing Diagnostics` | Вклад свежего контента | [Свежесть контента](../../metrics/vk_play_media/контентное_производство/свежесть_контента.md) | CMS + просмотры | день, категория | Analyst / Editorial | После подтверждения даты первой публикации |

### 3.6 Revenue Diagnostics

| Дашборд | Виджет | Метрика | Источник | Grain | Owner | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| `Revenue Diagnostics` | Revenue after click | [Выручка после переходов из Media](../../metrics/vk_play_media/выручка/выручка_после_переходов_из_media.md) | transactions + transitions | день, продукт, материал, transaction | Analyst | |
| `Revenue Diagnostics` | Revenue after visit | [Выручка после посещения Media](../../metrics/vk_play_media/выручка/выручка_после_посещения_media.md) | transactions + visits | день, продукт, session, transaction | Analyst | |
| `Revenue Diagnostics` | Paying users | [Платящие пользователи после переходов из Media](../../metrics/vk_play_media/выручка/платящие_пользователи_после_переходов_из_media.md) | transactions + transitions | день, продукт, user | Analyst | |
| `Revenue Diagnostics` | Purchase conversion | [Конверсия из перехода в покупку](../../metrics/vk_play_media/выручка/конверсия_из_перехода_в_покупку.md) | transactions + transitions | день, product, material | Analyst | |
| `Revenue Diagnostics` | Revenue per transition | [Средняя выручка на переход](../../metrics/vk_play_media/выручка/средняя_выручка_на_переход.md) | transactions + transitions | день, product, material | Analyst | |
| `Revenue Diagnostics` | Refund-adjusted diagnostics | refund-adjusted revenue | transactions | день, product, transaction | Analyst | Требует отдельного правила возвратов |

## Основные фильтры по умолчанию
Для управленческих дашбордов:
* период;
* платформа;
* категория;
* продукт, если дашборд связан с переходами или выручкой.

Для аналитических дашбордов:
* период;
* платформа;
* источник трафика;
* категория;
* автор;
* тип материала;
* материал;
* продукт.
* сценарий атрибуции, если дашборд связан с выручкой.

## Ограничения
TBD:
* часть виджетов publishing-контура останется проектной спецификацией до подтверждения полей CMS;
* отдельный video/stream-контур не включен в текущие требования;
* revenue-виджеты останутся проектной спецификацией до подтверждения транзакционного source of truth, user/session matching и правил возвратов;
* QA-виджеты опираются на технические проверки, а не на отдельные продуктовые метрики каталога.
