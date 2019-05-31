---
title: "Come aggiungere un'intera pagina del report a un dashboard di Power BI "
description: Documentazione su come aggiungere un'intera pagina dinamica del report a un dashboard di Power BI da un report.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 4a30d01040daffa394ff884c38dda3dd66fa5809
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61140120"
---
# <a name="pin-an-entire-report-page-as-a-live-tile-to-a-power-bi-dashboard"></a>Aggiungere un'intera pagina del report, come riquadro animato, a un dashboard di Power BI
Per aggiungere un nuovo [riquadro del dashboard](consumer/end-user-tiles.md), è anche possibile aggiungere un'intera pagina del report. Questo è un modo semplice per aggiungere più di una visualizzazione contemporaneamente.  Inoltre, quando si aggiunge un'intera pagina, i riquadri sono *animati*. È possibile interagire con essi direttamente nel dashboard. Le modifiche apportate a qualsiasi visualizzazione nell'editor di report, ad esempio l’aggiunta di un filtro o la modifica dei campi utilizzati nel grafico, vengono riflesse anche nel riquadro del dashboard.  

L'aggiunta di riquadri dinamici dai report ai dashboard è disponibile solo nel servizio Power BI (app.powerbi.com).

> [!NOTE]
> Non è possibile aggiungere i riquadri dai report condivisi con l'utente.
> 
> 

## <a name="pin-a-report-page"></a>Aggiungere una pagina del report
Il video seguente mostra come aggiungere una pagina dinamica del report. Seguire quindi le istruzioni dettagliate successive per fare una prova in prima persona.

<iframe width="560" height="315" src="https://www.youtube.com/embed/EzhfBpPboPA" frameborder="0" allowfullscreen></iframe>


1. Aprire un report nella [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md).
2. Senza selezionare alcuna visualizzazione scegliere **Aggiungi pagina dinamica** nella barra dei menu.
   
   ![Icona Aggiungi pagina dinamica](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page.png) 
3. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard. Si noti il testo evidenziato: *L'opzione Aggiungi pagina dinamica consente di visualizzare le modifiche ai report nel riquadro del dashboard quando la pagina viene aggiornata.*
   
   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa. I dashboard che sono stati condivisi con l'utente non saranno presenti nell'elenco a discesa.
   * Nuovo dashboard: digitare il nome del nuovo dashboard.
     
     ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page-dialog.png)
4. Selezionare **Aggiungi oggetto dinamico**. Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che la pagina è stata aggiunta, come riquadro, al dashboard.

## <a name="open-the-dashboard-to-see-the-pinned-live-tile"></a>Aprire il dashboard per visualizzare il riquadro animato bloccato
1. Nel riquadro di spostamento selezionare il dashboard con il nuovo riquadro animato. In quel punto è possibile eseguire operazioni come [rinominare, ridimensionare, collegare e spostare](service-dashboard-edit-tile.md) la pagina del report aggiunta.  
2. Interagire con il riquadro animato.  Nella schermata seguente, se si seleziona una barra nell'istogramma, le altre visualizzazioni nel riquadro vengono evidenziate e filtrate in modo incrociato.
   
    ![Dashboard con un riquadro animato](media/service-dashboard-pin-live-tile-from-report/pbi-live-tile.png)

## <a name="next-steps"></a>Passaggi successivi
[Dashboard in Power BI](consumer/end-user-dashboards.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

