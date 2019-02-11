---
title: Esportare i report in formato PDF
description: Informazioni su come esportare un report di Power BI in formato PDF.
author: mihart
manager: kvivek
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: c18257f1f4e4e3f325c8d4d895e3b6abf88e900c
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794995"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Esportare report da Power BI in PDF
Con Power BI, è possibile pubblicare il report in formato PDF e creare facilmente un documento basato su un report di Power BI. Quando si **esporta in formato PDF** ogni pagina del report di Power BI diventa una singola pagina del documento PDF.

## <a name="how-to-export-your-power-bi-report-to-pdf"></a>Come esportare il report di Power BI in PDF
Nel servizio Power BI selezionare un report per visualizzarlo nell'area di disegno. È anche possibile selezionare un report dalla home page, da App o da qualsiasi altra sezione del riquadro di spostamento a sinistra.

1. Selezionare **File** > **Esporta in PDF** dalla barra dei menu.

    ![Selezionare File nella barra dei menu, freccia rivolta verso Esporta in PDF](media/end-user-pdf/power-bi-export-pdf.png)

    Nell'angolo superiore destro viene visualizzato un indicatore di stato. L'esportazione del report può richiedere alcuni minuti ma consente di continuare a lavorare in Power BI.

    ![Messaggio di stato dell'esportazione](media/end-user-pdf/power-bi-export-message.png)

    Al termine della procedura, il banner di notifica cambia, informando che il servizio Power BI ha terminato il processo di esportazione.

2. Il file sarà quindi disponibile nel percorso in cui il browser visualizza i file scaricati. Nella figura seguente, è visualizzato come banner di download nella parte inferiore della finestra del browser.

    ![Percorso del file scaricato](media/end-user-pdf/power-bi-save-file.png)

E questo è tutto. È possibile scaricare il file e aprirlo con qualsiasi visualizzatore PDF, ad esempio quello disponibile in Microsoft Edge.


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Quando si lavora con la funzionalità **Esporta in PDF** è necessario tenere presenti alcune considerazioni e limitazioni.

- L'interattività durante la sessione, ad esempio l'evidenziazione e il filtro, il drill-down e così via, non è ancora supportata durante l'esportazione in PDF. Nel file PDF esportato gli oggetti visivi originali sono visualizzati così com'erano stati salvati nel report. Se sono stati applicati filtri e filtri dei dati e si vuole conservarli nell'esportazione, salvare il report e quindi eseguire l'esportazione.

* Gli **oggetti visivi R** non sono attualmente supportati. Nel file PDF questi oggetti visivi sono vuoti e visualizzano un messaggio di errore.  

* Gli **oggetti visivi personalizzati** che sono stati **certificati** sono supportati. Per altre informazioni sugli oggetti visivi personalizzati certificati, tra cui come certificare un oggetto visivo personalizzato, vedere [Ottenere la certificazione di un oggetto visivo personalizzato](../power-bi-custom-visuals-certified.md). Gli oggetti visivi personalizzati che non sono stati certificati non sono supportati. Nel file PDF vengono visualizzati con un messaggio di errore.   

* I report con più di 30 pagine attualmente non possono essere esportati.

* Il completamento del processo di esportazione del report in PDF può richiedere alcuni minuti. I fattori che possono influire sul tempo necessario includono la struttura del report e il carico corrente del servizio Power BI.

* Se la voce di menu **Esporta in PDF** non è disponibile nel servizio Power BI, con molta probabilità l'amministratore tenant ha disabilitato questa funzionalità. Per informazioni dettagliate, contattare l'amministratore tenant.

* Le immagini di sfondo verranno ritagliate con l'area di delimitazione del grafico. Si consiglia vivamente di rimuovere le immagini di sfondo prima dell'esportazione in PDF.

* Non è possibile pubblicare in PDF i report di proprietà di un utente esterno al dominio del tenant di Power BI, ad esempio un report il cui proprietario è esterno all'organizzazione e che è condiviso con l'utente attivo.

* Se si condivide un dashboard con un utente esterno all'organizzazione, quindi con un utente non incluso nel tenant di Power BI, tale utente non potrà esportare i report associati del dashboard condiviso in PDF. Se, ad esempio, si è aaron@contoso.com, è possibile condividere con cassie@cohowinery.com, ma cassie@cohowinery.com non può esportare i report associati in PDF.

* Il servizio Power BI usa l'impostazione di lingua di Power BI come lingua per l'esportazione in PDF. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio  **Impostazioni** > **Generali** > **Lingua**.

## <a name="next-steps"></a>Passaggi successivi
[Stampare un report](end-user-print.md)