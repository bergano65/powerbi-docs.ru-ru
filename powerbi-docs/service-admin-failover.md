---
title: Вопросы и ответы о высоком уровне доступности, отработке отказа и аварийном восстановлении в Power BI
description: Узнайте, как в службе Power BI реализуется высокая доступность, непрерывность бизнес-процессов и аварийное восстановление.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 7446cb9db0f4ebbb20e316365263fa6f09de71bb
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2019
ms.locfileid: "55448228"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Вопросы и ответы о высоком уровне доступности, отработке отказа и аварийном восстановлении в Power BI

В этой статье рассказывается, как в службе Power BI реализуется высокая доступность, непрерывность бизнес-процессов и аварийное восстановление. Прочитав эту статью, вы сможете лучше понять, каким образом достигается высокий уровень доступности, при каких условиях Power BI выполняет отработку отказа и чего ожидать от службы во время отработки отказа.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Что означает "высокий уровень доступности" в Power BI?

Power BI — это полностью управляемое программное обеспечение как услуга (SaaS).  Эта служба разработана и предоставляется корпорацией Майкрософт таким образом, чтобы обеспечивать устойчивость к сбоям инфраструктуры и бесперебойный доступ пользователей к отчетам.  Для службы реализуется [соглашение об уровне обслуживания 99,9 %](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>Что такое отработка отказа в Power BI?

Для обеспечения непрерывности бизнес-процессов Power BI сохраняет несколько экземпляров каждого компонента в центрах обработки данных Azure (также известных как регионы). Если возникает сбой или проблема, из-за которых служба Power BI становится недоступной или выходит из строя в одном регионе, Power BI выполняет отработку отказа всех компонентов в этом регионе на резервном экземпляре. Функция отработки отказа восстанавливает доступность и работу в экземпляре службы Power BI в новом регионе (обычно в том же географическом расположении, как указано в [Центре управления безопасностью Майкрософт](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Экземпляр службы Power BI, для которого выполняется отработка отказа, поддерживает только _операции чтения_. Это означает, что следующие операции не поддерживаются во время отработки отказа: обновления, операции публикации отчетов, изменение панели мониторинга или отчета и другие операции, требующие внесения изменений в метаданные Power BI (например, вставка комментария в отчет).  Операции чтения, такие как отображение панелей мониторинга и отчетов (не на основе подключений Direct Query и Live Connect к локальным источникам данных), работают в обычном режиме.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Как обеспечивается синхронизация резервных экземпляров с моими данными?

Все компоненты службы Power BI регулярно синхронизируются с соответствующими резервными экземплярами. Целевым показателем является синхронизация раз в 15 минут любого содержимого, передаваемого или изменяемого в Power BI. В случае отработки отказа Power BI использует [географически избыточную репликацию хранилища Azure](/azure/storage/common/storage-redundancy-grs) и [географически избыточную репликацию SQL Azure](/azure/sql-database/sql-database-active-geo-replication). Это гарантирует наличие в других регионах резервных экземпляров, которые могут использоваться для отработки отказа.

## <a name="where-are-the-failover-clusters-located"></a>Где находятся отказоустойчивые кластеры?

Резервные экземпляры размещаются в том же географическом расположении (геообъекте), которое вы выбрали при регистрации организации в Power BI, за исключением оговоренных в [Центре управления безопасностью Майкрософт](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Геообъект может содержать несколько регионов, и системы Майкрософт могут реплицировать данные в любой из регионов в данном геообъекте для обеспечения устойчивости данных. Корпорация Майкрософт не будет реплицировать или перемещать данные пользователей за пределы геообъекта. Сведения о картах геообъектов, предлагаемых Power BI, и соответствующих регионах см. в [Центре управления безопасностью Майкрософт](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Как определяется необходимость отработки отказа?

Существуют две различные системы, которые указывают, когда может потребоваться отработка отказа:

- Наши внешние и внутренние проверки мониторинга выявляют низкую доступность или невозможность правильной работы. На это могут указывать сбои, обнаруженные в компонентах или в одной или нескольких службах Power BI, от которых зависит работа Power BI в этом регионе.
- Центральный эксплуатационный отдел Microsoft Azure информирует нас о критическом сбое в регионе.

В обоих случаях руководители Power BI принимают решение выполнить отработку отказа: принятие решений не автоматизировано. Как только будет принято решение, процесс отработки отказа выполняется автоматически.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Как узнать, что Power BI находится в режиме отработки отказа?

Соответствующее уведомление публикуется на странице поддержки Power BI ([https://powerbi.microsoft.com/en-us/support/](https://powerbi.microsoft.com/en-us/support/)). В уведомлении перечисляются основные операции, которые будут недоступны во время отработки отказа, включая публикацию, обновление, создание панели мониторинга, дублирование панели мониторинга и изменение разрешений.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Сколько времени занимает отработка отказа Power BI?

Как только будет принято решение об отработке отказа, резервный экземпляр становится доступным максимум в течение 60 минут.

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Когда мой экземпляр Power BI будет возвращен в исходный регион?

Экземпляры службы Power BI возвращаются в исходный регион после устранения ошибки, приведшей к отработке отказа. Посетите страницу поддержки по Power BI: Когда проблема будет устранена, команда Power BI удалит уведомление с описанием отработки отказа. На этом этапе будет восстановлена нормальная работа.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Несу ли я ответственность за доступность моего решения Power BI?

Если решение Power BI, используемое в вашей организации, включает в себя один из следующих элементов, необходимо принять некоторые меры, чтобы гарантировать высокую доступность такого решения.

- Если в вашей организации используется Power BI Premium, необходимо убедиться, что емкость Premium соответствует требованиям развертывания к нагрузке.  [Технический документ по планированию и развертыванию Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) и [приложение "Метрики емкости Power BI Premium"](service-admin-premium-monitor-capacity.md) могут помочь вам спланировать и выполнить это требование. Мы регулярно добавляем новые функции в приложение метрик и на портал администрирования Power BI.
- Если ваша организация получает доступ к локальным источникам данных с помощью локального шлюза Power BI, для поддержки высокой доступности необходимо настроить шлюз, [как описано в этой статье](service-gateway-high-availability-clusters.md). Следуйте инструкциям в этом руководстве при обновлении отчетов в режиме импорта или при обращении к данным или моделям данных с помощью DirectQuery или Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Работают ли шлюзы в режиме отработки отказа?

Нет. Данные, поступающие из локальных источников данных (все отчеты и панели мониторинга на основе Direct Query и Live Connect), не будут работать во время отработки отказа. Тем не менее конфигурация шлюза не изменяется. Когда экземпляр Power BI возвращается в исходное состояние, шлюзы также возвращаются к обычным функциям.