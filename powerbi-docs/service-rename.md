---
title: Переименование информационных панелей, отчетов, рабочих областей, страниц отчета, наборов данных
description: Переименование содержимого в службе Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: de842b95c8f6e023a5207c07abb2525c5fe45878
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2020
ms.locfileid: "73871711"
---
# <a name="rename-almost-anything-in-power-bi-service"></a>Переименование содержимого в службе Power BI
В этой статье показано, как изменить имя информационной панели, отчета, страницы отчета, книги, набора данных, приложения и рабочей области в службе Power BI.

**Кто может изменять имена**

| Тип содержимого | Автор или создатель | Мне предоставлен доступ |
| --- | --- | --- |
| Информационная панель в рабочей области |Да |Нет |
| Отчет в рабочей области |Да |Нет |
| Книга в рабочей области |Да |Нет |
| Набор данных в рабочей области |Да |Нет |
| Рабочая область |Да, если вы владелец или имеете разрешения администратора. |Нет |
| Опубликованные приложения |Не в приложении. Имя приложения можно изменить в рабочей области, а затем это приложение необходимо повторно опубликовать с новым именем, если у вас есть разрешения администратора. |Нет |
| Содержимое приложения (информационная панель, отчет, книга, набор данных) |Не в приложении. Содержимое приложения можно переименовать в рабочей области, а затем это приложение необходимо повторно опубликовать, если у вас есть разрешения администратора. |Нет |
| Содержимое на панели **Мне предоставлен доступ** |Нет |Нет |

## <a name="rename-a-dashboard-report-or-workbook"></a>Переименование информационной панели, отчета или книги
1. Запустите рабочую область и выберите вкладку **Информационные панели**, **Отчеты** или **Книги**. Наведите указатель мыши на элемент, имя которого необходимо изменить, и щелкните значок шестеренки ![значок шестеренки](media/service-rename/powerbi-cog-icon.png). Если значок шестеренки не отображается, у вас нет разрешений переименовывать.
   
   ![рабочая область службы Power BI](media/service-rename/power-bi-workspace-dashboards.png)
2. На странице "Параметры" введите новое имя и щелкните **Сохранить**.
   
   ![окно "Параметры" для набора данных](media/service-rename/power-bi-rename-dashboard2.png)

## <a name="rename-a-dataset"></a>Переименование набора данных
1. Запустите рабочую область и выберите вкладку **Наборы данных**.
   
   ![вкладка "Наборы данных" рабочей области](media/service-rename/power-bi-ellipses.png)
2. Наведите указатель мыши на элемент, имя которого необходимо изменить, щелкните **Дополнительные параметры** (...) и выберите команду **Переименовать**.  
   
      ![выбор команды "Переименовать"](media/service-rename/power-bi-rename-datasets.png)
   
   > [!NOTE]
   > Параметры в раскрывающемся списке могут отличаться.
   > 
   > 
3. На странице "Параметры" введите новое имя и щелкните **Сохранить**.
   
     ![область переименования](media/service-rename/power-bi-rename.png)

## <a name="rename-a-workspace"></a>Переименовать рабочую область
Любой пользователь с правами администратора может изменить имя рабочей области.

1. Войдите в рабочую область, имя которой требуется изменить.
2. В правом верхнем углу щелкните **Дополнительные параметры** (...) и выберите команду **Изменить рабочую область**. Если этот параметр не отображается, у вас нет разрешений переименовывать эту рабочую область. 
   
    ![выбор пункта "Изменить рабочую область"](media/service-rename/power-bi-edit-workspace.png)
3. Введите новое имя рабочей области и щелкните **Сохранить**.
   
   ![Область "Изменение рабочей области"](media/service-rename/power-bi-workspace-rename.png)

## <a name="rename-a-page-in-a-report"></a>Переименование страницы в отчете
Не нравится имя страницы в отчете Power BI?  Новое имя назначить очень просто. Имена страниц можно изменять в [режиме правки отчета](service-interact-with-a-report-in-editing-view.md).

1. Откройте отчет в [режиме редактирования](consumer/end-user-reading-view.md).
2. Найдите вкладки страницы отчета в нижней части окна Power BI.
   
    ![отчет с выделенными вкладками](media/service-rename/report-page-tabs-new.png)
3. Откройте страницу отчета, которую нужно переименовать. Для этого перейдите на соответствующую вкладку.
4. Дважды щелкните имя вкладки, чтобы выделить его.  
   
    ![имя вкладки крупным планом](media/service-rename/hilite-tab.png)
5. Введите новое имя страницы отчета и нажмите клавишу ВВОД.
   
    ![ввод нового имени страницы](media/service-rename/new-name.png)

## <a name="considerations-and-troubleshooting"></a>Рекомендации и устранение неполадок
* Если к элементу, который нужно переименовать, вам предоставили доступ или он входит в пакет содержимого, значок шестеренки отображаться не будет, и у вас не будет доступа к странице "Параметры".
* Если вы не видите **Дополнительные параметры** (...) на вкладке **Наборы данных**, разверните окно браузера.

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI.](https://community.powerbi.com/)

