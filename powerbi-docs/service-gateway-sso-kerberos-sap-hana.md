---
title: Использование Kerberos для единого входа в SAP HANA
description: Настройка сервера SAP HANA для включения единого входа из службы Power BI
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e7bdb0ae2f1e512e3e431cf69395d601cbc7b3f
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968529"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Использование Kerberos для единого входа в SAP HANA

В этой статье описывается, как настроить источник данных SAP HANA для включения единого входа из службы Power BI.

> [!NOTE]
> Выполните действия, описанные в этой статье, в дополнение к шагам в статье [Настройка единого входа на основе Kerberos из службы Power BI в локальные источники данных](service-gateway-sso-kerberos.md), прежде чем пытаться обновить отчет на основе SAP HANA, в котором используется единый вход Kerberos.

## <a name="enable-sso-for-sap-hana"></a>Включение единого входа для SAP HANA

Чтобы включить единый вход для SAP HANA, выполните следующие действия:

* Убедитесь, что для сервера SAP HANA используется минимально допустимая версия, которая зависит от уровня платформы сервера SAP HANA:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* На компьютере шлюза установите последнюю версию драйвера ODBC для HANA от SAP.  Минимальная версия драйвера ODBC для HANA — 2.00.020.00, выпущенная в августе 2017 г.

Убедитесь, что сервер SAP HANA настроен для единого входа на основе Kerberos. Дополнительные сведения о настройке единого входа для SAP HANA с помощью Kerberos см. в разделе о [едином входе с использованием Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) руководства по безопасности SAP HANA. На этой странице приведены полезные ссылки, в частности примечание SAP 1837331 — HOWTO HANA DBSSO Kerberos/Active Directory.

Мы также рекомендуем следующие дополнительные действия, которые позволят обеспечить небольшое повышение производительности.

1. В каталоге установки шлюза найдите и откройте этот файл конфигурации: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Найдите свойство *FullDomainResolutionEnabled* и измените его значение на *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Теперь [запустите отчет Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о **локальном шлюзе данных** и **DirectQuery** см. в следующих ресурсах:

* [Что такое локальный шлюз данных?](/data-integration/gateway/service-gateway-getting-started)
* [Power BI и DirectQuery](desktop-directquery-about.md)
* [Источники данных, поддерживаемые DirectQuery](desktop-directquery-data-sources.md)
* [Использование DirectQuery и SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [DirectQuery и SAP HANA](desktop-directquery-sap-hana.md)
