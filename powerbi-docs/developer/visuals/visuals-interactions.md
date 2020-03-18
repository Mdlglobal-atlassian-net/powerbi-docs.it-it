---
title: Interazioni con oggetti visivi negli oggetti visivi di Power BI
description: Questo articolo illustra come verificare se gli oggetti visivi di Power BI devono consentire le interazioni degli oggetti visivi.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1fb4f7d5950ab18a74dcacfdfef9c3ada90512c4
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378939"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Interazioni con oggetti visivi negli oggetti visivi di Power BI

Gli oggetti visivi possono eseguire query sul valore del flag `allowInteractions`, che indica se l'oggetto visivo deve consentire interazioni di oggetti visivi. Ad esempio, gli oggetti visivi sono interattivi durante la visualizzazione o la modifica dei report, ma non lo sono quando vengono visualizzati in un dashboard. Queste interazioni includono *clic*, *panoramica*, *zoom*, *selezione* e altre ancora. 

> [!NOTE]
> È consigliabile abilitare le descrizioni comandi in tutti gli scenari, indipendentemente dal flag indicato.

Il flag `allowInteractions` viene passato come valore booleano durante l'inizializzazione dell'oggetto visivo, come membro dell'interfaccia IVisualHost.

In qualsiasi scenario di Power BI che richiede che gli oggetti visivi non siano interattivi, ad esempio nei riquadri del dashboard, il flag `allowInteractions` viene impostato su `false`. In caso contrario, ad esempio nei report, `allowInteractions` è impostato su `true`.

Per altre informazioni, vedere il [repository dell'oggetto visivo SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

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
