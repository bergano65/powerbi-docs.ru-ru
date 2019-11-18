---
title: Подключение к журналам аудита Azure с помощью Power BI
description: Журналы аудита Azure для Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d0bd4e90dac6e71d95c38bed83f1c9507acc4fd3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855395"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Подключение к журналам аудита Azure с помощью Power BI
Пакет контента "Журналы аудита Azure" для Power BI позволяет анализировать и визуализировать информацию, хранящуюся в журналах аудита. Power BI извлекает данные, создает стандартную панель мониторинга и строит на основе этих данных отчеты.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Подключитесь к пакету содержимого журналов аудита Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) или прочтите дополнительные сведения об [интеграции журналов аудита Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) с Power BI.

## <a name="how-to-connect"></a>Способы подключения
1. В нижней части области навигации выберите **Получить данные**.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. В поле **Службы** выберите **Получить**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Выберите пункты **Журналы аудита Azure** > **Получить**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. При появлении запроса введите **идентификатор подписки Azure**. Сведения о том, как узнать свой [идентификатор подписки](#FindingParams), см. ниже.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. В качестве **метода проверки подлинности** выберите **oAuth2** \> **Войти**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Введите свои учетные данные для входа в учетную запись.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI извлечет данные журналов аудита Azure и создаст информационную панель и отчет, готовые к использованию. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Дальнейшие действия**

* Попробуйте [задать вопрос в поле "Вопросы и ответы"](consumer/end-user-q-and-a.md) в верхней части информационной панели.
* [Измените плитки](service-dashboard-edit-tile.md) на информационной панели.
* [Выберите плитку](consumer/end-user-tiles.md), чтобы открыть соответствующий отчет.
* Хотя набор данных будет обновляться ежедневно по расписанию, вы можете изменить график обновлений или попытаться выполнять обновления по запросу с помощью кнопки **Обновить сейчас**

## <a name="system-requirements"></a>Требования к системе
Пакету содержимого журналов аудита Azure требуется доступ к журналам аудита на портале Azure. Дополнительные сведения см. [здесь](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Поиск параметров
Вы можете определить свой идентификатор подписки одним из двух простых способов.

1. На сайте https://portal.azure.com -&gt; "Обзор" —&gt; "Подписки" —&gt; "Идентификатор подписки"
2. На сайте https://manage.windowsazure.com -&gt; "Параметры" —&gt; "Идентификатор подписки"

Идентификатор подписки представляет собой длинную последовательность цифр и букв, как в шаге \# 4 приведенного выше примера. 

## <a name="troubleshooting"></a>Устранение неполадок
Если возникает ошибка, указывающая на неправильные учетные данные, или ошибка обновления, указывающая на неправильные учетные данные, попробуйте удалить все экземпляры пакета содержимого журналов аудита Azure и повторите попытку подключения.

## <a name="next-steps"></a>Дальнейшие действия
[Что такое Power BI?](fundamentals/power-bi-overview.md)  
[Основные понятия для разработчиков в службе Power BI](service-basic-concepts.md)  

