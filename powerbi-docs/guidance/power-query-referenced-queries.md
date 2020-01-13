---
title: Ссылки на запросы Power Query
description: Использование ссылок на запросы Power Query
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: a0127a6ffa0d698a94e368532c44d0f83c362b42
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002404"
---
# <a name="referencing-power-query-queries"></a>Ссылки на запросы Power Query

В этой статье описаны средства моделирования данных, работающие с Power BI Desktop. Статья содержит рекомендации по определению запросов Power Query, ссылающихся на другие запросы.

Давайте попробуем понять, что это означает. _Когда один запрос ссылается на другой запрос, это аналогично тому, как если шаги во втором запросе объединяются и выполняются перед шагами в первом запросе._

Рассмотрим сценарий использования нескольких запросов. **Query1** получает данные из веб-службы, и их загрузка отключена. Все запросы **Query2**, **Query3** и **Query4** ссылаются на запрос **Query1**, и их выходные данные загружаются в модель данных.

![Представление зависимостей запросов с отображением запросов, описанных в предыдущем абзаце.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Считается, что при обновлении модели данных Power Query извлекает результат выполнения запроса **Query1**, повторно используемого другими запросами, на которые указывают ссылки. Но все происходит иначе. Фактически Power Query выполняет запросы **Query2**, **Query3** и **Query4** по-отдельности.

Иными словами, запрос **Query2** будет содержать все внедренные действия **Query1**. То же справедливо и для запросов **Query3** и **Query4**. Ниже представлена схема выполнения запросов.

![Измененная версия представления зависимостей запросов с отображением запросов Query2, Query3 и Query4. Каждый из трех запросов содержит внедренный запрос Query1.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

Запрос **Query1** выполняется три раза. Множественное выполнение может приводить к задержкам при обновлении данных и негативно влиять на их источник.

Использование функции [Table.Buffer](/powerquery-m/table-buffer) в запросе **Query1** не исключает избыточное получение данных. Эта функция позволяет поместить таблицу в память. После этого такую таблицу можно использовать при выполнении только одного запроса. Таким образом, если в нашем примере запрос **Query1** помещается в буфер при выполнении запроса **Query2**, буферизованные данные не будут использоваться при выполнении запросов **Query3** и **Query4**. Для этих запросов данные будут помещены в буфер дважды (в итоге такое поведение может негативно сказаться на производительности, так как таблица будет помещаться в буфер при выполнении каждого запроса со ссылкой).

> [!NOTE]
> Архитектура кэширования Power Query достаточно сложна. Она не описана в этой статье. Power Query может кэшировать данные, полученные из источника данных. Но при выполнении запроса данные могут извлекаться из источника данных более одного раза.

## <a name="recommendations"></a>Рекомендации

В целом мы рекомендуем использовать ссылочные запросы, чтобы избежать дублирования логики в запросах. Тем не менее, как описано в этой статье, такой подход к проектированию может привести к задержкам при обновлении данных и избыточной нагрузке на их источники.

Вместо этого рекомендуется создавать [потоки данных](../service-dataflows-overview.md). Использование потоков данных ускоряет обновление данных и минимизирует влияние на их источники,

а также позволяет инкапсулировать исходные данные и преобразования. Так как поток данных — это постоянное хранилище данных в службе Power BI. Поэтому их получение происходит быстро. Следовательно, даже при выполнении ссылочных запросов с множественным обращением к потоку данных обновление данных можно ускорить.

Если в нашем примере запрос **Query1** преобразовать в сущность потока данных, запросы **Query2**, **Query3** и **Query4** смогут обращаться к нему, как к источнику данных. При таком подходе сущность, источником которой является **Query1**, будет оцениваться только один раз.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения, связанные с темой этой статьи, см. в следующих ресурсах.

- [Самостоятельная подготовка данных в Power BI](../service-dataflows-overview.md)
- [Создание и использование потоков данных в Power BI](../service-dataflows-create-use.md)
- Видео на канале Guy in a Cube: [Inside Power Query reference queries for Power BI and Excel](https://www.youtube.com/watch?v=3uKNNZqBIkg) (Сведения о ссылочных запросах Power Query для Power BI и Excel)
- У вас появились вопросы? [Попробуйте задать вопрос в сообществе Power BI.](https://community.powerbi.com/)