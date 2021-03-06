---
title: Сертифицированные визуальные элементы Power BI
description: Требования и процесс отправки пользовательского визуального элемента для сертификации, а также список сертифицированных визуальных элементов Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: 2dee596648c9921cefab6903167e780bfacb122e
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2020
ms.locfileid: "80113907"
---
# <a name="get-a-power-bi-visual-certified"></a>Получите сертификацию для визуального элемента Power BI

Сертифицированные визуальные элементы Power BI — это визуальные элементы Power BI в [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals), которые соответствуют [требованиям к коду](#certification-requirements) группы разработчиков Power BI в Microsoft. Эти визуальные элементы проверяются, не обращаются ли они к внешним службам или ресурсам и соответствуют ли шаблонам и рекомендациям по созданию безопасного кода.

Сертифицированные визуализации Power BI предусматривают дополнительные возможности. Например, вы можете [экспортировать их в PowerPoint](../../consumer/end-user-powerpoint.md) или добавлять для отображения в сообщениях электронной почты, получаемых при оформлении [подписки на страницы отчета](../../consumer/end-user-subscribe.md).

Процесс сертификации необязателен. Несертифицированные визуальные элементы Power BI не обязательно являются ненадежными визуальными элементами Power BI. Некоторые визуальные элементы Power BI не проходят сертификацию, так как не соответствуют одному или нескольким [требованиям сертификации](power-bi-custom-visuals-certified.md#certification-requirements). Например, визуальный элемент Power BI сопоставления подключается к внешней службе или визуальный элемент Power BI использует коммерческие библиотеки.

> [!NOTE]
> Корпорация Майкрософт не является автором сторонних визуализаций Power BI. Чтобы проверить функциональные возможности сторонних визуализаций, обращайтесь к автору напрямую.

## <a name="certification-requirements"></a>Требования к сертификации

Чтобы [сертифицировать](#get-a-power-bi-visual-certified) свою визуализацию Power BI, она должна соответствовать требованиям, перечисленным в этом разделе. 

### <a name="general-requirements"></a>Общие требования

Визуальный элемент Power BI должен быть одобрен в Центре партнеров. Рекомендуется, чтобы визуальный элемент Power BI уже был в [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Дополнительные сведения о публикации визуального элемента Power BI в AppSource см. в статье [Публикация визуальных элементов Power BI в Центре партнеров](office-store.md).

Перед отправкой визуального элемента Power BI для сертификации убедитесь, что он соответствует правилам [для визуальных элементов Power BI](guidelines-powerbi-visuals.md).

При отправке визуального элемента Power BI убедитесь, что скомпилированный пакет точно соответствует отправляемому пакету.

### <a name="code-repository-requirements"></a>Требования к репозиторию кода

Хотя вам не нужно публиковать код в GitHub, репозиторий кода должен быть доступен команде разработчиков Power BI для ознакомления. Лучший способ сделать это — предоставить исходный код (JavaScript или TypeScript) в GitHub.

Репозиторий должен содержать следующие элементы:
* код только для одного визуального элемента Power BI; Он не может содержать код для нескольких визуальных элементов Power BI или несвязанного кода.
* ветвь с именем **certification** (обязательно в нижнем регистре). Исходный код в этой ветви должен соответствовать коду в отправленном пакете. Этот код можно обновить только во время следующей отправки, когда вы будете повторно отправлять визуальный элемент Power BI.

Если визуальный элемент Power BI использует частные пакеты NPM или подмодули Git, необходимо предоставить доступ к дополнительным репозиториям, содержащим этот код.

Чтобы понять, как выглядит репозиторий визуальных элементов Power BI, изучите репозиторий GitHub с [примерами линейчатых диаграмм визуальных элементов Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).

### <a name="file-requirements"></a>Требования к файлу

Используйте последнюю версию API для создания визуального элемента Power BI.

Репозиторий должен содержать следующие файлы:
* **GITIGNORE**-файл — добавьте в него `node_modules`, `.tmp` и `dist`. Код не может содержать папки *node_modules*, *.tmp* или *dist*.
* **capabilities.json** — если вы отправляете новую версию визуального элемента Power BI с изменениями в свойствах этого файла, убедитесь, что они не нарушают отчеты для существующих пользователей.
* **pbiviz.json** 
* **package.json**. Для визуального элемента должны быть установлены следующие пакеты:
   * [tslint](https://www.npmjs.com/package/tslint) версии 5.18.0 или выше;
   * [typescript](https://www.npmjs.com/package/typescript) версии 3.0.0 или выше;
   * [tslint-microsoftcontrib](https://www.npmjs.com/package/tslint-microsoft-contrib) версии 6.2.0 или выше.
   * Файл должен содержать команду для запуска анализатора кода — `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Требования к командам

Убедитесь, что перечисленные ниже команды не возвращают ошибок.

* `npm install`
* `pbiviz package`
* `npm audit` — не должна возвращать предупреждения с высоким или умеренным уровнем.
* [TSlint от Майкрософт](https://www.npmjs.com/package/tslint-microsoft-contrib) с [необходимой конфигурацией](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Эта команда не должна возвращать ошибки, связанные с оформлением кода.

### <a name="compiling-requirements"></a>Требования к компиляции

Для написания визуальных элементов Power BI используйте последнюю версию [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools).

Необходимо компилировать визуальный элемент Power BI с `pbiviz package`. Если вы используете собственные сборочные скрипты, укажите пользовательскую команду сборки `npm run package`.



### <a name="source-code-requirements"></a>Требования к исходному коду

Убедитесь, что вы следуете перечню политик [дополнительной сертификации визуальных элементов Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Если отправка не будет соответствовать этим рекомендациям, сообщение из Центра партнеров об отклонении отправки будет содержать номера политик, перечисленные по этой ссылке.

Выполните приведенные ниже требования к коду, чтобы код соответствовал политикам сертификации Power BI.  

**Обязательно**
* Используйте только открытые и доступные для просмотра компоненты OSS, например общедоступные библиотеки JavaScript или TypeScript.
* Код должен поддерживать [API событий отрисовки](event-service.md).
* Обеспечьте безопасную обработку DOM. Перед добавлением данных в модель DOM используйте очистку для пользовательского ввода или пользовательской информации.
* Используйте [образец отчета](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) в качестве тестового набора данных.

**Не разрешено**
* Доступ к внешним службам или ресурсам. Например, запросы HTTP/S или WebSocket не должны отправляться из Power BI во внешние службы.
* С помощью `innerHTML` или `D3.html(user data or user input)`.
* Ошибки или исключения JavaScript для любых входных данных в консоли браузера.
* Произвольный или динамический код, например `eval()`, небезопасное использование `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)`, пользовательский ввод или данные пользователя.
* Минифицированные файлы или проекты JavaScript.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Отправка визуализации Power BI на сертификацию

Вы можете подать заявку на сертификацию визуализации Power BI командой Power BI через Центр партнеров.

>[!TIP]
>Процесс сертификации визуализации Power BI может занять некоторое время. Если вы создаете новую визуализацию Power BI, мы рекомендуем опубликовать ее в Центре партнеров, прежде чем подавать заявку на сертификацию Power BI. Так публикация визуализации не будет отложена.

Чтобы подать заявку на сертификацию визуализацию Power BI, сделайте следующее:

1. Войдите в Центр партнеров.
2. На странице **Обзор** выберите визуализацию Power BI и перейдите на страницу **настройки продукта**.
3. Установите флажок **Запросите сертификацию Power BI**.
4. На странице **Проверка и публикация** в текстовом поле **Примечания о сертификации** укажите ссылку на исходный код и учетные данные, требуемые для получения доступа.

### <a name="private-repository-submission-process"></a>Процесс отправки частного репозитория

Если вы используете частный репозиторий, например GitHub, чтобы отправить визуальный элемент Power BI на сертификацию, следуйте инструкциям в этом разделе.
1. Создайте новую учетную запись для группы проверки.
2. Настройте [двухфакторную проверку подлинности для учетной записи](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa).
3. [Создайте новый набор кодов восстановления](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. При отправке визуального элемента Power BI предоставьте следующее:
    * ссылка на репозиторий;
    * учетные данные для входа (включая пароль);
    * коды восстановления;
    * разрешения на доступ к учетной записи только для чтения ([pbicvsupport](https://github.com/pbicvsupport)).

## <a name="certified-power-bi-visual-badges"></a>Эмблемы сертифицированных визуальных элементов Power BI

После сертификации визуальный элемент Power BI получает специальную эмблему, которая указывает, что он сертифицирован.

### <a name="certified-power-bi-visuals-in-appsource"></a>Сертифицированные визуальные элементы Power BI в AppSource

* При поиске в Интернете [визуальных элементов Power BI в AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) вы можете увидеть маленькую желтую эмблему на карточке визуального элемента. Она означает, что это сертифицированный визуальный элемент Power BI.

    ![Сертифицированный визуальный элемент Power BI в AppSource](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Если щелкнуть визуальную карту Power BI в AppSource, желтая эмблема с надписью *PBI Certified* будет означать, что этот визуальный элемент Power BI сертифицирован.

    ![Сертифицированный визуальный элемент Power BI на странице приложений](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Сертифицированные визуальные элементы Power BI в интерфейсе Power BI

* При импорте визуального элемента Power BI из Power BI Desktop или службы Power BI синий значок означает, что этот визуальный элемент Power BI сертифицирован.

    ![Сертифицированный визуальный элемент Power BI в интерфейсе Power BI](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* Можно отобразить только сертифицированные визуальные элементы Power BI, выбрав параметр фильтра *Сертифицированные Power BI*.

## <a name="next-steps"></a>Дальнейшие действия

* Если вы как веб-разработчик заинтересованы в создании собственных визуализаций Power BI и их добавлении в  [Microsoft AppSource](https://appsource.microsoft.com), начните с руководства по  [разработке визуализаций Power BI](custom-visual-develop-tutorial.md).

* Дополнительные сведения о визуальных элементах см. в разделе [Часто задаваемые вопросы о сертифицированных визуальных элементах](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

* [Разработка визуального элемента Power BI](custom-visual-develop-tutorial.md)

* [Список видео Майкрософт, посвященных визуальным элементам Power BI, на сайте YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Визуальные элементы в Power BI](power-bi-custom-visuals.md)

* [Публикация визуальных элементов Power BI в Microsoft AppSource](office-store.md)

* Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI.](https://community.powerbi.com/)