---
title: Impostare le visualizzazioni per i report impaginati - Power BI
description: In questo articolo vengono illustrate le diverse visualizzazioni disponibili per i report impaginati nel servizio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: ''
ms.topic: conceptual
ms.date: 05/14/2020
ms.openlocfilehash: 3816cfe4e1b61b9445e16d7c322c5ba19aa2bc3d
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407933"
---
# <a name="set-report-views-for-paginated-reports-in-the-power-bi-service"></a>Impostare le visualizzazioni per i report impaginati nel servizio Power BI

Quando si esegue il rendering di un report impaginato nel servizio Power BI, la visualizzazione predefinita è basata su HTML e interattiva. Un'altra visualizzazione report per i formati di pagina fissa, ad esempio PDF, è la nuova opzione Visualizzazione pagina.

**Visualizzazione interattiva predefinita**

![Visualizzazione predefinita](media/page-view/power-bi-paginated-default-view.png)

**Visualizzazione pagina**

![Visualizzazione pagina](media/page-view/power-bi-paginated-page-view.png)

In Visualizzazione pagina il report di cui viene eseguito il rendering è diverso rispetto alla visualizzazione predefinita. Alcune proprietà e concetti nei report impaginati si applicano solo alle pagine fisse. La visualizzazione è simile a quella di un report stampato o esportato. È comunque possibile modificare alcuni elementi, come i valori dei parametri, ma non sono disponibili altre funzionalità interattive, ad esempio l'ordinamento delle colonne e gli interruttori.

Visualizzazione pagina supporta tutte le funzionalità supportate dal visualizzatore PDF del browser, ad esempio Zoom avanti, Zoom indietro e Adatta alla pagina.

## <a name="switch-to-page-view"></a>Passare a Visualizzazione pagina

Quando si apre un report impaginato, per impostazione predefinita ne viene eseguito il rendering in visualizzazione interattiva. Se il report include parametri, selezionare i parametri, quindi visualizzare il report.

1. Selezionare **Visualizza** sulla barra degli strumenti > **Visualizzazione pagina**.

    ![Passare a Visualizzazione pagina](media/page-view/power-bi-paginated-page-view-dropdown.png)

2. Per modificare le impostazioni della visualizzazione pagina, scegliere **Impostazioni pagina** dal menu **Visualizza** sulla barra degli strumenti. 

    ![Selezionare Impostazioni pagina](media/page-view/power-bi-paginated-page-settings-dropdown.png)
    
    La finestra di dialogo **Impostazioni pagina** contiene opzioni per impostare **Dimensioni pagina** e **Orientamento** per la visualizzazione pagina. Dopo aver applicato le impostazioni della pagina, le stesse opzioni vengono applicate quando si stampa la pagina in un secondo momento.
   
    ![Finestra di dialogo Impostazioni pagina](media/page-view/power-bi-paginated-page-settings-dialog.png)

3. Per tornare alla visualizzazione interattiva, selezionare **Impostazione predefinita** nella casella a discesa **Visualizza**.

## <a name="browser-support"></a>Supporto browser

Visualizzazione pagina è supportata nei browser Google Chrome e Microsoft Edge. Assicurarsi che la visualizzazione di file PDF nel browser sia abilitata. Si tratta dell'impostazione predefinita per questi browser.

Visualizzazione pagina non è supportata in Internet Explorer e in Safari, quindi l'opzione è disabilitata. Non è inoltre supportata nei browser dei dispositivi mobili o nelle app per dispositivi mobili Power BI native.  


## <a name="next-steps"></a>Passaggi successivi

- [Visualizzare un report impaginato nel servizio Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
