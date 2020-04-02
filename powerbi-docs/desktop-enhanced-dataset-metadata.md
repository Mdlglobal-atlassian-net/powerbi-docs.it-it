---
title: Uso dei metadati del set di dati avanzati in Power BI Desktop (anteprima)
description: Questo articolo descrive come usare i metadati dei set di dati avanzati in Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3812f16489d304912ec9574352897e1effb29d4a
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201402"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Uso dei metadati dei set di dati avanzati (anteprima)

Quando Power BI Desktop crea report, crea anche i metadati dei set di dati nei file PBIX e PBIT corrispondenti. In precedenza i metadati venivano archiviati in un formato specifico per Power BI Desktop. Venivano usate origini dati ed espressioni M codificate in base 64 con ipotesi sulla modalità di archiviazione dei metadati.

Con il rilascio della funzionalità dei **metadati dei set di dati avanzati**, molte di queste limitazioni non esistono più. Con la funzionalità dei **metadati dei set di dati avanzati** abilitata, i metadati creati da Power BI Desktop usano un formato simile a quello usato per i modelli tabulari di Analysis Services, basato sul [modello a oggetti tabulare](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La funzionalità dei **metadati dei set di dati avanzati** è strategica e fondamentale, perché le future funzionalità di Power BI saranno sviluppate in base a questi metadati. Alcune funzionalità aggiuntive che traggono vantaggio dai metadati dei set di dati avanzati includono [lettura/scrittura di XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) per la gestione di set di dati di Power BI e la migrazione di carichi di lavoro di Analysis Services a Power BI per sfruttare le funzionalità di prossima generazione.

## <a name="enable-enhanced-dataset-metadata"></a>Abilitare i metadati dei set di dati avanzati

La funzionalità dei **metadati dei set di dati avanzati** è attualmente disponibile in anteprima. Per abilitare i metadati dei set di dati avanzati, in Power BI Desktop selezionare **File > Opzioni e impostazioni > Opzioni > funzionalità di anteprima** e quindi selezionare la casella di controllo **Archivia i set di dati con il formato di metadati avanzato**, come illustrato nella figura seguente. 

![Abilitare la funzionalità di anteprima](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Verrà richiesto di riavviare Power BI Desktop.

![Prompt per il riavvio](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Dopo aver abilitato la funzionalità di anteprima, Power BI Desktop tenta di aggiornare i file PBIX e PBIT che usano il formato dei metadati precedente. 

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

Nella versione di anteprima esistono le limitazioni seguenti quando la funzionalità di anteprima è abilitata.

Quando si apre un file PBIX o PBIT esistente che non è stato aggiornato, l'aggiornamento avrà esito negativo se il set di dati contiene le funzionalità o i connettori seguenti. Nel caso si verifichi, un errore di questo tipo non dovrebbe avere effetti immediati sull'esperienza utente e Power BI Desktop continua a usare il formato dei metadati precedente.

* Script Python
* Connettori personalizzati
* Azure DevOps Server
* Connettore BI
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* ODBC Jethro
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* Espressioni M contenenti determinate combinazioni di caratteri, ad esempio "\\n" nei nomi di colonna
* Quando si usano i set di dati con la funzionalità dei **metadati dei set di dati avanzati** abilitata, le origini dati Single Sign-On (SSO) non possono essere configurate nel servizio Power BI.

Inoltre, i file PBIX e PBIT che sono già stati aggiornati correttamente per l'uso dei **metadati dei set di dati avanzati** *non possono* usare le funzionalità o i connettori sopra indicati nella versione corrente.


## <a name="next-steps"></a>Passaggi successivi

Power BI Desktop offre infinite possibilità. Per altre informazioni sulle capacità disponibili, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Novità in Power BI Desktop](desktop-latest-update.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Tipi di dati in Power BI Desktop](desktop-data-types.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)
