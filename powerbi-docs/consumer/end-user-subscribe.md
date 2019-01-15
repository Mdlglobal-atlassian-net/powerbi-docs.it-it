---
title: Sottoscrivere i report e i dashboard nel servizio Power BI
description: Informazioni su come effettuare la sottoscrizione per se stessi o altri utenti di uno snapshot di un report e un dashboard di Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 226d36690d2e3e98588802aa1e4fd9d5f7128ef0
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293011"
---
# <a name="subscribe-to-a-report-or-dashboard-in-power-bi-service"></a>Sottoscrivere un report o un dashboard nel servizio Power BI 
Rimanere aggiornati sui dashboard e sui report più importanti non è mai stato così facile. Basta sottoscrivere le pagine dei report e dei dashboard più importanti e Power BI invierà uno snapshot nella posta in arrivo. È possibile indicare con quale frequenza si vogliono ricevere i messaggi di posta da Power BI, da una volta al giorno a una volta alla settimana. 

Per il messaggio di posta elettronica e lo snapshot verrà usata la lingua specificata nelle impostazioni di Power BI (vedere [Lingue e paesi/aree geografiche supportate per Power BI](../supported-languages-countries-regions.md)). Se non è definita alcuna lingua, Power BI usa la lingua in base alle impostazioni internazionali nel browser corrente. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](./media/end-user-subscribe/power-bi-settings-icon.png) > **Impostazioni > Generali > Lingua**. 

![Elenco a discesa Lingua](./media/end-user-subscribe/power-bi-language.png)

Il messaggio di posta elettronica ricevuto includerà un collegamento "Passa al report" o "Passa al dashboard". Nei dispositivi mobili con l'app Power BI installata, selezionando questo collegamento si avvia l'app (anziché l'azione predefinita di apertura del report o del +dashboard nel sito Web di Power BI).


## <a name="requirements"></a>Requisiti
- La **creazione** di una sottoscrizione è una funzionalità di Power BI Pro. 
- Poiché i messaggi di posta elettronica di sottoscrizione vengono inviati solo quando viene aggiornato un set di dati sottostante, le sottoscrizioni non funzionano nei set di dati che non vengono aggiornati.

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Sottoscrivere una pagina di report o dashboard
Il processo di sottoscrizione a un dashboard o un report è molto simile. Lo stesso pulsante consente di effettuare la sottoscrizione ai dashboard e ai report del servizio Power BI.
 
![Selezionare l'icona Sottoscrivi](./media/end-user-subscribe/power-bi-subscribe-orientation.png).

1. Aprire il dashboard o il report.
2. Nella barra dei menu superiore selezionare **Sottoscrivi** oppure l'icona a forma di busta ![Icona Sottoscrivi](./media/end-user-subscribe/power-bi-icon-envelope.png).
   
   ![Icona Sottoscrivi](./media/end-user-subscribe/power-bi-subscribe-icon.png)

3. Usare il dispositivo di scorrimento giallo per attivare e disattivare la sottoscrizione.  Lo spostamento del dispositivo di scorrimento sulla posizione Disattivato non comporta l'eliminazione della sottoscrizione. Per eliminare la sottoscrizione, selezionare l'icona a forma di cestino.

4. Facoltativamente, aggiungere i dettagli del messaggio di posta elettronica. 

    Nelle schermate riportate di seguito si noti che quando si sottoscrive un report, viene in realtà eseguita una sottoscrizione a una *pagina* di report.  Per sottoscrivere più di una pagina di un report, selezionare **Aggiungi un'altra sottoscrizione** e selezionare una pagina diversa. 
      
   ![Finestra Sottoscrivi](./media/end-user-subscribe/power-bi-emails.png)

5. Selezionare **Salva e chiudi** per salvare la sottoscrizione. Si riceverà un messaggio di posta elettronica e uno snapshot del dashboard o della pagina di report ogni volta che viene apportata una modifica a uno dei set di dati sottostanti. Se il dashboard o il report viene aggiornato più di una volta al giorno, il messaggio di posta elettronica viene inviato solo dopo il primo aggiornamento.  
   
   ![Snapshot tramite posta elettronica del dashboard](./media/end-user-subscribe/power-bi-dashboard-email-new.jpg)
   
L'aggiornamento della pagina del report non aggiorna il set di dati. Solo il proprietario del set di dati può aggiornare manualmente un set di dati. Per cercare il nome dei set di dati sottostanti, selezionare **Visualizza elementi correlati** nella barra dei menu superiore.
   
![Set di dati correlati](./media/end-user-subscribe/power-bi-view-related-screen.png)

## <a name="how-the-email-schedule-is-determined"></a>Come determinare la pianificazione di posta elettronica
La tabella seguente descrive la frequenza con cui si riceverà un messaggio di posta elettronica. Tutto dipende dal metodo di connessione del set di dati su cui è basato il dashboard o il report (DirectQuery, Live Connect, importato in Power BI o file di Excel in OneDrive o SharePoint Online) e dalle opzioni di sottoscrizione disponibili e selezionate (giornaliera, settimanale o nessuna).

|  | **DirectQuery** | **Live Connect** | **Aggiornamento pianificato (importazione)** | **File di Excel in OneDrive/SharePoint Online** |
| --- | --- | --- | --- | --- |
| **Con quale frequenza viene aggiornato il report/dashboard?** |Ogni 15m |Power BI controlla ogni 15 minuti e, se il set di dati è stato modificato, il report viene aggiornato. |L'utente seleziona nessuna, giornaliera o settimanale. La frequenza giornaliera può essere fino a 8 volte al giorno. La frequenza settimanale è effettivamente una pianificazione settimanale creata dall'utente, in base alla quale viene impostato l'aggiornamento, da una volta alla settimana a una volta al giorno. |Una volta ogni ora |
| **Quale livello di controllo ha l'utente sulla pianificazione di posta elettronica della sottoscrizione?** |Le opzioni sono: giornaliera o settimanale |Nessuna opzione: all'utente viene inviato un messaggio di posta elettronica se il report viene aggiornato, ma non più di una volta al giorno. |Se la pianificazione dell'aggiornamento è giornaliera, le opzioni sono giornaliera e settimanale.  Se la pianificazione dell'aggiornamento è settimanale, l'unica opzione è settimanale. |Nessuna opzione: all'utente viene inviato un messaggio di posta elettronica ogni volta che il set di dati viene aggiornato, ma non più di una volta al giorno. |

## <a name="manage-your-subscriptions"></a>Gestire le sottoscrizioni
Si possono gestire solo le sottoscrizioni personali. Selezionare **Sottoscrivi** di nuovo e quindi scegliere **Gestisci tutte le sottoscrizioni** (vedere gli screenshot dopo il punto 4 più indietro). 

![Visualizzare tutte le sottoscrizioni in Area di lavoro personale](./media/end-user-subscribe/power-bi-subscriptions.png)

Una sottoscrizione termina se la licenza Pro scade, il dashboard o il report viene eliminato dal proprietario o l'account utente usato per creare la sottoscrizione viene eliminato.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Per le sottoscrizioni tramite posta elettronica ai dashboard, i riquadri a cui è stata applicata la sicurezza a livello di riga non vengono visualizzati.  Per le sottoscrizioni tramite posta elettronica ai report, non sarà possibile creare una sottoscrizione se il set di dati usa la sicurezza a livello di riga.
* Le sottoscrizioni alle pagine dei report sono associate al nome della pagina del report. Se si sottoscrive una pagina del report e la pagina viene rinominata, sarà necessario ricreare la sottoscrizione
* Alcune impostazioni dell'organizzazione possono essere configurate in Azure Active Directory e ciò potrebbe limitare la possibilità di usare le sottoscrizioni tramite posta elettronica in Power BI.  Ciò include, a titolo di esempio, l'autenticazione a più fattori o la presenza di restrizioni dell'intervallo IP quando si accede alle risorse.
* Per le sottoscrizioni tramite posta elettronica nei set di dati con connessione dinamica, si riceveranno messaggi di posta elettronica solo quando vengono modificati i dati. Quindi, se si verifica un aggiornamento ma nessun dato viene modificato, Power BI non invierà alcun messaggio di posta elettronica.
* Le sottoscrizioni tramite posta elettronica non supportano la maggior parte degli [oggetti visivi personalizzati](../power-bi-custom-visuals.md).  L'unica eccezione è costituita dagli oggetti visivi personalizzati che sono stati [certificati](../power-bi-custom-visuals-certified.md).  
* Attualmente le sottoscrizioni tramite posta elettronica non supportano oggetti visivi R personalizzati.  
* I riquadri dei dashboard a cui è stata applicata la sicurezza a livello di riga non vengono visualizzati.
* Le sottoscrizioni tramite posta elettronica vengono inviate con gli stati di filtro e filtro dei dati predefinito del report. Eventuali modifiche ai valori predefiniti apportate dopo la sottoscrizione non vengono visualizzate nel messaggio di posta elettronica.    
* Per le sottoscrizioni ai dashboard, in particolare, alcuni tipi di riquadri non sono ancora supportati,  tra cui: riquadri di streaming, riquadri video, riquadri di contenuto Web personalizzato.     
* Le sottoscrizioni possono non riuscire nei dashboard o nei report con immagini grandi a causa dei limiti delle dimensioni della posta elettronica.    
* Power BI sospende automaticamente l'aggiornamento nei set di dati associati ai dashboard e ai report che non sono stati visitati da più di 2 mesi.  Tuttavia, se si aggiunge una sottoscrizione a un dashboard o un report, l'aggiornamento non verrà sospeso anche nel caso in cui non sia stato visitato.    

## <a name="next-steps"></a>Passaggi successivi
* Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)    
* [Leggere il post di blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

