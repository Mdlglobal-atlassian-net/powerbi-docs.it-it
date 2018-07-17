---
title: Visualizzare e modificare le impostazioni dei parametri di set di dati nel servizio Power BI
description: I parametri di query vengono creati in Power BI Desktop, ma possono essere controllati e aggiornati nel servizio Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965160"
---
# <a name="what-is-a-query-parameter"></a>Che cos'è un parametro di query
I parametri di query vengono aggiunti a Power BI Desktop dagli autori dei report. I parametri consentono di creare porzioni del report in funzione di uno o più *valori* di parametri. Ad esempio, gli autori di report possono creare un parametro che limita i dati a un singolo paese o regione o un parametro che definisce i formati accettabili di alcuni campi come, ad esempio, date, ore e testo.

![Scheda Home con l'opzione Gestisci parametri nel Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Esaminare e modificare i parametri nel servizio Power BI

Una volta definiti i parametri in Desktop, quando il [report viene pubblicato nel servizio Power BI](desktop-upload-desktop-files.md) le impostazioni e le selezioni dei parametri si spostano con quel report. Alcune impostazioni dei parametri possono essere esaminate e modificate nel servizio Power BI: non si tratta dei parametri che limitano i dati disponibili bensì dei parametri che definiscono e descrivono i valori accettabili.

1. Nel servizio Power BI selezionare l'icona a forma di ingranaggio ![icona a forma di ingranaggio](media/service-parameters/power-bi-cog.png) e scegliere **Impostazioni**.

2. Selezionare la scheda per i **set di dati** ed evidenziare un set di dati nell'elenco. 
    
    ![Finestra Impostazioni con la scheda Set di dati selezionata](media/service-parameters/power-bi-select-dataset2.png)

3. Espandere **Parametri**.  Se il set di dati selezionato non ha parametri, verrà visualizzato un messaggio con un collegamento per ottenere altre informazioni sui parametri di query. Ma se per il set di dati sono stati definiti dei parametri, espandendo l'intestazione **Parametri** verranno rivelati tali parametri. 

    ![Finestra Impostazioni con parametri visualizzati](media/service-parameters/power-bi-settings.png)

    Esaminare le impostazioni dei parametri e apportare le modifiche necessarie. I campi in grigio non sono modificabili. 


## <a name="next-steps"></a>Passaggi successivi
Un modo ad hoc per aggiungere parametri semplici consiste nel [modificare l'URL](service-url-filters.md).