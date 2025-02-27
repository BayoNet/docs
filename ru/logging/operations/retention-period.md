# Изменение срока хранения записей

{% list tabs %}

- Консоль управления

    1. В [консоли управления]({{ link-console-main }}) перейдите в каталог, в котором находится [лог-группа](../concepts/log-group.md).
    1. Выберите сервис **{{ cloud-logging-name }}**.
    1. В строке с лог-группой нажмите значок ![image](../../_assets/horizontal-ellipsis.svg).
    1. В открывшемся меню нажмите кнопку **Редактировать**.
    1. Измените срок хранения записей в лог-группе. Максимальный срок хранения записей — 3 дня, минимальный — 1 день.
    1. Нажмите кнопку **Сохранить**.

- CLI

    {% include [cli-install](../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../_includes/default-catalogue.md) %}

    Для обращения к лог-группе используйте ее имя или уникальный идентификатор. Чтобы узнать их, [получите](./list.md) список лог-групп в каталоге.

    {% note info %}

    Срок хранения записей можно указать только в часах, минутах или секундах. Например, `1h` или `1440m`.

    {% endnote %}

    Чтобы изменить срок хранения записей в [лог-группе](../concepts/log-group.md), выполните команду:

    ```
    yc logging group update --name=default --retention-period=24h
    ```

    Где:
    * `--name` — имя лог-группы, срок хранения записей в которой вы хотите изменить.
    * `--retention-period` — новый срок хранения записей.

    Результат:

    ```
    id: af3mu6hnd0**********
    folder_id: aoek6qrs8t**********
    cloud_id: aoegtvhtp8**********
    created_at: "2021-06-22T09:51:43.614Z"
    name: default
    status: ACTIVE
    retention_period: 86400s
    ```

- API

    Изменить срок хранения записей в лог-группе можно с помощью метода API [update](../api-ref/LogGroup/update.md).

{% endlist %}
