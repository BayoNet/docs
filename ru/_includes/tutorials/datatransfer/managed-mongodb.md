# Перенос данных с использованием сервиса {{ data-transfer-full-name }} {#data-transfer}

1. [Подготовьте кластер-источник](../../../data-transfer/operations/prepare.md#source-mg).
1. [Подготовьте кластер-приемник](../../../data-transfer/operations/prepare.md#target-mg).
1. [Создайте эндпоинт для источника](../../../data-transfer/operations/endpoint/index.md#create) со следующими параметрами:

    * **Тип базы данных** — `MongoDB`.
    * **Параметры эндпоинта** → **Настройки подключения** — `Пользовательская инсталляция`.
        Укажите параметры подключения к кластеру-источнику.

1. [Создайте эндпоинт для приемника](../../../data-transfer/operations/endpoint/index.md#create) со следующими параметрами:

    * **Тип базы данных** — `MongoDB`.
    * **Параметры эндпоинта** → **Настройки подключения** — `Кластер MDB`.
        Укажите идентификатор кластера-приемника.

1. [Создайте трансфер](../../../data-transfer/operations/transfer.md#create) типа _{{ dt-type-copy-repl }}_, использующий созданные эндпоинты.
1. [Активируйте](../../../data-transfer/operations/transfer.md#activate) его.
1. Дождитесь перехода трансфера в статус `Реплицируется`.
1. Переведите кластер-источник в режим <q>только чтение</q> и переключите нагрузку на кластер-приемник.
1. На странице [мониторинга трансфера](../../../data-transfer/operations/monitoring.md) дождитесь снижения до нуля характеристики **Maximum lag on delivery**. Это значит, что на кластер-приемник перенесены все изменения, произошедшие в кластере-источнике после завершения копирования данных.
1. [Деактивируйте](../../../data-transfer/operations/transfer.md#deactivate) трансфер и дождитесь его перехода в статус `Остановлен`.

    Подробнее о жизненном цикле трансфера см. в [соответствующем разделе](../../../data-transfer/concepts/transfer-lifecycle.md).

1. [Удалите](../../../data-transfer/operations/transfer.md#delete) остановленный трансфер.
1. [Удалите эндпоинты](../../../data-transfer/operations/endpoint/index.md#delete) для источника и приемника.
