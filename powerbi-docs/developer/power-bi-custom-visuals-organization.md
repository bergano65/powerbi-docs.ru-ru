---
title: Визуальны элементы организации в Power BI
description: Применение и создание визуальных элементов организации в Power BI, а также управление ими
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 8c28c5ee89ffee37c09db8dc6ffcd6fb90274786
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102095"
---
# <a name="organizational-visuals-in-power-bi"></a>Визуальные элементы организации в Power BI

В Power BI визуальные элементы Power BI используются для создания уникальной визуализации, соответствующей вашим требованиям. Эти визуальные элементы создаются разработчиками, когда другие визуальные элементы в Power BI не соответствуют их требованиям.

Для некоторых организаций пользовательские элементы Power BI имеют еще большее значение. Они могут пригодиться для передачи данных или аналитических сведений, уникальных для организации. Организации могут иметь особые требования к данным или уделять большое внимание методам частного бизнеса. Таким организациям нужна разработка визуальных элементов Power BI, их распространение по всей организации и правильное обслуживание. С помощью визуальных элементов Power BI в организации можно выполнять все эти задачи.

На следующем рисунке показан поток прохождения визуальных элементов в Power BI: передача от администратора на разработку и обслуживание, а затем к специалисту по анализу данных.

![Изображение пользовательского визуального элемента](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Визуальные элементы организации развертываются и управляются администратором Power BI на портале администрирования. После того как визуальные элементы Power BI организации развернуты в репозиторий организации, пользователи в организации могут легко находить и импортировать их непосредственно из Power BI Desktop в свои отчеты.

Дополнительные сведения об использовании визуальных элементов Power BI организации в созданных вами отчетах см. в статье об [импорте визуальных элементов организации в отчеты](power-bi-custom-visuals.md).

## <a name="administer-organizational-power-bi-visuals"></a>Администрирование визуальных элементов Power BI организации

Дополнительные сведения об администрировании, развертывании визуальных элементов Power BI организации и управлении ими см. в статье о [развертывании и администрировании визуальных элементов Power BI организации](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Пользовательский визуальный элемент может содержать код, подвергающий риску безопасность или конфиденциальность. Прежде чем развертывать пользовательский визуальный элемент в репозиторий организации, убедитесь в надежности его автора и источника.

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

Есть некоторые рекомендации и ограничения, которые нужно учитывать.

Администратор

* Устаревшие визуальные элементы Power BI (например, визуальные элементы, которые созданы не на основе API новых версий) не поддерживаются.

* Если пользовательский визуальный элемент удален из репозитория, все отчеты, в которых использовался этот элемент, перестанут отображаться. Удаление из репозитория является необратимой операцией. Чтобы на время отключить пользовательский визуальный элемент, используйте функцию "Отключить".

Пользователь

* Визуальные элементы Power BI организации закрыты для внешних пользователей. Они импортируются из репозитория организации. Как и любой другой закрытый элемент, их нельзя [экспортировать в PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) или отображать в сообщениях электронной почты по [подписке на страницы отчетов](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Эти возможности поддерживаются только для [сертифицированных визуальных элементов Power BI](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified), импортируемых напрямую из Marketplace.

* Визуальные элементы Visio, PowerApps и GlobeMap из магазина AppSource не будут отображаться, если они развернуты в репозитории организации.

## <a name="troubleshoot"></a>Устранение неполадок

Сведения об устранении неполадок: [Устранение неполадок с визуальными элементами Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>ВОПРОСЫ И ОТВЕТЫ

Дополнительные сведения и ответы на вопросы: [Часто задаваемые вопросы о визуальных элементах Power BI](power-bi-custom-visuals-faq.md#organizational-visuals).

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI](https://community.powerbi.com/).