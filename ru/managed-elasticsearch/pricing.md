---
editable: false
---

# Правила тарификации для Managed Service for Elasticsearch

{% include [currency-choice](../_includes/pricing/currency-choice.md) %}


## Статус кластера {#running-stopped}

В зависимости от статуса кластера тарифы применяются различным образом:

* Для запущенного кластера (`Running`) тарифицируются как вычислительные ресурсы, так и объем хранилища.
* Для остановленного кластера (`Stopped`) тарифицируется только объем хранилища.

{% include [pricing-status-warning.md](../_includes/mdb/pricing-status-warning.md) %}


## Из чего складывается стоимость использования {{ mes-short-name }} {#rules}

Расчет стоимости использования {{ mes-name }} учитывает:

* используемую редакцию {{ ES }};

* вычислительные ресурсы, выделенные хостам кластера (в том числе хостам с ролью `Master node`);

* тип и объем хранилища (дискового пространства);

* объем исходящего трафика из {{ yandex-cloud }} в интернет.

{% include [pricing-gb-size](../_includes/pricing-gb-size.md) %}

### Использование хостов кластера {#rules-hosts-uptime}

Стоимость начисляется за каждый час работы хоста в соответствии с выделенными для него вычислительными ресурсами и используемой редакцией {{ ES }}. Поддерживаемые конфигурации ресурсов приведены в разделе [{#T}](concepts/instance-types.md), цены за использование vCPU и RAM — в разделе [Цены](#prices).

Вы можете выбрать класс хостов как для хостов с ролью `Data node`, так и для хостов с ролью `Master node`.

Минимальная единица тарификации — минута (например, стоимость 1,5 минут работы хоста равна стоимости 2 минут). Время, когда хост {{ ES }} не может выполнять свои основные функции, не тарифицируется.

### Использование дискового пространства {#rules-storage}

Оплачивается:

* Объем хранилища, выделенный для кластеров.

* Объем, занимаемый резервными копиями данных сверх заданного хранилища для кластера.

    * Хранение резервных копий не тарифицируется пока сумма размера данных в кластере и всех резервных копий остается меньше выбранного объема хранилища.

    * При автоматическом резервном копировании {{ mes-short-name }} не создает новую копию, а сохраняет изменения данных по сравнению с предыдущей копией. Поэтому потребление хранилища автоматическими резервными копиями растет только пропорционально объему изменений.

    * Количество хостов кластера не влияет на объем хранилища и, соответственно, на бесплатный объем резервных копий.

Цена указывается за 1 месяц использования. Минимальная единица тарификации — 1 ГБ в минуту (например, стоимость хранения 1 ГБ в течение 1,5 минут равна стоимости хранения в течение 2 минут).



## Цены {#prices}


{% include [disclaimer-new-prices](../_pricing/disclaimer-new-prices.md) %}


Все цены указаны с включением НДС.


{% include notitle [rub-hosts-and-storage.md](../_pricing/managed-elasticsearch/rub-hosts-and-storage.md) %}



### Исходящий трафик {#prices-traffic}


{% include notitle [rub-egress-traffic.md](../_pricing/rub-egress-traffic.md) %}



