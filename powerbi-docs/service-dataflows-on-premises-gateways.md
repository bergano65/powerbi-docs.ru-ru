---
title: Использование потоков данных с локальными источниками данных
description: Сведения об использовании локальных данных в потоках данных
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: efd110ad73b1bd72813d418a1f641613c88dc0d5
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762584"
---
# <a name="using-dataflows-with-on-premises-data-sources"></a>Использование потоков данных с локальными источниками данных

С помощью **потоков данных** можно создать коллекцию данных из разных источников, очистить и преобразовать эти данные, а затем загрузить их в хранилище Power BI. При создании потока данных вы можете использовать локальные источники данных. В этой статье разъясняются требования, связанные с созданием потоков данных, и настройки **корпоративного шлюза** для использования таких подключений.

![Потоки данных и шлюзы](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Настройка корпоративного шлюза для использования с потоками данных

Чтобы создать поток данных с помощью шлюза, пользователь должен иметь права администратора корпоративного шлюза либо администратор должен предоставить общий доступ к источнику данных, который планируется использовать. 


> [!NOTE]
> Потоки данных можно использовать только через корпоративные шлюзы.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Использование локального источника данных в потоке данных

При создании потока данных выберите локальный источник данных из списка источников данных, как показано на следующем изображении.

![Выбор локального источника данных](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Выбрав источник данных, вы получите предложение ввести сведения о подключении к корпоративному шлюзу, который будет использоваться для доступа к локальным данным. Здесь следует выбрать нужный шлюз и указать учетные данные для него.

![Ввод сведений о подключении](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Мониторинг шлюза

Корпоративные шлюзы для потока данных можно отслеживать так же, как шлюзы для набора данных.

На экране параметров потока данных в Power BI можно отслеживать состояние шлюза для потока данных и назначить потоку данных новый шлюз, как показано на следующем изображении.

![Мониторинг шлюза](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Изменение шлюза

Изменить корпоративный шлюз, используемый для некоторого потока данных, можно любым из двух способов:

1. **Из средства разработки**. В средстве разработки потоков данных можно изменить шлюз, назначенный для всех запросов.

    > [!NOTE]
    > Поток данных будет искать и (или) создавать нужные источники через новый шлюз. Если это будет невозможно, вы не сможете изменить шлюз, пока все необходимые потоки данных не станут доступны через выбранный шлюз.

2. **На экране параметров**. Назначенный шлюз можно изменить на экране потока данных в службе Power BI.

Дополнительные сведения о корпоративных шлюзах см. в статье [о локальных шлюзах данных](service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

Есть несколько известных ограничений на использование корпоративных шлюзов с потоками данных:

* Каждый поток данных может использовать только один шлюз. Это означает, что все запросы нужно настроить через один и тот же шлюз.
* Изменение шлюза повлияет на работу всего потока данных.
* Если необходимо использовать несколько шлюзов, мы рекомендуем создать несколько потоков данных (по одному на каждый шлюз) и использовать вычисляемые или сопоставленные сущности для объединения данных.
* Потоки данных можно использовать только через корпоративные шлюзы. Личные шлюзы не предоставляются для выбора в раскрывающихся списках и на экранах параметров.


## <a name="next-steps"></a>Следующие шаги

В этой статье предоставлены сведения об использовании локального источника данных для потоков данных, а также об использовании и настройке шлюзов для доступа к этим данным. Следующие статьи также содержат полезные сведения на эти темы.

* [Self-service data prep in Power BI (Preview)](service-dataflows-overview.md) (Самостоятельная подготовка данных в Power BI (предварительная версия))
* [Creating and using dataflows in Power BI (Preview)](service-dataflows-create-use.md) (Создание и использование потоков данных в Power BI (предварительная версия))
* [Использование вычисляемых сущностей в Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Ресурсы для разработчиков потоков данных Power BI](service-dataflows-developer-resources.md)

Дополнительные сведения о Power Query и обновлении по расписанию содержатся в следующих статьях:
* [Общие сведения о запросах в Power BI Desktop](desktop-query-overview.md)
* [Настройка запланированного обновления](refresh-scheduled-refresh.md)

Дополнительные сведения о модели общих данных вы найдете в этой обзорной статье:
* [Что такое модель общих данных?](https://docs.microsoft.com/powerapps/common-data-model/overview)

