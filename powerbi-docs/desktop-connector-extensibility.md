---
title: Расширение соединителей в Power BI
description: Возможности, функции, параметры безопасности и сертифицированные соединители для расширения соединителей
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: c63357df043ff6a646562d398a07d8042dd5a0ee
ms.sourcegitcommit: 7fb0b68203877ff01f29724f0d1761d023075445
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2018
ms.locfileid: "39256602"
---
# <a name="connector-extensibility-in-power-bi"></a>Расширение соединителей в Power BI

В Power BI клиенты и разработчики могут расширить источники данных, к которым они подключаются, различными способами, например с помощью существующих соединителей и универсальных источников данных (таких как ODBC, OData, Oledb, Web, CSV, XML, JSON). В дополнение к этим источникам данных разработчики могут создавать модули обработки данных, или **настраиваемые соединители**, и сертифицировать соединители, чтобы использовать их как **сертифицированные соединители**.

В предыдущих версиях Power BI **настраиваемые соединители** можно было использовать через специальный параметр. Теперь вам доступно меню, где можно безопасно управлять уровнем пользовательского кода, которому вы разрешите выполняться в вашей системе: все настраиваемые соединители или только соединители, сертифицированные и распространяемые корпорацией Майкрософт в диалоговом окне **Получить данные**.

## <a name="custom-connectors"></a>Настраиваемые соединители

**Настраиваемые соединители** могут предоставлять целый ряд возможностей — от небольших API-интерфейсов, которые важны для вашего бизнеса, до крупных отраслевых служб, которые еще не реализованы в Майкрософт. Большинство таких соединителей распространяются самим поставщиком, и, если вам нужен определенный соединитель данных, обратитесь к поставщику.

Чтобы использовать **настраиваемый соединитель**, поместите его в папку *\[Документы]\\Power BI Desktop\\Настраиваемые соединители* и измените параметры безопасности, как описано в следующем разделе.

Вам не нужно менять параметры безопасности для использования **сертифицированных соединителей**.

## <a name="data-extension-security"></a>Безопасность модуля обработки данных

Чтобы изменить параметры безопасности модуля обработки данных в **Power BI Desktop**, выберите **Файл > Параметры и настройки > Параметры > Безопасность**.

![Выбор возможности загружать настраиваемые соединители с параметрами безопасности модуля обработки данных](media/desktop-connector-extensibility/data-extension-security-1.png)

В разделе **Модули обработки данных** можно выбрать один из двух уровней безопасности:

* (рекомендуется) Разрешить загрузку только сертифицированных модулей;
* (не рекомендуется) Разрешить загрузку всех модулей без предупреждения.

Если вы планируете использовать **настраиваемые соединители** или соединители, которые разработали и распространяете вы или сторонние разработчики, выберите **(Не рекомендуется) Разрешить загрузку всех модулей без предупреждения**. Этот параметр безопасности не рекомендуется, если вы не планируете использовать **настраиваемые соединители**.

Если вы выберете **рекомендованный** параметр безопасности и в вашей системе есть настраиваемые соединители, будет выведено сообщение об ошибке, описывающее соединители, которые не удается загрузить в связи с безопасностью.

![В диалоговом окне будут приведены настраиваемые соединители, которые не удается загрузить из-за параметров безопасности, в этом примере это TripPin.](media/desktop-connector-extensibility/data-extension-security-2.png)

Чтобы устранить эту ошибку и использовать эти соединители, измените параметры безопасности на **нерекомендованные**, как описано ранее, и перезапустите **Power BI Desktop**.

## <a name="certified-connectors"></a>Сертифицированные соединители

Некоторые модули обработки данных считаются **сертифицированными**. Такие сертифицированные соединители можно использовать через диалоговое окно **Получить данные**, но обслуживанием и поддержкой все равно будет заниматься сторонний разработчик, который создал соединитель. Корпорация Майкрософт распространяет такие соединители, однако мы не несем ответственности за их производительность или непрерывную работу.

Если вы хотите сертифицировать настраиваемый соединитель, попросите своего поставщика обратиться в корпорацию Майкрософт.