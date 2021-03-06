---
title: Параметры конфигурации приложения Power BI
description: Настройка поведения Power BI с помощью средства MDM
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/07/2020
ms.author: painbar
ms.openlocfilehash: 1991381f8b2917fe3bc61a8be22fbdf44e706d71
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79205557"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Удаленная настройка приложения Power BI с помощью средства управления мобильными устройствами (MDM)

Приложение Power BI Mobile для iOS и Android поддерживает параметры, позволяющие администраторам служб управления мобильными устройствами (MDM), таких как Intune, настраивать поведение приложения.

Приложение Power BI Mobile поддерживает следующие сценарии конфигурации:

* Конфигурация сервера отчетов (IOS и Android)
* Параметры защиты данных (iOS)
* Параметры взаимодействия (iOS и Android)

## <a name="report-server-configuration-ios-and-android"></a>Конфигурация сервера отчетов (IOS и Android)

Приложение Power BI для iOS и Android позволяет администраторам удаленно отправлять конфигурацию сервера отчетов на зарегистрированные устройства.

| Ключ | Тип | Описание |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Строка | URL-адрес сервера отчетов.<br><br>Должен начинаться с префикса http или https.|
| com.microsoft.powerbi.mobile.ServerUsername | Строка | [необязательно]<br><br>Имя пользователя для подключения к серверу.<br><br>Если оно отсутствует, в приложении будет выведен запрос на ввод имени пользователя.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Строка | [необязательно]<br><br>Значение по умолчанию — "Сервер отчетов"<br><br>Понятное имя, представляющее сервер в приложении. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Логический | [необязательно]<br><br>Значение по умолчанию — True. Если задано значение True, этот параметр переопределяет любое уже имеющееся определение сервера отчетов на мобильном устройстве. Уже настроенные существующие серверы удаляются. Кроме того, пользователь не может удалить данную конфигурацию.<br><br>Если задано значение False, передаваемые значения добавляются, а существующие параметры сохраняются. Если в мобильном приложении уже настроен тот же URL-адрес сервера, приложение оставляет эту конфигурацию нетронутой. Приложение не требует, чтобы пользователь вновь проходил проверку подлинности на том же сервере. |

## <a name="data-protection-settings-ios"></a>Параметры защиты данных (iOS)

Приложение Power BI для iOS позволяет администраторам настроить конфигурацию по умолчанию для параметров безопасности и конфиденциальности. Вы можете заставить пользователей предоставить их Face ID, Touch ID или секретный код при доступе к приложению Power BI.

| Ключ | Тип | Описание |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Логический | По умолчанию используется значение False. <br><br>Пользователям для доступа к приложению на устройстве могут потребоваться биометрические данные, такие как TouchID или FaceID. При необходимости биометрические данные используются в дополнение к проверке подлинности.<br><br>При использовании политик защиты приложений корпорация Майкрософт рекомендует отключить этот параметр, чтобы предотвратить двойной запрос доступа. |

## <a name="interaction-settings-ios-and-android"></a>Параметры взаимодействия (iOS и Android)

Приложение Power BI для iOS и Android позволяет администраторам настраивать параметры взаимодействия, если необходимо изменить параметры по умолчанию для определенных групп пользователей в организации.

>[!NOTE]
>В настоящее время не все устройства поддерживают полный набор параметров взаимодействия. Параметры, доступные в настоящее время на различных устройствах, приведены в таблице в разделе [Настройка параметров взаимодействия с отчетами](mobile-app-interaction-settings.md).

| Ключ | Тип | Значения | Описание |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Строка |  <nobr>одиночное касание</nobr><br><nobr>двойное касание</nobr> | Настройка выбора точки данных при касании визуального элемента. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Логический |  <nobr>True</nobr><br><nobr>False</nobr> | Настройка выбора точки данных при касании вместо ранее выбранных элементов или в дополнение к ним. |
| com.microsoft.powerbi.mobile.RefreshAction | Строка |  <nobr>потяните, чтобы обновить</nobr><br>. | Настройка обновления отчета с помощью кнопки или функции "Потяните, чтобы обновить". |
| com.microsoft.powerbi.mobile.FooterAppearance | Строка |  закреплено<br>Динамический | Настройка закрепления колонтитула внизу отчета или его автоматического скрытия. |

## <a name="deploying-app-configuration-settings"></a>Развертывание параметров конфигурации приложения

Ниже описаны действия, которые позволяют создать политику конфигурации приложения. После создания этой политики вы можете назначить ее параметры группам пользователей.

1. Подключите средство MDM.
2. Создайте политику настройки приложения и присвойте ей имя.
3. Выберите пользователей, к которым будет применена эта политика.
4. Создайте пары "ключ-значение" для параметра, который нужно отправить пользователям.

Портал Intune позволяет администраторам развертывать эти параметры в приложении Power BI с помощью политик конфигурации приложений. Однако поддерживается любой поставщик MDM. Если вы не используете Intune, потребуется обратиться к документации по MDM, чтобы узнать, как развертывать эти параметры.

## <a name="next-steps"></a>Дальнейшие действия

* Скачайте мобильное приложение Power BI из [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) и [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Подпишитесь на страницу [@MSPowerBI в Twitter](https://twitter.com/MSPowerBI)
* Присоединяйтесь к обсуждению в [сообществе Power BI](https://community.powerbi.com/).
