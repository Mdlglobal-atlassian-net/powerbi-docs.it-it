---
title: API di archiviazione locale negli oggetti visivi di Power BI
description: Questo articolo descrive come usare l'API degli oggetti visivi di Power BI per ottenere l'accesso alla risorsa di archiviazione locale del browser
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 7665f0c8e3c909263f194a0fd54a54ed2a752c8c
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819101"
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

Per impostazione predefinita, l'API di archiviazione locale non è attivata per gli oggetti visivi personalizzati. Se si vuole attivarla per l'oggetto visivo personalizzato, inviare una richiesta al supporto per gli oggetti visivi personalizzati di Power BI all'indirizzo `pbicvsupport@microsoft.com`.  
**Si noti che l'oggetto visivo deve essere disponibile in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) e deve essere [certificato](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
