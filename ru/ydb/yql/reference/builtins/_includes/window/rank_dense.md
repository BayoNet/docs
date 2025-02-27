---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/yql-core/builtins/_includes/window/rank_dense.md
sourcePath: ru/ydb/yql/reference/yql-core/builtins/_includes/window/rank_dense.md
---
## RANK / DENSE_RANK {#rank}

Пронумеровать группы соседних строк [раздела](../../../syntax/window.md#partition) с одинаковым значением выражения в аргументе. `DENSE_RANK` нумерует группы подряд, а `RANK` — пропускает `(N - 1)` значений, где `N` — число строк в предыдущей группе.

При отсутствии аргумента использует порядок, указанный в секции `ORDER BY` определения окна.
Если аргумент отсутствует и `ORDER BY` не указан, то все строки считаются равными друг другу.

{% note info %}

Возможность передавать аргумент в `RANK`/`DENSE_RANK` является нестандартным расширением YQL.

{% endnote %}

**Примеры**
``` yql
SELECT
   RANK(my_column) OVER w
FROM my_table
WINDOW w AS (ORDER BY key);
```
``` yql
SELECT
   RANK() OVER w
FROM my_table
WINDOW w AS (ORDER BY my_column);
