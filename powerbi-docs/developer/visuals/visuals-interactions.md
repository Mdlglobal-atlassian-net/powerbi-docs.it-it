---
title: Interazioni di oggetti visivi
description: Come verificare se l'oggetto visivo di Power BI consente le interazioni degli oggetti visivi
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424494"
---
# <a name="visuals-interactions"></a>Interazioni di oggetti visivi

Gli oggetti visivi possono eseguire query sul valore del flag "allowInteractions", che indica se l'oggetto visivo deve consentire interazioni di oggetti visivi.
Ad esempio, gli oggetti visivi sono interattivi durante la visualizzazione o la modifica dei report, ma non lo sono quando vengono visualizzati in un dashboard.
Queste interazioni includono clic, panoramica, zoom, selezione e altre ancora.
Si noti che le descrizioni comando devono essere abilitate in tutti gli scenari, indipendentemente da questo flag.

Il flag "allowInteractions" viene passato come valore booleano durante l'inizializzazione dell'oggetto visivo, come membro dell'interfaccia IVisualHost.

In qualsiasi scenario di Power BI che richiede che gli oggetti visivi non siano interattivi, ad esempio nei riquadri del dashboard, il flag "allowInteractions" sarà impostato su false.
In caso contrario, ad esempio nei report,"allowInteractions" sarà impostato su true.

Per altre informazioni, vedere il [repository dell'oggetto visivo SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
