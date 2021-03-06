---
title: Установка и распространение приложений-шаблонов в вашей организации — Power BI
description: Сведения об установке, настройке и распространении в организации приложений-шаблонов Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 03/15/2020
ms.author: painbar
ms.openlocfilehash: 08aadc3027c5b265194e4239b150ea5d27fe2e43
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436118"
---
# <a name="install-and-distribute-template-apps-in-your-organization"></a>Установка и распространение приложений-шаблонов в организации

Являетесь ли вы аналитиком Power BI? Если это так, в этой статье вы узнаете, как установить [приложения-шаблоны](service-template-apps-overview.md) для подключения к различным службам, используемым для обеспечения работы вашей организации, таким как Salesforce, Microsoft Dynamics и Google Analytics. Можно изменять панели мониторинга и отчеты в приложениях-шаблонах в соответствии с потребностями своей организации, а затем распространить их в виде обычных [приложений](consumer/end-user-apps.md) среди коллег. 

![Установленные приложения Power BI](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Если вас интересует создание приложений-шаблонов самостоятельно для распространения за пределами организации, обратитесь к статье [Создание приложений-шаблонов в Power BI](service-template-apps-create.md). Используя минимальное количество кода (или вообще без него), партнеры Power BI могут создавать приложения Power BI и развертывать их для клиентов Power BI. 

## <a name="prerequisites"></a>Предварительные требования  

Для установки, настройки и распространения приложения-шаблона потребуется следующее. 

* [Лицензия Power BI Pro](service-self-service-signup-for-power-bi.md).
* Разрешения на установку приложений-шаблонов в клиенте.
* Действительная ссылка для установки приложения, полученная либо из AppSource, либо от создателя приложения.
* Хорошее знание [основных принципов Power BI](service-basic-concepts.md).

## <a name="install-a-template-app"></a>Установка приложения-шаблона

1. В службе Power BI в области навигации выберите **Приложения** > **Получить приложения**.

    ![Получить приложения](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

1. В появившемся окне AppSource выберите **Приложения**. Найдите приложение, а затем выберите **Получить**.

    ![Поиск в AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

1. В появившемся диалоговом окне выберите **Установить**.

    ![Установка приложения](media/service-template-apps-install-distribute/power-install-dialog.png)
    
    Приложение устанавливается вместе со связанной рабочей областью. **Если вы решили настроить приложение, это необходимо сделать в соответствующей рабочей области**.

    > [!NOTE]
    > При переходе по ссылке для установки приложения, отсутствующего в AppSource, появится диалоговое окно с просьбой подтвердить выбор.
    >
    >Чтобы установить приложение-шаблон, которое отсутствует в AppSource, необходимо обратиться к администратору с просьбой предоставить соответствующие разрешения. Дополнительные сведения см. в разделе [Параметры приложений-шаблонов](service-admin-portal.md#template-apps-settings) статьи, посвященной порталу администрирования Power BI.

    После успешной установки появится соответствующее уведомление о том, что новое приложение готово.

    ![Перейти к приложению](media/service-template-apps-install-distribute/power-bi-go-to-app.png)

## <a name="connect-to-data"></a>Подключение к данным

1. Выберите **Перейти к приложению**. Появится окно **Начало работы с новым приложением**.

   ![Начало работы с приложением](media/service-template-apps-install-distribute/power-bi-template-app-get-started.png)

1. Нажмите кнопку **Подключить**.
    
    Откроется диалоговое окно или серия диалоговых окон, в которых вы измените источник данных из образца данных на собственный источник данных. Обычно это подразумевает переопределение параметров набора данных и учетных данных источника. См. раздел [Известные ограничения](service-template-apps-tips.md#known-limitations).
    
    В примере ниже подключение к данным включает два диалоговых окна.

   ![Диалоговые окна подключения к источнику данных](media/service-template-apps-install-distribute/power-bi-template-app-connect-to-data-dialogs.png)

    По завершении ввода данных в диалоговых окнах подключения начинается процесс подключения. Баннер, который отображается сверху, информирует о том, что вы просматриваете демонстрационные данные.

    ![Просмотр демонстрационных данных](media/service-template-apps-install-distribute/power-bi-template-app-viewing-sample-data.png)

    Дождитесь завершения подключения и обновления данных. Для отслеживания процесса служит индикатор хода выполнения в строке набора данных (новое представление) или на вкладке (старое представление).

   Когда подключение и обновление данных завершены, обновите страницу в браузере. Теперь баннер информирует вас о том, что необходимо обновить приложение, чтобы применить внесенные в него изменения и предоставить к нему общий доступ.

    ![Настройка приложения и общий доступ к нему](media/service-template-apps-install-distribute/power-bi-template-app-customize-share.png)

## <a name="customize-and-share-the-app"></a>Настройка приложения и общий доступ к нему

После обновления браузера, подключения к данным и обновления данных отобразится рабочая область, связанная с приложением. На этом этапе можно изменить любой из артефактов — так же, как и в любой рабочей области. Однако помните, что любые внесенные изменения будут перезаписаны при обновлении приложения до новой версии, если не сохранить измененные элементы под разными именами. [Ознакомьтесь с дополнительными сведениями о перезаписи](#overwrite-behavior).

Сведения об изменении артефактов в рабочей области см. в следующих разделах.
* [Обзор редактора отчетов в Power BI](service-the-report-editor-take-a-tour.md)
* [Основные понятия для разработчиков в службе Power BI](service-basic-concepts.md)

После внесения изменений в артефакты в рабочей области можно приступать к публикации приложения и предоставлению общего доступа к нему. Сведения о том, как это сделать, см. в разделе [Публикация приложения](service-create-distribute-apps.md#publish-your-app).

## <a name="update-a-template-app"></a>Обновление приложения-шаблона

Время от времени авторы приложений-шаблонов выпускают новые улучшенные версии приложений-шаблонов, используя AppSource, прямые ссылки или и то и другое.

Если вы изначально загрузили приложение из AppSource, то при появлении новой версии приложения-шаблона в службе Power BI появится баннер с информацией о доступности новой версии приложения.

  ![Уведомление об обновлении приложения-шаблона](media/service-template-apps-install-distribute/power-bi-new-app-version-notification.png)

>[!NOTE]
>Если изначально приложение было получено посредством прямой ссылки, а не через AppSource, единственный способ узнать, имеется ли новая версия, это обратиться к создателю приложения-шаблона.

  Чтобы установить обновление, нажмите **Получить** в баннере с уведомлением или снова найдите приложение в AppSource и выберите **Получить**. Если вы получили прямую ссылку на обновление от создателя приложения-шаблона, просто щелкните ссылку.
  
  Будет предложено заменить текущую версию или установить новую версию в новой рабочей области. По умолчанию выбрана замена.

  ![Обновление приложения-шаблона](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Перезаписать существующую версию:** перезаписывает существующую рабочую область обновленной версией приложения-шаблона. [Ознакомьтесь с дополнительными сведениями о перезаписи](#overwrite-behavior).

- **Установить в новую рабочую область:** установка новой версии рабочей области и приложения, которые необходимо перенастроить (то есть подключиться к данным, определить навигацию и разрешения).

### <a name="overwrite-behavior"></a>Поведение при перезаписи

* При перезаписи обновляются отчеты, панели мониторинга и набор данных в рабочей области, а не в приложении. Перезапись не влияет на навигацию, установку и разрешение приложения.
* После обновления рабочей области необходимо **обновить приложение, чтобы применить изменения из рабочей области к приложению**.
* Перезапись сохраняет настроенные параметры и проверку подлинности. После обновления запускается автоматическое обновление набора данных. **Во время этого обновления в приложении, отчетах и на панели мониторинга представлены демонстрационные данные**.

  ![Образцы данных](media/service-template-apps-install-distribute/power-bi-sample-data.png)

* Перезапись всегда демонстрирует образцы данных до завершения обновления. Если автор приложения-шаблона внес изменения в набор данных или параметры, пользователи рабочей области и приложения смогут увидеть новые данные только после завершения обновления. Вместо этого для них по-прежнему будут отображаться демонстрационные данные.
* При перезаписи никогда не удаляются новые отчеты или панели мониторинга, добавленные в рабочую область. Исходные отчеты и панели мониторинга перезаписываются с учетом изменений, внесенных изначальным автором.

>[!IMPORTANT]
>Не забудьте [обновить приложение](#customize-and-share-the-app) после перезаписи, чтобы применить изменения к отчетам и панели мониторинга для пользователей приложения организации.

## <a name="next-steps"></a>Дальнейшие действия

[Создание рабочих областей вместе с коллегами в Power BI](service-create-workspaces.md)
