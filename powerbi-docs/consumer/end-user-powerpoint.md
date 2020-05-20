---
title: Esportare report interi in PowerPoint
description: Informazioni su come esportare un report di Power BI in PowerPoint.
author: mihart
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/12/2020
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: f70c41e40ff2da385b2f63798b93dec3fcd7b7c5
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565742"
---
# <a name="export-reports-to-powerpoint"></a>Esportare report in PowerPoint

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


Con il servizio Power BI (app.powerbi.com) è possibile pubblicare il report in Microsoft PowerPoint e creare facilmente una presentazione basata su un report di Power BI. Quando si esporta in PowerPoint, si verifica quanto segue:

* Ogni pagina nel report di Power BI diventa una singola diapositiva di PowerPoint.
* Ogni pagina nel report di Power BI viene esportata come singola immagine ad alta risoluzione in PowerPoint.
* È possibile mantenere le impostazioni di filtri e filtri dei dati aggiunte al report.
* In PowerPoint viene creato un collegamento che indirizza al report di Power BI.

Esportare il **report di Power BI** in **PowerPoint** è veloce. Seguire i passaggi descritti nella sezione successiva.

È anche possibile copiare un oggetto visivo alla volta dal servizio Power BI e incollarlo in PowerPoint (o in qualsiasi altro programma che supporta l'operazione Incolla). Selezionare l'icona **Copia come immagine** per copiare l'oggetto visivo negli Appunti. Aprire quindi PowerPoint e incollare l'oggetto visivo. Per altre informazioni, vedere [Copiare gli oggetti visivi come immagini statiche](../visuals/power-bi-visualization-copy-paste.md).

![Selezionare l'icona Copia come immagine](media/end-user-powerpoint/power-bi-copy.png)

## <a name="export-your-power-bi-report-to-powerpoint"></a>Esportare il report di Power BI in PowerPoint
Nel **servizio Power BI** selezionare un report per visualizzarlo nel canvas. È anche possibile selezionare un report da **Home**, da **App** o da qualsiasi altro contenitore del riquadro di spostamento.

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Quando il report da esportare in PowerPoint è visualizzato nell'area di disegno, selezionare **Esporta** > **PowerPoint** dalla barra dei menu.

![Selezionare Esporta dalla barra dei menu](media/end-user-powerpoint/power-bi-export.png)

Viene visualizzata una finestra popup in cui è possibile selezionare **Valori correnti** oppure **Valori predefiniti**. **Valori correnti** consente di esportare il report nello stato corrente, comprese le modifiche attive apportate ai valori del filtro dei dati e del filtro.  La maggior parte degli utenti seleziona questa opzione. Se è stato eseguito lo scorrimento, in **Valori correnti** non è incluso lo stato di scorrimento dell'oggetto visivo, ma viene esportata la parte superiore dei dati. In alternativa, se si seleziona **Valori predefiniti**, il report viene esportato nello stato originale, ovvero come è stato condiviso dal *progettista*, e non riflette le eventuali modifiche apportate rispetto a tale stato.

![Selezionare l'elemento da esportare](media/end-user-powerpoint/power-bi-current-values.png)
 
È anche disponibile una casella di controllo per scegliere se esportare le schede nascoste di un report. Selezionare questa casella di controllo se si vogliono esportare solo le schede dei report visibili per l'utente nel browser. Se si preferisce includere tutte le schede nascoste nell'esportazione, lasciare deselezionata questa casella di controllo. Se la casella di controllo è disattivata, non sono presenti schede nascoste nel report. Un esempio di scheda nascosta è quella di descrizione comando. Le [descrizioni comando personalizzate](../create-reports/desktop-tooltips.md) vengono create dai *progettisti* dei report e non vengono visualizzate come schede dei report nel servizio Power BI per gli *utenti finali*. 

Dopo aver eseguito le selezioni, selezionare **Esporta** per continuare. Nell'angolo in alto a destra della finestra del browser del servizio Power BI verrà visualizzato un banner di notifica che informa che si sta esportando il report in PowerPoint. 



![Notifica dell'esportazione in PowerPoint in corso](media/end-user-powerpoint/power-bi-export-progress.png)

L'esportazione potrebbe richiedere alcuni minuti. I fattori che possono influire sul tempo necessario includono la struttura del report e il carico corrente del servizio Power BI. È possibile continuare a lavorare in Power BI durante l'esportazione del report.

Al termine della procedura, il banner di notifica cambia, informando che il servizio Power BI ha terminato il processo di esportazione. Il file sarà quindi disponibile nel percorso in cui il browser visualizza i file scaricati. Nella figura seguente, è visualizzato come banner di download nella parte inferiore della finestra del browser.

![notifica del browser, nella parte inferiore della schermata](media/end-user-powerpoint/power-bi-browsers.png)

E questo è tutto. È possibile scaricare il file, aprirlo con PowerPoint e quindi modificarlo o migliorarlo come si farebbe con qualsiasi altra presentazione di PowerPoint.

## <a name="open-the-powerpoint-file"></a>Aprire il file di PowerPoint
Quando si apre il file di PowerPoint esportato da Power BI, si noteranno alcuni elementi interessanti e utili. Osservare l'immagine seguente, quindi osservare gli elementi numerati che descrivono alcune delle funzionalità più interessanti. Le pagine in PowerPoint vengono create sempre nel formato standard 9:16, a prescindere dalle dimensioni originali della pagina nel report di Power BI.

![PowerPoint viene aperto](media/end-user-powerpoint/power-bi-powerpoint-numbered.png)

1. La prima pagina della presentazione include il nome del report, nonché un collegamento per poter **visualizzare in Power BI** il report su cui è basata.
2. Si ottengono anche alcune informazioni utili sul report. **Ultimo aggiornamento dati** Visualizza la data e l'ora dei dati su cui è basato il report esportato. **Downloaded at** (Data/ora download) indica la data e l'ora in cui il report di Power BI è stato esportato in un file di PowerPoint. L'ora indicata in **Downloaded at** (Data/ora download) è impostata sul fuso orario del computer al momento dell'esportazione.


3. Ogni pagina del report è una diapositiva separata, come mostrato nel riquadro di spostamento. 
4. Il rendering del report pubblicato viene eseguito nella lingua delle impostazioni di Power BI oppure in base alle impostazioni locali del browser. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/end-user-powerpoint/power-bi-settings-icon.png) > **Impostazioni** > **Generale** > **Lingua**. Per altre informazioni, vedere [Lingue e paesi o aree geografiche supportate per Power BI](../fundamentals/supported-languages-countries-regions.md).


Quando si visualizza una singola diapositiva, si noterà che ogni pagina del report è un'immagine indipendente. Lo scorrimento in PowerPoint non è disponibile perché ogni diapositiva è un'immagine statica.

![Schermata che mostra ogni oggetto visivo come immagine separata](media/end-user-powerpoint/power-bi-images.png)

Da questo momento in poi, le operazioni da eseguire con la presentazione di PowerPoint o con qualsiasi immagine ad alta risoluzione sono responsabilità dell'utente.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
Quando si lavora con la funzionalità **Esporta in PowerPoint** è necessario tenere presenti alcune considerazioni e limitazioni.
 

* I [filtri URL](../collaborate-share/service-url-filters.md) non vengono attualmente rispettati quando si sceglie **Valori correnti** per l'esportazione.

* Quando si esporta in PowerPoint, se il report usa un tipo di carattere personalizzato, esso verrà sostituito con un tipo di carattere predefinito.

* I tipi di oggetti visivi seguenti non sono supportati e non verranno esportati in PowerPoint:
   - Gli [oggetti visivi personalizzati non certificati](../developer/visuals/power-bi-custom-visuals-certified.md) non sono supportati. 
   - L'[oggetto visivo ESRI ArcGIS](../visuals/power-bi-visualizations-arcgis.md) non è supportato
   - Gli oggetti visivi R e Python non sono supportati.
   - Le immagini di sfondo verranno ritagliate con l'area di delimitazione del grafico. Si consiglia di rimuovere le immagini di sfondo prima di eseguire l'esportazione in PowerPoint.

* Alcuni report non possono essere esportati. Tra queste sono incluse:
    - I report di proprietà di un utente esterno al dominio del tenant di Power BI, ad esempio un report il cui proprietario è esterno all'organizzazione e che è condiviso con l'utente attivo.
    - Se si condivide un dashboard con un utente esterno all'organizzazione, ovvero quindi con un utente non incluso nel tenant di Power BI, tale utente non può esportare i report associati del dashboard condiviso in PowerPoint. L'utente aaron@contoso.com non può ad esempio condividere con david@cohowinery.com, ma david@cohowinery.com non può esportare i report associati in PowerPoint.
    - I report con più di 30 pagine. Verranno esportate solo le prime 30 pagine.
    - I report esportati in versioni precedenti di PowerPoint.

* Se la voce di menu **Esporta in PowerPoint** non è disponibile nel servizio Power BI, con molta probabilità l'amministratore tenant ha disabilitato questa funzionalità. Per informazioni dettagliate, contattare l'amministratore tenant.
* Il servizio Power BI usa l'impostazione di lingua di Power BI come lingua per l'esportazione in PowerPoint. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/end-user-powerpoint/power-bi-settings-icon.png) > **Impostazioni** > **Generale** > **Lingua**.



## <a name="next-steps"></a>Passaggi successivi
[Copiare gli oggetti visivi come immagini statiche](../visuals/power-bi-visualization-copy-paste.md)    
[Stampare un report](end-user-print.md)
