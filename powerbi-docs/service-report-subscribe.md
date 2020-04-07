---
title: Eseguire la sottoscrizione a report e dashboard per se stessi e altri utenti
description: Informazioni su come sottoscrivere per se stessi e altri utenti uno snapshot di una pagina di report, un dashboard o un report impaginato di Power BI.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/03/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 0804650149f98d7f63315025ffe3f8a1771ac2ef
ms.sourcegitcommit: bcc42e938fa28abe433287fecb9abb28c253b6bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2020
ms.locfileid: "80302736"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Sottoscrivere per se stessi e altri utenti report e dashboard nel servizio Power BI

È possibile effettuare una sottoscrizione per se stessi e i propri colleghi per le pagine di report, i dashboard e i report impaginati più importanti. Power BI invierà uno snapshot alla Posta in arrivo. Indicare a Power BI con che frequenza si vuole ricevere i messaggi di posta elettronica: giornaliera, settimanale, oraria o mensile o una volta al giorno dopo l'aggiornamento iniziale dei dati.  Se si sceglie la frequenza giornaliera, settimanale, oraria o mensile, è possibile scegliere gli orari in cui eseguire la sottoscrizione.  In tutto, è possibile impostare fino a 24 sottoscrizioni diverse per ogni report o dashboard.

![Snapshot tramite posta elettronica del dashboard](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

È possibile creare sottoscrizioni solo nel servizio Power BI. L'utente riceve un messaggio di posta elettronica con uno snapshot della pagina di report o del dashboard, con un collegamento per aprire il report o il dashboard. Nei dispositivi mobili con app Power BI installate selezionando questo collegamento si avvia l'app Power BI anziché aprire il report o dashboard nel sito Web di Power BI.

## <a name="requirements"></a>Requisiti

La **creazione** di una sottoscrizione può essere eseguita da:

- Utenti con una licenza di Power BI Pro
- Gli utenti che visualizzano contenuti in un'app o un'area di lavoro Premium possono inoltre sottoscrivere i contenuti disponibili in tale posizione, anche senza una licenza di Power BI Pro.

Non sono necessarie autorizzazioni per la modifica del contenuto (dashboard o report) per creare una sottoscrizione per se stessi, ma tali autorizzazioni sono obbligatorie se si vuole creare una sottoscrizione per altri. 

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>Sottoscrivere un dashboard, una pagina di report o un report impaginato

Il processo di sottoscrizione a un dashboard, un report o un report impaginato è molto simile. Lo stesso pulsante consente di effettuare la sottoscrizione ai dashboard e ai report del servizio Power BI.

Sottoscrivere i report impaginati è leggermente diverso. Per maggiori dettagli, vedere [Subscribe yourself and others to a paginated report in the Power BI service](consumer/paginated-reports-subscriptions.md) (Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI).
 
![Selezionare l'icona Sottoscrivi](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Aprire il dashboard o il report.
2. Dalla barra dei menu superiore selezionare **Sottoscrivi** oppure selezionare l'icona a forma di busta ![Sottoscrivi](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Icona Sottoscrivi](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. Usare il dispositivo di scorrimento giallo per attivare e disattivare la sottoscrizione.  Lo spostamento del dispositivo di scorrimento sulla posizione **Disattivato** non comporta l'eliminazione della sottoscrizione. Per eliminare la sottoscrizione, selezionare l'icona a forma di cestino.

4. Il messaggio di posta elettronica è già nella casella **Sottoscrivi**. È possibile aggiungere anche altri indirizzi di posta elettronica alla sottoscrizione, ma solo nello stesso dominio. Se il report o dashboard è ospitato nella [capacità Premium](service-premium-what-is.md), è possibile eseguire la sottoscrizione per altri indirizzi di posta elettronica singoli e alias di gruppi. Se il report o dashboard non è ospitato nella capacità Premium, è possibile eseguire la sottoscrizione per altre persone purché abbiano a loro volta una licenza Power BI Pro. Per maggiori dettagli, vedere [Considerazioni e risoluzione dei problemi](#considerations-and-troubleshooting) più avanti. 

5. Specificare i dettagli dell'**oggetto** e del **messaggio** di posta elettronica. 

5. Selezionare una **frequenza** per la sottoscrizione: **Ogni giorno**, **Ogni ora**, **Ogni settimana**, **Ogni mese** o **Dopo l'aggiornamento dei dati (una volta al giorno)** .  Per ricevere il messaggio di posta elettronica della sottoscrizione solo in determinati giorni, selezionare **Ogni ora** o **Ogni settimana** e scegliere i giorni desiderati.  Ad esempio, se si vuole ricevere il messaggio della sottoscrizione solo nei giorni feriali, selezionare **Ogni settimana** e deselezionare le caselle **Sab** e **Dom**.  Se si seleziona **Ogni mese**, immettere il giorno o i giorni del mese per i quali si desidera ricevere il messaggio di posta elettronica di sottoscrizione.  

6. Se si sceglie **Ogni giorno**, **Ogni ora**, **Ogni mese** o **Ogni settimana** è anche possibile scegliere un'**Ora pianificata** per la sottoscrizione.  L'orario può essere l'ora in punto o l'ora e 15, 30 o 45 minuti.  Selezionare mattina (AM) o pomeriggio/sera (PM). È anche possibile specificare il fuso orario.  Se si sceglie **Ogni ora**, in **Ora pianificata** selezionare l'orario desiderato per l'avvio della sottoscrizione e l'esecuzione avverrà ogni ora dopo tale orario.

7. Per impostazione predefinita, la data di inizio per la sottoscrizione è la data in cui viene creata. Si ha la possibilità di selezionare una data di fine. Se non viene impostata, la data di fine è automaticamente un anno dopo la data di inizio. È possibile modificarla impostando una data nel futuro (fino all'anno 9999) in qualsiasi momento prima della scadenza della sottoscrizione. Quando una sottoscrizione raggiunge una data di fine, viene interrotta finché non viene riabilitata. Si riceveranno delle notifiche prima della data di fine pianificata in cui viene chiesto se si intende prorogare la sottoscrizione.    

    Nella schermata riportata di seguito si noti che quando si sottoscrive un report, viene in realtà eseguita una sottoscrizione a una *pagina* di report.  Per sottoscrivere più di una pagina di un report, selezionare **Aggiungi un'altra sottoscrizione** e selezionare una pagina diversa. 
      
   ![Riquadro Sottoscrivi](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. Selezionare **Salva e chiudi**. Gli utenti con sottoscrizione ricevono un messaggio di posta elettronica e uno snapshot della pagina di report o del dashboard per la frequenza e l'ora selezionate. In tutto, si possono creare fino a 24 sottoscrizioni per report o dashboard ed è possibile specificare destinatari, frequenze e orari univoci per ogni sottoscrizione.  Tutte le sottoscrizioni impostate su **Dopo l'aggiornamento dei dati** per il dashboard o report invieranno ancora un messaggio di posta elettronica dopo il primo aggiornamento pianificato.   
      
   > [!TIP]
   > Se si vuole inviare il messaggio di posta elettronica da una sottoscrizione immediatamente o su richiesta in qualsiasi momento, selezionare **Esegui** per le sottoscrizioni per il dashboard o il report da inviare. Verrà visualizzata la notifica dell'invio di un messaggio di posta elettronica a tutti gli utenti per la sottoscrizione specifica.  Questa azione non viene conteggiata per il limite di 24 esecuzioni pianificate al giorno per report o dashboard per la sottoscrizione. Tale esecuzione NON attiva l'aggiornamento dei dati del set di dati sottostante. 
   > 
   > 
   
## <a name="email-languages"></a>Lingue della posta elettronica

Per il messaggio di posta elettronica e lo snapshot viene usata la lingua specificata nelle impostazioni di Power BI (vedere [Lingue e paesi/aree geografiche supportate per Power BI](supported-languages-countries-regions.md)). Se non è definita alcuna lingua, Power BI usa la lingua in base alle impostazioni internazionali nel browser corrente. Per visualizzare o impostare la preferenza per la lingua, selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-report-subscribe/power-bi-settings-icon.png) > **Impostazioni > Generali > Lingua**. 

![Elenco a discesa Lingua](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>Gestire le sottoscrizioni
La sottoscrizione può essere gestita solo dalla persona che l'ha creata.  Per accedere alla schermata per la gestione delle sottoscrizioni, è possibile procedere in due modi.  Selezionare **Gestione di tutte le sottoscrizioni** nella finestra di dialogo **Sottoscrivere i messaggi di posta elettronica** (vedere gli screenshot successivi al passaggio 4). Selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-report-subscribe/power-bi-settings-icon.png) di Power BI nella barra dei menu superiore e scegliere **Impostazioni**.

![Selezionare Impostazioni](media/service-report-subscribe/power-bi-subscribe-settings.png)

Le sottoscrizioni visualizzate variano in base all'area di lavoro attiva.  Per vedere contemporaneamente tutte le sottoscrizioni per tutte le aree di lavoro, assicurarsi che **Area di lavoro personale** sia attivo. Per altre informazioni sulle aree di lavoro, vedere [Workspaces in Power BI](service-create-workspaces.md) (Aree di lavoro in Power BI).

![Visualizzare tutte le sottoscrizioni in Area di lavoro personale](media/service-report-subscribe/power-bi-subscriptions.png)

Una sottoscrizione termina se la licenza Pro scade, il proprietario elimina il dashboard o report o viene eliminato l'account utente usato per creare la sottoscrizione.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

* È possibile che i dashboard con più di 25 riquadri aggiunti o più di 4 pagine report dinamiche aggiunte non vengano visualizzati interamente nei messaggi di posta elettronica della sottoscrizione inviati agli utenti.  Le sottoscrizioni di dashboard con un numero superiore di riquadri non vengono bloccate. Tuttavia, vengono considerate senza supporto nel caso in cui si verifichino problemi. Considerare la possibilità di modificarli in modo da farli rientrare in un intervallo supportato.
* In rare occasioni il recapito delle sottoscrizioni via posta elettronica ai destinatari può richiedere più di quindici minuti. In questo caso è consigliabile eseguire l'aggiornamento dei dati e la sottoscrizione via posta elettronica in momenti diversi per garantire il recapito tempestivo. Se il problema persiste, contattare il supporto di Power BI.
* Per le sottoscrizioni via posta elettronica dei dashboard, i riquadri a cui è stata applicata la sicurezza a livello di riga non vengono visualizzati.  
* Per le sottoscrizioni via posta elettronica dei report, gli utenti non possono creare una sottoscrizione da soli se il set di dati usa la sicurezza a livello di riga. Non è possibile sottoscrivere un report per altri utenti con la sicurezza a livello di riga applicata a meno che non si usi un report impaginato, che consente di inviare la sottoscrizione ad altri utenti usando il proprio contesto di protezione. 
* Le sottoscrizioni alle pagine dei report sono associate al nome della pagina del report. Se si sottoscrive una pagina del report e dopo la si rinomina, è necessario ricreare la sottoscrizione.
* L'organizzazione potrebbe configurare determinate impostazioni in Azure Active Directory per limitare la possibilità di usare le sottoscrizioni tramite posta elettronica in Power BI.  Queste limitazioni includono, a titolo di esempio, l'autenticazione a più fattori o la presenza di restrizioni dell'intervallo IP quando si accede alle risorse.
* Attualmente, le sottoscrizioni di posta elettronica per report e dashboard che usano set di dati con connessione dinamica non sono supportate per altri utenti oltre a se stessi, a meno che non si usi un report impaginato, che consente di inviare la sottoscrizione ad altri utenti usando il proprio contesto di protezione.
* Per le sottoscrizioni di posta elettronica sono supportati solo gli [oggetti visivi predefiniti e certificati di Power BI](developer/visuals/power-bi-custom-visuals.md).  
* Attualmente le sottoscrizioni di posta elettronica non supportano oggetti visivi di Power BI basati su R.  
* Le sottoscrizioni tramite posta elettronica vengono inviate con gli stati di filtro e filtro dei dati predefinito del report. Eventuali modifiche ai valori predefiniti apportate dopo la sottoscrizione non vengono visualizzate nel messaggio di posta elettronica.  I report impaginati supportano questa funzionalità e consentono di impostare i valori dei parametri specifici per ogni sottoscrizione.
* Per le sottoscrizioni ai dashboard, in particolare, alcuni tipi di riquadri non sono ancora supportati,  tra cui: riquadri di streaming, riquadri video, riquadri di contenuto Web personalizzato.     
* Se si condivide un dashboard con un collega al di fuori del tenant, non è possibile creare anche una sottoscrizione per il collega. Di conseguenza, se si è aaron@xyz.com è possibile condividere con anyone@ABC.com, ma non è possibile sottoscrivere anyone@ABC.com che non può sottoscrivere contenuto condiviso.      
* Power BI sospende automaticamente l'aggiornamento nei set di dati associati ai dashboard e ai report che non vengono visitati da più di due mesi.  Tuttavia, se si aggiunge una sottoscrizione a un dashboard o un report, l'aggiornamento non viene sospeso anche nel caso in cui non sia stato visitato.    
* Se non si ricevono i messaggi di posta elettronica relativi alla sottoscrizione, assicurarsi che il Nome dell'entità utente sia in grado di ricevere messaggi di posta elettronica. 
* Se il dashboard o il report è nella capacità Premium, è possibile usare alias di posta elettronica di gruppo per le sottoscrizioni anziché eseguire le sottoscrizioni per un indirizzo alla volta. Gli alias sono basati sull'istanza corrente di Active Directory. 

## <a name="next-steps"></a>Passaggi successivi

- [Subscribe yourself and others to a paginated report in the Power BI service](consumer/paginated-reports-subscriptions.md) (Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI)
- Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)    
- [Leggere il post di blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
