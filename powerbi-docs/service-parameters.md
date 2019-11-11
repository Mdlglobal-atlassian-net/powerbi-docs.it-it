---
title: Modificare le impostazioni dei parametri nel servizio Power BI
description: I parametri di query vengono creati in Power BI Desktop, ma possono essere controllati e aggiornati nel servizio Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 656de2cbf318211bf2fe19f15a3867ab183f3173
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871971"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Modificare le impostazioni dei parametri nel servizio Power BI
Gli autori dei report aggiungono i parametri di query ai report in Power BI Desktop. I parametri consentono di creare porzioni del report in funzione di uno o più *valori* di parametri. Ad esempio, un autore di report può creare un parametro che limita i dati a un singolo paese o regione o un parametro che definisce i formati accettabili di alcuni campi come, ad esempio, date, ore e testo.

![Scheda Home con l'opzione Gestisci parametri nel Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Esaminare e modificare i parametri nel servizio Power BI

Gli autori di report definiscono i parametri in Desktop. Quando si [pubblica il report nel servizio Power BI](desktop-upload-desktop-files.md), le impostazioni e le selezioni dei parametri rimangono associate al report. È possibile rivedere e modificare le impostazioni di alcuni parametri nel servizio Power BI, ovvero dei parametri che definiscono e descrivono valori accettabili ma non dei parametri che limitano i dati disponibili.

1. Nel servizio Power BI selezionare l'icona a forma di ingranaggio ![icona a forma di ingranaggio](media/service-parameters/power-bi-cog.png) e scegliere **Impostazioni**.

2. Selezionare la scheda per i **set di dati** ed evidenziare un set di dati nell'elenco. 
    
    ![Finestra Impostazioni con la scheda Set di dati selezionata](media/service-parameters/power-bi-select-dataset2.png)

3. Espandere **Parametri**.  Se il set di dati selezionato non ha parametri, verrà visualizzato un messaggio con un collegamento per ottenere altre informazioni sui parametri di query. Ma se per il set di dati sono stati definiti dei parametri, espandendo l'intestazione **Parametri** verranno rivelati tali parametri. 

    ![Finestra Impostazioni con parametri visualizzati](media/service-parameters/power-bi-settings.png)

    Esaminare le impostazioni dei parametri e apportare le modifiche necessarie. I campi disattivati non sono modificabili. 


## <a name="next-steps"></a>Passaggi successivi
Un modo ad hoc per aggiungere parametri semplici consiste nel [modificare l'URL](service-url-filters.md).