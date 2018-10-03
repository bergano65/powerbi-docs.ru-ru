---
title: Экспорт данных из визуализации Power BI
description: Экспортируйте данные из визуализаций отчетов и панелей мониторинга и просматривайте их в Excel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8e5e2211af7dc53dba20a8d43c1083517b51bf17
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565988"
---
# <a name="export-data-from-visualizations"></a>Экспорт данных из визуализаций
Чтобы просмотреть данные, которые используются для создания визуализации, [откройте их в Power BI](end-user-show-data.md) или экспортируйте в Excel в виде файла с расширением XLSX или CSV.   

Просмотрите видео, в котором показан экспорт данных из визуализации в отчете и сохранение их в файл XLSX с последующим просмотром в Excel. Затем сделайте то же самое, выполнив пошаговые инструкции, приведенные под видео.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="from-a-visualization-on-a-power-bi-dashboard"></a>Экспорт из визуализации на панели мониторинга Power BI
1. Щелкните многоточие в правом верхнем углу визуализации.

    ![](media/end-user-export-data/pbi-export-tile3.png)
2. Выберите значок  **Экспорт данных** .

    ![](media/end-user-export-data/pbi_export_dash.png)
3. Данные экспортируются в файл CSV. Если визуальный элемент фильтруется, то скачанные данные также будут отфильтрованы.    
4. Браузер предложит сохранить файл.  Откройте сохраненный файл CSV в программе Excel.

    ![](media/end-user-export-data/pbi-export-to-excel.png)

## <a name="from-a-visualization-in-a-report"></a>Экспорт из визуализации в отчете
Для начала откройте [отчет по примеру анализа закупок](../sample-procurement.md) в [представлении редактирования](end-user-reading-view.md). [Добавьте новую пустую страницу отчета](../power-bi-report-add-page.md). Затем выполните следующие действия, чтобы добавить агрегирование и фильтры уровня визуализации.

1. Создайте гистограмму.  В области "Поля" выберите **Location > City** (Расположение > Город) и **Invoice > Discount Percent** (Счет > Процент скидки).  Возможно, нужно будет переместить **Процент скидки** в область "Значение". 

    ![](media/end-user-export-data/power-bi-export-data3.png)
2. Измените тип агрегации для **процента скидки** с **количества** на **среднее значение**. В области значений щелкните стрелку справа от параметра **Discount Percent** (Процент скидки) (он может называться **Count of Discount Percent** (Число процента скидки)) и выберите значение **Average** (Среднее значение).

    ![](media/end-user-export-data/power-bi-export-data6.png)
3. Добавьте фильтр для **города**, чтобы удалить **Атланту**.

   ![](media/end-user-export-data/power-bi-export-data4.png)

   Теперь можно попробовать оба варианта для экспорта данных. 

4. Щелкните многоточие в правом верхнем углу визуализации. Выберите  **Экспорт данных**.

   ![](media/end-user-export-data/power-bi-export-data2.png)
5. В веб-клиенте Power BI, если в визуализации есть статистическое выражение (например, если значение **количества** заменено на *среднее значение*, **сумму** или *минимальное значение*), вам доступно два варианта: **сводные данные** и **базовые данные**. В Power BI Desktop вам доступен только вариант **сводные данные**. Сведения о статистических выражениях см. в разделе [Статистические выражения в Power BI](../service-aggregates.md).

    ![](media/end-user-export-data/power-bi-export-data5.png)
6. Выберите **Сводные данные** > **Экспорт**, а затем выберите формат (XLSX или CSV). Power BI экспортирует данные.  Если к визуализации применялись фильтры, данные будут экспортированы с учетом фильтров. При выборе элемента **Экспорт** браузер предложит сохранить файл. Откройте сохраненный файл в программе Excel.

   **Сводные данные**: выберите этот вариант, если вы хотите экспортировать данные, которые отображаются в этом визуальном элементе.  Этот тип экспорта отображает только данные (столбцы и меры), которые вы выбрали для создания визуального элемента.  Если визуальный элемент содержит статистическое выражение, будут экспортированы объединенные данные. Например, если в гистограмме отображается 4 столбца, вы получите 4 строки данных. Сводные данные можно получить в формате XLSX и CSV.

   В этом примере в экспортированных данных Excel отображается итоговая сумма для каждого города. Так как мы отфильтровали Атланту, этого города нет в результатах.  В первой строке электронной таблицы отображаются фильтры, использованные при извлечении данных из Power BI.

   ![](media/end-user-export-data/power-bi-export-data7.png)
7. Теперь выберите **Базовые данные** > **Экспорт** и выберите формат XLSX. Power BI экспортирует данные. Если к визуализации применялись фильтры, экспортированные данные будут экспортированы с учетом фильтров. При выборе элемента **Экспорт** браузер предложит сохранить файл. Откройте сохраненный файл в программе Excel.

   >[!WARNING]
   >Экспорт базовых данных позволяет пользователям видеть все подробные сведения, включая каждый столбец в данных. Администраторы службы Power BI могут отключить этот параметр для своей организации. Если вы являетесь владельцем набора данных, определите собственные столбцы как скрытые, чтобы они не отображались в списке полей на рабочем столе или в службе Power BI.


   **Базовые данные**: выберите этот вариант, если вы хотите просмотреть данные в визуальном элементе ***и*** дополнительные данные из модели (дополнительные сведения см. в диаграмме ниже).  Если визуализация содержит статистическое выражение, при выборе варианта *Базовые данные* статистическое выражение удаляется. После нажатия кнопки **Экспортировать** данные экспортируются в файл XLSX и браузер предлагает сохранить этот файл. Откройте сохраненный файл в программе Excel.

   В этом примере в экспортированных данных Excel отображается по одной строке для каждой строки "Город" в наборе данных и процент скидки для одной записи. Другими словами, данные преобразованы в плоскую структуру без суммирования. В первой строке электронной таблицы отображаются фильтры, использованные при извлечении данных из Power BI.  

   ![](media/end-user-export-data/power-bi-export-data8.png)

## <a name="export-underlying-data-details"></a>Сведения об экспорте базовых данных
Данные, отображаемые при выборе варианта **Базовые данные**, могут различаться. Для понимания этих сведений может потребоваться помощь администратора или ИТ-отдела. В Power BI Desktop или в службе в представлении отчетов *мера* отображается в списке полей со значком калькулятора ![отображение значка](./media/end-user-export-data/power-bi-calculator-icon.png). Меры создаются в Power BI Desktop, а не в службе Power BI.


| Визуальный элемент содержит |                                                                              Что вы видите при экспорте                                                                              |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Статистические выражения    |                                                 *Первое* статистическое выражение и нескрытые данные из всей таблицы для этого статистического выражения                                                  |
|   Статистические выражения    | Связанные данные — если визуальный элемент использует данные из других таблиц данных, которые *\*\*связаны*\* с таблицей данных, содержащей статистическое выражение (если это связь типа \*: 1 или 1:1) |
|    Меры     |                                      Все меры в визуальном элементе *и* все меры из любой таблицы данных, содержащей меру, используемую в визуальном элементе                                      |
|    Меры     |                                       Все нескрытые данные из таблиц, содержащих эту меру (если это связь типа \*: 1 или 1:1)                                       |
|    Меры     |                                      Все данные из всех таблиц, связанных с таблицей, содержащей меры с помощью цепочки \*: 1 из 1:1                                      |
|  Только меры  |                                                   Все нескрытые столбцы из всех связанных таблиц (для расширения меры)                                                   |
|  Только меры  |                                                             Сводные данные для всех повторяющихся строк для мер модели.                                                              |

## <a name="limitations-and-considerations"></a>Рекомендации и ограничения
* Максимальное число строк, которые можно экспортировать из **Power BI Desktop** и **службы Power BI** в CSV-файл, — 30 000.
* Максимальное количество строк, которое можно экспортировать в XLSX-файл, — 150 000.
* Экспорт с помощью *базовых данных* не будет работать, если источником данных является динамическое соединение Analysis Services версии старше 2016 и если для таблиц в модели не существует уникального ключа.  
* Экспорт с помощью *базовых данных* не будет работать, если для экспортируемой визуализации используется параметр *Показать элементы без данных*.
* При использовании DirectQuery максимальный объем данных, который можно экспортировать, составляет 16 МБ. Это может привести к экспорту меньшего числа строк, чем максимальное, особенно если таблица содержит много столбцов либо данные, трудно поддающиеся сжатию, или есть другие факторы, увеличивающие размер файла и уменьшающие число экспортируемых строк.
* Если визуальный элемент использует данные из нескольких таблиц данных и для этих таблиц в модели данных не существует связей, экспортируются только данные для первой таблицы. 
* Пользовательские визуальные элементы и визуальные элементы R пока не поддерживаются.
* Экспорт данных недоступен для пользователей за пределами вашей организации, которые используют предоставленную им панель мониторинга. 
* В Power BI поле (столбец) можно переименовать, дважды щелкнув его и введя новое имя.  Новое имя называется *псевдонимом*. В отчете Power BI в итоге могут оказаться повторяющиеся имена полей, однако в Excel они запрещены.  Поэтому при экспорте данных в Excel псевдонимы заменяются исходными именами полей (столбцов).  
* Если в CSV-файле содержится знак Юникода, то текст в Excel может отображаться неправильно. Но при этом в блокноте все будет работать нормально. Примерами знаков Юникода являются символы валют и иностранные слова. Решением этой проблемы является импорт CSV-файла в Excel вместо открытия его напрямую. Для этого выполните следующие действия.

  1. Откройте Excel
  2. На вкладке **Данные** выберите **Получить внешние данные** > **Из текста**.
* Администраторы Power BI имеют возможность отключить экспорт данных.

## <a name="next-steps"></a>Дальнейшие действия
[Панели мониторинга в Power BI](end-user-dashboards.md)  
[Отчеты в Power BI](end-user-reports.md)  
[Power BI — основные понятия](end-user-basic-concepts.md)

Появились дополнительные вопросы? [Попробуйте задать вопрос в сообществе Power BI.](http://community.powerbi.com/)
