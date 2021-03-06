---
title: Руководство по использованию изображений в отчетах с разбивкой на страницы
description: Указания по использованию изображений в отчетах Power BI с разбивкой на страницы.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d2f3f36911c72df1b95ceb5bd90043870559cc62
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920707"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Руководство по использованию изображений в отчетах с разбивкой на страницы

Эта статья предназначена для разработчиков [отчетов Power BI с разбивкой на страницы](../paginated-reports/paginated-reports-report-builder-power-bi.md). В ней приводятся рекомендации по работе с изображениями. Как правило, изображения в макетах отчетов служат для отображения таких графических элементов, как логотип компании или картинка.

Изображения могут храниться в трех разных местах:

- в отчете (внедренные изображения);
- на веб-сервере;
- в базе данных, откуда они могут быть получены набором данных.

Изображения могут использоваться в макетах отчетов в различных целях:

- отдельный логотип или картинка;
- картинки, связанные со строками данных;
- фон для некоторых элементов отчета:
  - текст отчета;
  - Текстовое поле
  - Прямоугольник
  - область данных табликса (таблица, матрица или список).

## <a name="suggestions"></a>Предложения

Чтобы обеспечить профессиональное оформление отчетов, упростить обслуживание и оптимизировать производительность, следуйте приведенным ниже рекомендациям.

- **Используйте наименьший возможный размер**. Мы рекомендуем подготавливать изображения небольшого размера, но четкие и контрастные. Соблюдайте компромисс между качеством и размером. Чтобы уменьшить размер файла с изображением, можно воспользоваться графическим редактором (например Microsoft Paint).
- **Старайтесь не внедрять изображения**. Во первых, внедренные изображения могут существенно увеличить размер файла отчета и, следовательно, замедлить преобразование отчета для просмотра. Во-вторых, они могут катастрофически усложнить обслуживание, если потребуется обновить изображение во множестве отчетов (например, при изменении логотипа компании).
- **Используйте веб-сервер в качестве хранилища**. Веб-сервер хорошо подходит для хранения изображений, особенно если это логотип компании, который размещен на ее веб-сайте. Однако следует учесть, будут ли пользователи получать доступ к отчету извне вашей сети. В этом случае изображения должны быть доступны через Интернет.

    Если изображения связаны с данными (как в случае с фотографиями продавцов), присваивайте файлам изображений такие имена, чтобы выражение отчета могло динамически формировать URL-пути к изображениям. Например, именем файла с фотографией продавца может быть соответствующий номер сотрудника. Если набор данных отчета получает номера сотрудников, можно написать выражение, формирующее полные URL-пути к изображениям.
- **Используйте базу данных в качестве хранилища**. Если изображения хранятся в реляционной базе данных, имеет смысл получать их непосредственно из таблиц базы данных, особенно если изображения не слишком велики.
- **Используйте подходящие фоновые изображения**. Если вы решили использовать фоновые изображения, они не должны отвлекать пользователей от данных отчета. 

    Кроме того, следует использовать _изображения в стиле подложки_. Как правило, такие изображения имеют прозрачный фон (или тот же цвет фона, что и в отчете). В них также используются бледные цвета. Распространенными примерами изображений в стиле подложки могут служить логотипы компаний или гриф конфиденциальности.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения, связанные с темой этой статьи, см. в следующих ресурсах.

- [Сведения об отчетах с разбивкой на страницы в Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- У вас появились вопросы? [Попробуйте задать вопрос в сообществе Power BI.](https://community.powerbi.com/)
- У вас есть предложения? [Идеи по улучшению Power BI](https://ideas.powerbi.com/)
