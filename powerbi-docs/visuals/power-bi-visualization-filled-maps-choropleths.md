---
title: Картограммы (хороплеты) в Power BI
description: Документация по созданию картограмм (хороплетов) в Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/05/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a2ac2820c7beb3a82650716896ddd36b79c82e07
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436072"
---
# <a name="create-and-use-filled-maps-choropleth-maps-in-power-bi"></a>Создание и использование картограмм (хороплетов) в Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Картограмма с помощью заливки, оттенков или шаблонов показывает, как изменяется исследуемое значение по географическим регионам.  Картограмма позволяет быстро отобразить относительные различия с помощью заливки, которая изменяется от светлой (меньше, встречается с меньшей частотой) до темной (больше, встречается с большей частотой).    

![Карта США](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>Какие данные отправляются в Bing
Power BI интегрируется с Bing для предоставления картографических координат по умолчанию (этот процесс называется геокодированием). При создании визуализации карты в службе Power BI или Power BI Desktop данные в контейнерах **Расположение**, **Широта** и **Долгота**, используемых для создания визуального элемента, отправляются в Bing.

Вам или администратору может потребоваться обновить брандмауэр, чтобы разрешить доступ к URL-адресам, которые Bing использует для геокодирования.  Ниже приведены эти URL-адреса:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Дополнительные сведения о данных, отправляемых в Bing, а также подсказки по геокодированию см. в статье [Советы и рекомендации для визуализаций карт Power BI](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Когда следует использовать картограмму
Картограмма отлично подходит:

* для отображения на карте количественной информации;
* для отображения пространственных шаблонов и связей;
* для стандартизированных данных;
* при работе с социально-экономическими данными;
* когда некоторые регионы особо важны;
* для получения представления о географическом распределении величины.

### <a name="prerequisites"></a>Предварительные требования
В этом руководстве используется [PBIX-файл с образцом "Продажи и маркетинг"](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. В левом верхнем разделе строки меню выберите **Файл**  > **Открыть**.
   
2. Найдите свою копию **PBIX-файла "Продажи и маркетинг"** .

1. Откройте PBIX-файл **Продажи и маркетинг** в представлении отчета ![Снимок экрана: значок представления отчета](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Выбрать ![Снимок экрана: желтая вкладка,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) чтобы создать новую страницу.


## <a name="create-a-basic-filled-map"></a>Создание базовой картограммы
В этом видео Ким создает простую карту и преобразовывает ее в картограмму.
   > [!NOTE]
   > В этом видео показано использование более старой версии Power BI Desktop.
   > 
   > 

> [ВИДЕО https://www.youtube.com/embed/ajTPGNpthcg ]

### <a name="create-a-filled-map"></a>Создание картограммы
1. На панели "Поля" выберите поле **Геообъект** \> **Состояние**.    

   ![желтый флажок рядом со штатом](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Преобразуйте диаграмму](power-bi-report-change-visualization-type.md) в картограмму. Обратите внимание, что теперь поле **State** находится в разделе **Расположение**. Для создания картограммы служба "Карты Bing" использует поле в разделе **Расположение**.  Расположениями могут быть страны, округа, области, города, почтовые индексы и т. д. Служба "Карты Bing" предоставляет фигуры заполнения карт для работы с расположениями по всему миру. Без допустимых данных в разделе "Расположение" Power BI не может создать картограмму.  

   ![шаблоны с выделенным значком для заполненной картограммы](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Выполните фильтрацию карты, чтобы отображалась только континентальная часть США.

   а.  Слева от области визуализаций найдите область **Фильтры**. Разверните эту область, если она свернута.

   б.  Наведите указатель мыши на значение **State** (Штат) и выберите значок развертывания.  
   ![Фильтры уровня визуальных элементов: показано State(All)](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   в.  Установите флажок рядом с **Все** и снимите флажок рядом с **AK**(Аляска).

   ![Раскрывающийся список штатов: All и AK не выбраны](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Откройте панель форматирования, щелкнув значок валика, и выберите **Цвета данных**.

    ![Панель форматирования с пунктом меню "Цвета данных"](media/power-bi-visualization-filled-maps-choropleths/power-bi-colors-data.png)

5. Щелкните три вертикальные точки и выберите **Условное форматирование**.

    ![Кнопка условного форматирования цветов данных](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional.png)

6. Воспользуйтесь экраном **"Цвет по умолчанию" — "Цвета данных"** , чтобы определить, какие оттенки будут применяться к картограмме. Вы можете выбрать, какое поле станет основой для оттенка и как необходимо применить оттенок. В этом примере мы используем поле **SalesFact** > **Sentiment** и установим для самого низкого значения тональности оранжевый цвет, а для самого высокого — синий. Значения между максимальным и минимальным будут иметь оттенки оранжевого и синего цветов. На рисунке в нижней части экрана показан диапазон цветов, которые будут использоваться. 

    ![Панель цвета по умолчанию с выбранным полем Sentiment](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-field.png)

7. Для картограммы используется зеленый и красный цвет заливки: красный представляет слабо-позитивное настроение, а темно-зеленый — крайне позитивное.  Для отображения дополнительных сведений перетащите поле в раздел "Подсказки".  В этом случае мы добавили поле **SalesFact** > **Sentiment gap** (Разрыв в настроениях). При выделении штата Айдахо (код штата — ID) видно, что разрыв невелик и равен 6.
   ![Картограмма с подсказками для штата Айдахо](media/power-bi-visualization-filled-maps-choropleths/power-bi-idaho-filled-map.png)

10. [Сохраните отчет](../service-report-save.md).

Power BI позволяет контролировать внешний вид картограммы. Поэкспериментируйте с этими элементами управления данными до получения желаемого эффекта. 

## <a name="highlighting-and-cross-filtering"></a>Выделение и перекрестная фильтрация
Сведения об использовании области "Фильтры" см. в разделе [Добавление фильтра в отчет](../power-bi-report-add-filter.md).

При выделении определенного места на картограмме выполняется фильтрация других визуализаций на странице отчета и наоборот.

1. Чтобы продолжить, сначала сохраните этот отчет, выбрав **Файл > Сохранить**. 

2. Скопируйте картограмму с помощью клавиш CTRL+C.

3. Чтобы открыть страницу отчета тональности, выберите вкладку **Тональности** в нижней части отчета холста.

    ![Выбрана вкладка тональности](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Перемещайте и изменяйте размеры визуализаций на странице, чтобы освободить место, затем с помощью клавиш CTRL+V вставьте картограмму из предыдущего отчета. (См. следующие изображения.)

   ![Картограмма добавлена ​​на страницу тональности](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Выберите штат на картограмме.  Это приведет к перекрестному выделению и перекрестной фильтрации других визуализаций на странице. Например, при выборе **Texas** (Техас) выполняется перекрестная фильтрация карточек и перекрестное выделение линейчатой диаграммы. В результате видно, что значение тональности — 75, а Техас находится в центральном округе № 23.   
   ![Выбран Техас](media/power-bi-visualization-filled-maps-choropleths/power-bi-filter.png)
2. Выберите точку данных на графике Тональности в компании VanArsdel по месяцам. Это отфильтрует картограмму, чтобы показать данные о тональностях для VanArsdel, а не их конкуренцию.  
   ![новая заливка](media/power-bi-visualization-filled-maps-choropleths/power-bi-vanarsdel.png)

## <a name="considerations-and-troubleshooting"></a>Рекомендации и устранение неполадок
Данные карты могут быть неоднозначными.  Например, город с названием Париж есть во Франции и в Техасе. Географические данные, вероятно, хранятся в отдельных столбцах — столбец для названий городов, столбец для названий штатов или областей и т. д., — поэтому служба "Карты Bing" не может определить, о каком Париже идет речь. Если набор данных содержит сведения о широте и долготе, в Power BI можно воспользоваться специальными полями, которые помогают сделать данные карты однозначными. Просто перетащите поле, содержащее сведения о широте, в область "Визуализации" \> "Широта".  Сделайте то же самое для сведений о долготе.    

![Панели "Поля" и "Визуализации".](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

При наличии разрешений на изменение набора данных в Power BI Desktop просмотрите это видео, чтобы понять, как устранить неоднозначность карты.

> [ВИДЕО https://www.youtube.com/embed/Co2z9b-s_yM ]

Если доступа к сведениям о широте и долготе нет, но есть доступ на редактирование для набора данных, [выполните эти действия для обновления набора данных](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Дополнительные сведения о визуализации карт см. в разделе [Tips and tricks for map visualizations](../power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Дальнейшие действия

[Сопоставление фигур](desktop-shape-map.md)

[Типы визуализаций в Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
