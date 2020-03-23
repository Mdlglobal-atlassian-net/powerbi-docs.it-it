---
title: API di archiviazione locale negli oggetti visivi di Power BI
description: Questo articolo descrive come usare l'API degli oggetti visivi di Power BI per ottenere l'accesso alla risorsa di archiviazione locale del browser
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: e2cb11ea9be85916e6b5557e7933f6a6b5a7159a
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380595"
---
# <a name="local-storage-api"></a>API di archiviazione locale

L'API di archiviazione locale è un'API che un oggetto visivo personalizzato può usare per richiedere all'host di salvare o caricare dati dalla risorsa di archiviazione del dispositivo. L'archiviazione è isolata, nel senso che l'accesso alla risorsa di archiviazione da parte di tipi di oggetti visivi diversi è separato.

## <a name="sample"></a>Esempio

Se l'oggetto visivo personalizzato deve aumentare il contatore ogni volta che viene chiamato il metodo Update, ma il valore del contatore deve anche essere mantenuto e non reimpostato a ogni avvio dell'oggetto visivo:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Limitazioni e problemi noti

Per impostazione predefinita, l'API di archiviazione locale non è attivata per gli oggetti visivi di Power BI. Se si vuole attivarla per l'oggetto visivo di Power BI, inviare una richiesta al supporto per gli oggetti visivi di Power BI `pbicvsupport@microsoft.com`.  
**Si noti che l'oggetto visivo deve essere disponibile in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) e deve essere [certificato](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
