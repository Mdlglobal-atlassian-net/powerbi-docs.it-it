---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 02/15/2019
ms.author: mblythe
ms.openlocfilehash: 44ef0aa9d436f3a8a02f9a6b831847d5c996558a
ms.sourcegitcommit: 91ac6185f7026ddbaa925dc54057bb742b4fa411
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333868"
---
## <a name="limitations"></a>Limitazioni

Di seguito è riportato un elenco delle limitazioni correnti per la sicurezza a livello di riga nei modelli cloud.

* Se in precedenza sono stati definiti ruoli e regole nel servizio Power BI, sarà necessario crearli di nuovo in Power BI Desktop.

* È possibile definire la sicurezza a livello di riga solo per i set di dati creati con Power BI Desktop. Se si vuole abilitare la sicurezza a livello di riga per i set di dati creati con Excel, prima di tutto è necessario convertire i file in file di Power BI Desktop (con estensione pbix). [Altre informazioni](../desktop-import-excel-workbooks.md)

* Sono supportate solo le connessioni ETL e DirectQuery. Le connessioni dinamiche ad Analysis Services vengono gestite nel modello locale.

* Al momento l'uso di Cortana non è supportato con Sicurezza a livello di riga.

## <a name="known-issues"></a>Problemi noti

Esiste un problema noto per cui si riceve un messaggio di errore quando si prova a pubblicare un report già pubblicato in precedenza da Power BI Desktop. Lo scenario è come indicato di seguito.

1. Anna ha un set di dati che è pubblicato nel servizio Power BI e per il quale è configurata la sicurezza a livello di riga.

1. Anna aggiorna il report in Power BI Desktop e ripete l'operazione di pubblicazione.

1. Anna riceve un errore.

**Soluzione alternativa:** ripetere la pubblicazione del file di Power BI Desktop dal servizio Power BI fino a quando non viene risolto il problema. A tale scopo, selezionare **Recupera dati** > **File**.
