---
title: Passare un parametro di report in un URL per un report impaginato - Generatore report di Power BI
description: Questo argomento descrive come passare parametri di report a un report, includendoli nell'URL di un report impaginato.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: b8301ca17559b81d4db132fbeaa0955ce68a4c6e
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762141"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Passare un parametro di report in un URL per un report impaginato in Power BI 

È possibile passare parametri di report a un report, includendoli nell'URL di un report impaginato. Tutti i parametri di query possono avere parametri di report corrispondenti. Pertanto, si passa un parametro di query a un report passando il parametro di report corrispondente. È necessario aggiungere il prefisso `rp:` al nome del parametro, in modo che Power BI lo possa riconoscere nell'URL. 

I parametri di report fanno distinzione tra maiuscole e minuscole e usano questi caratteri speciali: 

- Uno spazio nella parte del parametro dell'URL viene sostituito con un segno più (+).  ad esempio: 

    ```rp:Holiday=Christmas+Day```

- Un punto e virgola in una parte qualsiasi della stringa viene sostituito con i caratteri `%3A`.

I browser devono eseguire automaticamente la codifica URL corretta. Non è necessario codificare manualmente i caratteri. 

Per impostare un parametro di report in un URL, usare la sintassi seguente: 

```
rp:parameter=value
```

Ad esempio, per specificare i due parametri "Salesperson" e "State" definiti in un report nell'area di lavoro personale, si userà l'URL seguente: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Per specificare gli stessi due parametri definiti in un report in un'app, è necessario usare l'URL seguente: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Per passare un valore Null per un parametro, usare la sintassi seguente: 

```
parameter:isnull=true
```

ad esempio:

```
rp:SalesOrderNumber:isnull=true
```

Per passare un valore booleano, usare 0 per false e 1 per true. Per passare un valore float, includere il separatore decimale delle impostazioni locali del server.

> [!NOTE]
> Se il report contiene un parametro di report con un valore predefinito e il valore della proprietà **Prompt** è **false** (ovvero, la proprietà **Richiesta all'utente** non è selezionata in Gestione report), non è possibile passare un valore per tale parametro di report in un URL. Ciò consente agli amministratori di impedire agli utenti finali di aggiungere o modificare i valori di determinati parametri del report.

> Power BI non supporta una stringa di query con più di 900 caratteri.  Questo valore può essere superato se si usano parametri URL per visualizzare il report impaginato.  Ciò vale in particolare quando si usano parametri multivalore.

## <a name="additional-examples"></a>Esempi aggiuntivi 

L'esempio di URL seguente include il parametro multivalore "Salesperson". Il formato di un parametro multivalore prevede la ripetizione del nome del parametro per ogni valore. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

L'esempio di URL seguente passa un singolo parametro di SellStartDate con il valore "7/1/2005", per un server di report in modalità nativa.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Passaggi successivi

- [Parametri URL nei report impaginati in Power BI](report-builder-url-parameters.md)
- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
