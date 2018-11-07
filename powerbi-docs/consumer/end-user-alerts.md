---
title: 'Esercitazione: Impostare gli avvisi per i dati nel servizio Power BI'
description: In questa esercitazione viene spiegato come impostare gli avvisi per ricevere una notifica quando i dati in un dashboard superano i limiti impostati nel servizio Microsoft Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 10/08/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: ba27b42d6449d38fef2659507f035144c67f23fd
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223215"
---
# <a name="tutorial-set-data-alerts-in-power-bi-service"></a>Esercitazione: Impostare gli avvisi per i dati nel servizio Power BI
Impostare gli avvisi per ricevere una notifica quando i dati nei dashboard superano i limiti impostati. 

È possibile impostare avvisi per i riquadri se si ha una licenza Power BI Pro o se un dashboard è stato condiviso con l'utente da una [capacità Premium](../service-premium.md). Gli avvisi possono essere impostati solo in riquadri aggiunti da oggetti visivi del report e solo su misuratori, indicatori KPI e schede. Gli avvisi possono essere impostati sugli oggetti visivi creati da set di dati di streaming aggiunti da un report, ma non possono essere impostati nei riquadri di streaming creati direttamente nel dashboard tramite **Aggiungi riquadro** > **Dati in streaming personalizzati**. 

Gli avvisi possono essere visualizzati solo da chi li imposta, anche se si condivide il dashboard. Gli avvisi per i dati sono completamente sincronizzati sulle piattaforme. È possibile quindi impostare e visualizzare gli avvisi per i dati [nell'app Power BI per dispositivi mobili](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) e nel servizio Power BI. 

![Riquadri](../media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Le notifiche di avviso basate sui dati forniscono informazioni sui dati. Se il dispositivo sul quale si visualizzano i dati di Power BI viene rubato, è consigliabile disattivare tutte le regole di avviso basate sui dati usando il servizio Power BI.
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

## <a name="set-data-alerts-in-power-bi-service"></a>Impostare gli avvisi per i dati nel servizio Power BI
Il video seguente mostra come aggiungere alcuni avvisi ai riquadri del dashboard. Seguire quindi tutte le istruzioni riportate sotto il video per provare a farlo da soli.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

Questo esempio usa un riquadro di tipo scheda dal dashboard [Esempio di analisi delle vendite al dettaglio](http://go.microsoft.com/fwlink/?LinkId=529778).

1. Selezionare i puntini di sospensione da un riquadro del misuratore, dell'indicatore KPI o della scheda del dashboard.
   
   ![Riquadro Total stores (Totale negozi)](media/end-user-alerts/powerbi-card.png)
2. Selezionare l'icona a forma di campana ![icona di avviso](media/end-user-alerts/power-bi-bell-icon.png) o **Gestisci avvisi** per aggiungere uno o più avvisi per **Total stores**.
   
1. Nel riquadro **Gestisci avvisi** selezionare **+ Aggiungi regola di avviso**.  Verificare che il dispositivo di scorrimento sia impostato su **Attivo** e assegnare un titolo all'avviso. I titoli consentono di riconoscere facilmente gli avvisi.
   
   ![Finestra Gestisci avvisi](media/end-user-alerts/powerbi-alert-title.png)
4. Scorrere verso il basso e immettere i dettagli dell'avviso.  In questo esempio viene creato un avviso che notifica una volta al giorno agli utenti se il numero totale di negozi supera 100. Gli avvisi vengono visualizzati nel centro notifiche e Power BI invia anche un messaggio di posta elettronica.
   
   ![Finestra Gestisci avvisi, impostare la soglia](media/end-user-alerts/power-bi-set-alert-details.png)
5. Selezionare **Salva e chiudi**.

## <a name="receiving-alerts"></a>Ricezione di avvisi
Quando i dati rilevati raggiungono una delle soglie impostate, vengono eseguite alcune operazioni. In base all'opzione selezionata, Power BI per prima cosa controlla se è trascorsa più di un'ora o più di 24 ore dall'invio dell'ultimo avviso. Se i dati superano la soglia, viene visualizzato un avviso.

Successivamente, Power BI invia un avviso al centro di notifica e, facoltativamente, alla casella di posta elettronica. Ogni avviso contiene un collegamento diretto ai dati. Selezionare il collegamento per visualizzare il riquadro pertinente.  

1. Se è stato impostato anche l'invio di un messaggio di posta elettronica, nella posta in arrivo viene visualizzato un messaggio simile al seguente.
   
   ![Messaggio di avviso](media/end-user-alerts/powerbi-alerts-email.png)
2. Power BI aggiunge un messaggio al **centro notifiche** e una nuova icona di avviso al riquadro applicabile.
   
   ![Icona di notifica nel servizio Power BI](media/end-user-alerts/powerbi-alert-notifications.png)
3. Aprire il centro notifiche per visualizzare i dettagli dell'avviso.
   
    ![Leggere l'avviso](media/end-user-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > Gli avvisi possono essere usati solo con dati aggiornati. Quando i dati vengono aggiornati, Power BI controlla se è impostato un avviso per tali dati. Se i dati raggiungono una soglia di avviso, viene generato un avviso.
   > 
   > 

## <a name="managing-alerts"></a>Gestione degli avvisi
Sono disponibili molti modi per gestire gli avvisi: dal riquadro del dashboard, dal menu Impostazioni di Power BI, da una sezione singola nell'[app Power BI per dispositivi mobili su iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) o nell'[app Power BI per dispositivi mobili per Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Dal riquadro
1. Per modificare o rimuovere un avviso per un riquadro, aprire nuovamente la finestra **Gestisci avvisi** selezionando l'icona a forma di campana ![Icona di avviso](media/end-user-alerts/power-bi-bell-icon.png). Vengono visualizzati tutti gli avvisi impostati per questo riquadro.
   
    ![Finestra Gestisci avvisi](media/end-user-alerts/powerbi-see-alerts.png).
2. Per modificare un avviso, selezionare la freccia a sinistra del nome dell'avviso.
   
    ![Freccia accanto al nome dell'avviso](media/end-user-alerts/powerbi-see-alerts-arrow.png).
3. Per eliminare un avviso, selezionare il cestino a destra del nome dell'avviso.
   
      ![Icona a forma di cestino selezionata](media/end-user-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Dal menu Impostazioni di Power BI
1. Selezionare l'icona dell'ingranaggio dalla barra dei menu di Power BI.
   
    ![Icona a forma di ingranaggio](media/end-user-alerts/powerbi-gear-icon.png).
2. In **Impostazioni** selezionare **Avvisi**.
   
    ![Scheda Avvisi della finestra Impostazioni](media/end-user-alerts/powerbi-alert-settings.png)
3. Da qui è possibile attivare e disattivare gli avvisi, aprire la finestra **Gestisci avvisi** per apportare modifiche o eliminare l'avviso.

## <a name="tips-and-troubleshooting"></a>Suggerimenti e risoluzione dei problemi
* Gli avvisi non sono attualmente supportati per i riquadri Bing o di tipo scheda con misure di data/ora.
* Gli avvisi possono essere usati solo con tipi di dati numerici.
* Gli avvisi possono essere usati solo con dati aggiornati. Non possono essere usati con dati statici.
* Gli avvisi funzioneranno nei set di dati di streaming solo se si crea un oggetto visivo del report di tipo indicatore KPI/scheda/misuratore e quindi si aggiunge l'oggetto visivo al dashboard.

## <a name="clean-up-resources"></a>Pulire le risorse
Le istruzioni per l'eliminazione degli avvisi sono illustrate in precedenza. In breve, selezionare l'icona dell'ingranaggio dalla barra dei menu di Power BI. In **Impostazioni** selezionare **Avvisi** ed eliminare l'avviso.

> [!div class="nextstepaction"]
> [Impostare gli avvisi per i dati nel dispositivo mobile](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


