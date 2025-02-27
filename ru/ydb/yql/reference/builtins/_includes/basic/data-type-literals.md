---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/yql-core/builtins/_includes/basic/data-type-literals.md
sourcePath: ru/ydb/yql/reference/yql-core/builtins/_includes/basic/data-type-literals.md
---
## Литералы простых типов {#data-type-literals}

Для простых типов могут быть созданы литералы на основании строковых литералов.

**Синтаксис**

<Простой тип>(<строка>[, <дополнительные атрибуты>])

В отличие от `CAST("myString" AS MyType)`:

* Проверка на приводимость литерала к требуемому типу происходит на этапе валидации;
* Результат не является optional.

Для типов данных `Date`, `Datetime`, `Timestamp` и `Interval` поддерживаются литералы только в формате, соответствующем [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601). У `Interval` есть следующие отличия от стандарта:

* поддерживается отрицательный знак для сдвигов в прошлое;
* микросекунды могут быть записаны как дробная часть секунд;
* единицы измерения больше недель не доступны;
* не поддерживаются варианты с началом/концом интервала, а также повторами.

Для типов данных `TzDate`, `TzDatetime`, `TzTimestamp` литералы также задаются в формате, соответствующем [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601), но вместо опционального суффикса Z через запятую указывается [IANA имя временной зоны](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones), например, GMT или Europe/Moscow.

{% include [decimal args](../../../_includes/decimal_args.md) %}

**Примеры**
``` yql
SELECT
  Bool("true"),
  Uint8("0"),
  Int32("-1"),
  Uint32("2"),
  Int64("-3"),
  Uint64("4"),
  Float("-5"),
  Double("6"),
  Decimal("1.23", 5, 2), -- до 5 десятичных знаков, из которых 2 после запятой
  String("foo"),
  Utf8("привет"),
  Yson("<a=1>[3;%false]"),
  Json(@@{"a":1,"b":null}@@),
  Date("2017-11-27"),
  Datetime("2017-11-27T13:24:00Z"),
  Timestamp("2017-11-27T13:24:00.123456Z"),
  Interval("P1DT2H3M4.567890S"),
  TzDate("2017-11-27,Europe/Moscow"),
  TzDatetime("2017-11-27T13:24:00,America/Los_Angeles"),
  TzTimestamp("2017-11-27T13:24:00.123456,GMT"),
  Uuid("f9d5cc3f-f1dc-4d9c-b97e-766e57ca4ccb");
```