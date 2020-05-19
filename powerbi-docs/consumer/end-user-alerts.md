---
title: 'Esercitazione: Impostare gli avvisi per i dati nei dashboard del servizio Power BI'
description: In questa esercitazione viene spiegato come impostare gli avvisi per ricevere una notifica quando i dati in un dashboard superano i limiti impostati nel servizio Microsoft Power BI.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 04/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 4cad37b9d4a7bf9e74a29312786a02b26fce5463
ms.sourcegitcommit: faa8cfb66e79ea16ba46605f752cc9ca57924d0e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83382762"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Esercitazione: Impostare gli avvisi per i dashboard di Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Impostare gli avvisi per ricevere una notifica quando i dati nei dashboard superano i limiti impostati. Gli avvisi possono essere impostati solo in riquadri aggiunti da oggetti visivi del report e solo su misuratori, indicatori KPI e schede. 

Gli *utenti finali* possono aggiungere avvisi ai riquadri dei dashboard che hanno creato in **Area di lavoro personale**. Gli *utenti finali* possono anche aggiungere avvisi ai riquadri nei dashboard che sono stati condivisi con loro in una [capacità Premium](end-user-license.md). Se si ha una licenza di Power BI Pro, è anche possibile impostare gli avvisi per i riquadri in qualsiasi altra area di lavoro.
Questa funzionalità è ancora in evoluzione, quindi fare riferimento alla [sezione Suggerimenti e risoluzione dei problemi di seguito](#tips-and-troubleshooting).

![riquadro, scheda, indicatore KPI](media/end-user-alerts/card-gauge-kpi.png)

Gli avvisi possono essere visualizzati solo da chi li imposta, anche se si condivide il dashboard. Gli avvisi per i dati sono completamente sincronizzati sulle piattaforme. È possibile quindi impostare e visualizzare gli avvisi per i dati [nell'app Power BI per dispositivi mobili](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) e nel servizio Power BI. 

> [!WARNING]
> Questi avvisi forniscono informazioni sui dati. Se il dispositivo sul quale si visualizzano i dati di Power BI viene rubato, è consigliabile disattivare tutti gli avvisi usando il servizio Power BI.
> 

In questa esercitazione vengono trattati gli argomenti seguenti.
> [!div class="checklist"]
> * Chi può impostare gli avvisi
> * Oggetti visivi che supportano gli avvisi
> * Chi può vedere gli avvisi
> * Funzionamento degli avvisi in Power BI Desktop e per dispositivi mobili
> * Come creare un avviso
> * Dove vengono recapitati gli avvisi

Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

Questo esempio usa un riquadro di tipo scheda del dashboard dall'app di esempio Sales & Marketing. Questa app è disponibile in [Microsoft AppSource](https://appsource.microsoft.com). Per informazioni su come ottenere l'app, vedere [Installare e usare l'app Sales & Marketing](end-user-app-marketing.md).

1. Selezionare i puntini di sospensione da un riquadro del misuratore, dell'indicatore KPI o della scheda del dashboard.
   
   ![riquadro di tipo scheda](media/end-user-alerts/power-bi-cards.png)
2. Selezionare l'icona a forma di campanello ![icona di avviso](media/end-user-alerts/power-bi-bell-icon.png) o **Gestisci avvisi** per aggiungere uno o più avvisi per **% Units market share**.

   ![riquadro di tipo scheda con puntini di sospensione selezionati](media/end-user-alerts/power-bi-ellipses.png)

   
1. Nel riquadro **Gestisci avvisi** selezionare **+ Aggiungi regola di avviso**.  Verificare che il dispositivo di scorrimento sia impostato su **Attivo** e assegnare un titolo all'avviso. I titoli consentono di riconoscere facilmente gli avvisi.
   
   ![Finestra Gestisci avvisi](media/end-user-alerts/power-bi-manage-alert.png)
4. Scorrere verso il basso e immettere i dettagli dell'avviso.  In questo esempio verrà creato un avviso che invia una notifica una volta al giorno se la quota di mercato aumenta fino a 35 o più. Gli avvisi vengono visualizzati nel centro notifiche e Power BI invia anche un messaggio di posta elettronica.
   
   ![Finestra Gestisci avvisi, impostare la soglia](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Selezionare **Salva e chiudi**.
 
   > [!NOTE]
   > Gli avvisi possono essere usati solo con dati aggiornati. Quando i dati vengono aggiornati, Power BI controlla se è impostato un avviso per tali dati. Se i dati raggiungono una soglia di avviso, viene generato un avviso. 
   > 

## <a name="receiving-alerts"></a>Ricezione di avvisi
Quando i dati rilevati raggiungono una delle soglie impostate, vengono eseguite alcune operazioni. In base all'opzione selezionata, Power BI per prima cosa controlla se è trascorsa più di un'ora o più di 24 ore dall'invio dell'ultimo avviso. Se i dati superano la soglia, viene visualizzato un avviso.

Successivamente, Power BI invia un avviso al centro di notifica e, facoltativamente, alla casella di posta elettronica. Ogni avviso contiene un collegamento diretto ai dati. Selezionare il collegamento per visualizzare il riquadro pertinente.  

1. Se è stato impostato anche l'invio di un messaggio di posta elettronica, nella posta in arrivo viene visualizzato un messaggio simile al seguente. Questo è un avviso impostato per un dashboard diverso. Questo dashboard tiene traccia delle attività completate dal team di usabilità.
   
   ![Messaggio di avviso](media/end-user-alerts/power-bi-alert-email.png)
2. Power BI aggiunge un messaggio al **centro notifiche** e una nuova icona di avviso al riquadro applicabile.
   
   ![Icona di notifica nel servizio Power BI](media/end-user-alerts/power-bi-task-alert.png)
3. Aprire il centro notifiche per visualizzare i dettagli dell'avviso.
   
    ![Leggere l'avviso](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Gestione degli avvisi

Sono disponibili molti modi per gestire gli avvisi: Dal riquadro del dashboard, dal menu Impostazioni di Power BI, da un singolo riquadro nell'[app Power BI per dispositivi mobili su iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) o nell'[app Power BI per dispositivi mobili per Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Dal riquadro

1. Per modificare o rimuovere un avviso per un riquadro, aprire nuovamente la finestra **Gestisci avvisi** selezionando l'icona a forma di campana ![Icona di avviso](media/end-user-alerts/power-bi-bell-icon.png). Vengono visualizzati tutti gli avvisi impostati per questo riquadro.
   
    ![Finestra Gestisci avvisi](media/end-user-alerts/power-bi-manage-alerts.png).
2. Per modificare un avviso, selezionare la freccia a sinistra del nome dell'avviso.
   
    ![Freccia accanto al nome dell'avviso](media/end-user-alerts/power-bi-modify-alert.png).
3. Per eliminare un avviso, selezionare il cestino a destra del nome dell'avviso.
   
      ![Icona a forma di cestino selezionata](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Dal menu Impostazioni di Power BI

1. Selezionare l'icona dell'ingranaggio dalla barra dei menu di Power BI.
   
    ![Icona a forma di ingranaggio](media/end-user-alerts/powerbi-gear-icon.png).
2. In **Impostazioni** selezionare **Avvisi**.
   
    ![Scheda Avvisi della finestra Impostazioni](media/end-user-alerts/power-bi-alert-settings.png)
3. Da qui è possibile attivare e disattivare gli avvisi, aprire la finestra **Gestisci avvisi** per apportare modifiche o eliminare l'avviso.

## <a name="tips-and-troubleshooting"></a>Suggerimenti e risoluzione dei problemi 

* Se non è possibile impostare un avviso per un misuratore, un indicatore KPI o una scheda, chiedere assistenza all'amministratore tenant. A volte gli avvisi vengono disattivati o non sono disponibili per il dashboard o per tipi specifici di riquadri del dashboard.
* Gli avvisi possono essere usati solo con dati aggiornati. Non possono essere usati con dati statici. La maggior parte degli esempi forniti da Microsoft è statica. 
* Per poter ricevere e visualizzare contenuto condiviso è necessario avere una licenza di Power BI Pro o Premium. Per altre informazioni, vedere [Quali licenze sono disponibili?](end-user-license.md)
* Gli avvisi possono essere impostati negli oggetti visivi creati da set di dati in streaming aggiunti da un report a un dashboard. Gli avvisi non possono essere impostati nei riquadri in streaming creati direttamente nel dashboard usando **Aggiungi riquadro** > **Dati in streaming personalizzati**.


## <a name="clean-up-resources"></a>Pulire le risorse
Le istruzioni per l'eliminazione degli avvisi sono illustrate in precedenza. In breve, selezionare l'icona dell'ingranaggio dalla barra dei menu di Power BI. In **Impostazioni** selezionare **Avvisi** ed eliminare l'avviso.

> [!div class="nextstepaction"]
> [Impostare gli avvisi per i dati nel dispositivo mobile](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


