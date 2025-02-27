---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/yql-core/builtins/_includes/window/lag_lead.md
sourcePath: ru/ydb/yql/reference/yql-core/builtins/_includes/window/lag_lead.md
---
## LAG / LEAD {#lag-lead}

Доступ к значению из строки [раздела](../../../syntax/window.md#partition), отстающей (`LAG`) или опережающей (`LEAD`) текущую на фиксированное число. В первом аргументе указывается выражение, к которому необходим доступ, а во втором — отступ в строках. Отступ можно не указывать, по умолчанию используется соседняя строка — предыдущая или следующая, соответственно, то есть подразумевается 1. В строках, для которых нет соседей с заданным расстоянием (например `LAG(expr, 3)` в первой и второй строках раздела), возвращается `NULL`.

**Примеры**
``` yql
SELECT
   int_value - LAG(int_value) OVER w AS int_value_diff
FROM my_table
WINDOW w AS (ORDER BY key);
```
