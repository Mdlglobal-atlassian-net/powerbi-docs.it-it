---
title: Esportare report da Power BI in PowerPoint
description: Informazioni su come esportare un report di Power BI in PowerPoint.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 8dd9af8b44e74aafb97e3265b9ee1c32a05edc64
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281552"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>Esportare report da Power BI in PowerPoint
Con Power BI, è possibile pubblicare il report in **Microsoft PowerPoint** e creare facilmente una presentazione basata su un report di Power BI. Quando si **esporta in PowerPoint**, si verifica quanto segue:

* Ogni pagina del report di Power BI diventa una singola diapositiva di PowerPoint
* Ogni pagina del report di Power BI viene esportata come singola immagine ad alta risoluzione in PowerPoint<!-- * The filters and slicers settings that you added to the report are preserved. -->
* In PowerPoint viene creato un collegamento che indirizza al report di Power BI 

Esportare il **report di Power BI** in **PowerPoint** è veloce. basta seguire i passaggi descritti nella sezione successiva.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Come esportare i report di Power BI in PowerPoint
Nel servizio Power BI selezionare un report per visualizzarlo nell'area di disegno. È anche possibile selezionare un report dalla pagina **Home**, da **App** o da qualsiasi altra sezione nel riquadro di spostamento a sinistra.

![Selezionare File nella barra dei menu, freccia rivolta verso Esporta in PowerPoint](media/end-user-powerpoint/power-bi-publish.png)

Quando il report da esportare in PowerPoint è visualizzato nell'area di disegno, selezionare **File > Esporta in PowerPoint** dalla barra dei menu nel servizio Power BI.

![Vista ravvicinata della barra di spostamento a sinistra con l'area di lavoro personale selezionata e l'elenco a discesa File selezionato](media/end-user-powerpoint/powerbi_to_powerpoint_1.png)

Nell'angolo in alto a destra della finestra del browser del servizio Power BI verrà visualizzato un banner di notifica che informa che si sta esportando il report in PowerPoint. L'esportazione del report potrebbe richiedere alcuni minuti ed è possibile continuare a lavorare in Power BI.

![notifica dell'esportazione in PowerPoint in corso](media/end-user-powerpoint/powerbi_to_powerpoint_2.png)

Al termine della procedura, il banner di notifica cambia, informando che il servizio Power BI ha terminato il processo di esportazione.

![visualizzazione del messaggio di operazione completata](media/end-user-powerpoint/powerbi_to_powerpoint_3.png)

Il file sarà quindi disponibile nel percorso in cui il browser visualizza i file scaricati. Nella figura seguente, è visualizzato come banner di download nella parte inferiore della finestra del browser.

![freccia rivolta verso la notifica del browser, nella parte inferiore della schermata](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

E questo è tutto. È possibile scaricare il file, aprirlo con PowerPoint e quindi modificarlo o migliorarlo come si farebbe con qualsiasi altra presentazione di PowerPoint.

## <a name="checking-out-your-exported-powerpoint-file"></a>Controllare il file di PowerPoint esportato
Quando si apre il file di PowerPoint esportato da Power BI, si noteranno alcuni elementi interessanti e utili. Osservare l'immagine seguente, quindi vedere di seguito gli elementi numerati che descrivono alcune delle funzionalità più interessanti.

![PowerPoint viene aperto](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. La prima pagina della presentazione include il nome del report, nonché un collegamento per poter **visualizzare in Power BI** il report su cui è basata.
2. Si ottengono anche utili informazioni sul report, inclusi l'*ultimo aggiornamento dei dati* su cui è basato il report esportato e l'ora e la data in cui è stato *scaricato*, cioè l'ora e la data in cui il report di Power BI è stato esportato in un file di PowerPoint.
3. Ogni pagina del report è una diapositiva separata, come mostrato nel riquadro di spostamento a sinistra. 
4. Il rendering del report pubblicato viene eseguito nella lingua delle impostazioni di Power BI oppure in base alle impostazioni locali del browser. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![icona a forma di ingranaggio](media/end-user-powerpoint/power-bi-settings-icon.png) **> Impostazioni > Generali > Lingua**. Per altre informazioni, vedere [Lingue e paesi/aree geografiche supportate per Power BI](../supported-languages-countries-regions.md).
5. La presentazione di PowerPoint include una diapositiva di copertina con l'ora dell'esportazione nel fuso orario corretto.

Quando si passa a una singola diapositiva, si noterà che ogni pagina del report è un'immagine indipendente.

>[!NOTE]
> La disponibilità di un oggetto visivo per ogni pagina di report è un comportamento nuovo. Il comportamento precedente, che forniva un'immagine indipendente per ogni oggetto visivo, non viene più implementato. 
 

![Immagine che mostra che ogni oggetto visivo è un'immagine separata](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

Da questo momento in poi, le operazioni da eseguire con la presentazione di PowerPoint o con qualsiasi immagine ad alta risoluzione sono responsabilità dell'utente.

## <a name="limitations"></a>Limitazioni
Quando si lavora con la funzionalità **Esporta in PowerPoint** è necessario tenere presenti alcune considerazioni e limitazioni.

* L'interattività durante la sessione, come ad esempio l'evidenziazione e il filtro, il drill-down e così via, non è ancora supportata durante l'esportazione in PowerPoint. Il file PowerPoint esportato mostra gli oggetti visivi originali così com'erano stati salvati nel report. Se si vogliono preservare i filtri e i filtri dei dati applicati nell'esportazione, salvare il report e quindi eseguire l'esportazione.
* Gli **oggetti visivi R** non sono attualmente supportati. Tutti questi oggetti visivi vengono esportati come un'immagine vuota in PowerPoint con un messaggio di errore che informa che l'oggetto visivo non è supportato.
* Gli **oggetti visivi personalizzati** che sono stati **certificati** sono supportati. Per altre informazioni sugli oggetti visivi personalizzati certificati, tra cui come certificare un oggetto visivo personalizzato, vedere [Ottenere la certificazione di un oggetto visivo personalizzato](../power-bi-custom-visuals-certified.md). Gli oggetti visivi personalizzati che sono stati certificati non sono supportati e vengono esportati come un'immagine vuota in PowerPoint, con un messaggio di errore che informa che l'oggetto visivo non è supportato.
* I report con più di 30 pagine attualmente non possono essere esportati.
* Il completamento del processo di esportazione del report in PowerPoint potrebbe richiedere alcuni minuti, quindi è consigliabile attendere. I fattori che possono influire sul tempo necessario includono la struttura del report e il carico corrente del servizio Power BI.
* Se la voce di menu **Esporta in PowerPoint** non è disponibile nel servizio Power BI, con molta probabilità l'amministratore tenant ha disabilitato questa funzionalità. Per informazioni dettagliate, contattare l'amministratore tenant.
* Le immagini di sfondo verranno ritagliate con l'area di delimitazione del grafico. Si consiglia vivamente di rimuovere le immagini di sfondo prima dell'esportazione in PowerPoint.
* Le pagine in PowerPoint vengono create sempre nel formato standard 9:16, a prescindere dalle dimensioni originali della pagina nel report di Power BI.
* Non è possibile pubblicare in PowerPoint i report di proprietà di un utente esterno al dominio del tenant di Power BI, ad esempio un report di proprietà di un utente esterno all'organizzazione e condiviso con l'utente attivo.
* Se si condivide un dashboard con un utente esterno all'organizzazione, ovvero quindi con un utente non incluso nel tenant di Power BI, tale utente non potrà esportare i report associati del dashboard condiviso in PowerPoint. Se, ad esempio, si è aaron@contoso.com, è possibile condividere con david@cohowinery.com, ma david@cohowinery.com non può esportare i report associati in PowerPoint.
* Come indicato in precedenza, ogni pagina del report viene esportata come singola immagine nel file di PowerPoint.
* Il servizio Power BI usa l'impostazione di lingua di Power BI come lingua per l'esportazione in PowerPoint. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![icona a forma di ingranaggio](media/end-user-powerpoint/power-bi-settings-icon.png) **> Impostazioni > Generali > Lingua**.
* L'orario **scaricato alle** indicato sulla diapositiva di copertina per il file di PowerPoint esportato è impostata sul fuso orario del computer al momento dell'esportazione.

## <a name="next-steps"></a>Passaggi successivi
[Stampare un report](end-user-print.md)