---
title: Возможности и свойства визуальных элементов Power BI
description: В этой статье описываются возможности и свойства визуальных элементов Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1e2fbe3288e5dbb759a56ad1c299db2e277408b2
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380762"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Добавление контекстного меню к визуальному элементу Power BI

Вы можете использовать `selectionManager.showContextMenu()` с параметрами `selectionId` и положением (в качестве объекта `{x:, y:}`), чтобы Power BI отображал контекстное меню для визуального элемента.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` появился в API визуальных элементов 2.2.0.

Обычно он добавляется как событие щелчка правой кнопкой мыши (или длительное нажатие для сенсорных устройств). Контекстное меню было добавлено в образец BarChart для справки:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
