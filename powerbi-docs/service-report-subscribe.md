---
title: Eseguire la sottoscrizione a report e dashboard per se stessi e altri utenti
description: Informazioni su come sottoscrivere per se stessi e altri utenti uno snapshot di una pagina di report, un dashboard o un report impaginato di Power BI.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/10/2020
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 17e4b259f15afa7caaafbdc32a3f137735d5a9f4
ms.sourcegitcommit: 52177142c3e1f49147dff08fe48600a85a814a2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2020
ms.locfileid: "82944752"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Sottoscrivere per se stessi e altri utenti report e dashboard nel servizio Power BI

È possibile effettuare una sottoscrizione per se stessi e i propri colleghi per le pagine di report, i dashboard e i report impaginati più importanti. Le sottoscrizioni di Power BI tramite posta elettronica consentono di:

- Decidere con che frequenza si vogliono ricevere i messaggi di posta elettronica: giornaliera, settimanale, oraria o mensile o una volta al giorno dopo l'aggiornamento iniziale dei dati.
- Scegliere l'ora in cui si vuole ricevere il messaggio di posta elettronica, se si sceglie la frequenza giornaliera, settimanale, oraria o mensile.
- Configurare 24 sottoscrizioni diverse per ogni report o dashboard di Power BI.  Non sono previsti limiti per il numero di sottoscrizioni che è possibile configurare per i report impaginati.
- Ricevere un messaggio di posta elettronica con un'immagine del report e il collegamento al report nel servizio.  Nei dispositivi mobili con app Power BI installate selezionando questo collegamento si avvia l'app Power BI anziché aprire il report o dashboard nel sito Web di Power BI.
- Includere un allegato del report completo, se si vuole sottoscrive un report impaginato.
- Inviare un messaggio di posta elettronica agli utenti esterni al tenant, se il contenuto di Power BI è ospitato in una capacità Premium.  Gli amministratori possono controllare l'accesso a chi può inviare sottoscrizioni tramite posta elettronica agli utenti esterni sfruttando le impostazioni di controllo della condivisione esterna esistenti nell'interfaccia di amministrazione di Power BI.

![Snapshot tramite posta elettronica del dashboard](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

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

1. Usare il dispositivo di scorrimento giallo per attivare e disattivare la sottoscrizione. Lo spostamento del dispositivo di scorrimento su **No** non comporta l'eliminazione della sottoscrizione. Per eliminare la sottoscrizione, selezionare l'icona a forma di cestino.

2. Il messaggio di posta elettronica è già nella casella **Sottoscrivi**. È possibile aggiungere anche altri indirizzi di posta elettronica nello stesso dominio alla sottoscrizione. Se il report o il dashboard è ospitato in una [capacità Premium](/service-premium-what-is), è possibile eseguire la sottoscrizione per altri indirizzi di posta elettronica singoli e alias di gruppi, indipendentemente dal fatto che siano nel dominio dell'utente o meno. Se il report o dashboard non è ospitato in una capacità Premium, è possibile eseguire la sottoscrizione per altre persone purché abbiano a loro volta una licenza Power BI Pro. Per maggiori dettagli, vedere [Considerazioni e risoluzione dei problemi](#considerations-and-troubleshooting) più avanti.

3. Specificare i dettagli dell'**oggetto** e del **messaggio** di posta elettronica.

4. Selezionare una **Frequenza** per la sottoscrizione:  **Ogni giorno**, **Ogni ora**, **Ogni settimana**, **Ogni mese** o **Dopo l'aggiornamento dei dati (una volta al giorno)** . Per ricevere il messaggio di posta elettronica della sottoscrizione solo in determinati giorni, selezionare **Ogni ora** o **Ogni settimana** e scegliere i giorni desiderati. Ad esempio, se si vuole ricevere il messaggio della sottoscrizione solo nei giorni feriali, selezionare **Ogni settimana** e deselezionare le caselle **Sab** e **Dom**. Se si seleziona **Ogni mese**, immettere il giorno o i giorni del mese nei quali si vuole ricevere il messaggio di posta elettronica di sottoscrizione.

5. Se si sceglie **Ogni giorno**, **Ogni ora**, **Ogni mese** o **Ogni settimana**, è anche possibile scegliere un'**ora pianificata** per la sottoscrizione. L'orario può essere l'ora in punto o l'ora e 15, 30 o 45 minuti. Selezionare mattina (AM) o pomeriggio/sera (PM). È anche possibile specificare il fuso orario. Se si sceglie **Ogni ora**, in **Ora pianificata** selezionare l'orario desiderato per l'avvio della sottoscrizione e l'esecuzione avverrà ogni ora dopo tale orario.

6. Per impostazione predefinita, la data di inizio per la sottoscrizione è la data in cui viene creata. Si ha la possibilità di selezionare una data di fine. Se non viene impostata, la data di fine è automaticamente un anno dopo la data di inizio. È possibile modificarla impostando una data nel futuro (fino all'anno 9999) in qualsiasi momento prima della scadenza della sottoscrizione. Quando una sottoscrizione raggiunge una data di fine, viene interrotta finché non viene riabilitata. Si riceveranno delle notifiche prima della data di fine pianificata in cui viene chiesto se si intende prorogare la sottoscrizione.

    Nella schermata riportata di seguito si noti che quando si sottoscrive un report, viene in realtà eseguita una sottoscrizione a una _pagina_ di report. Per sottoscrivere più di una pagina di un report, selezionare **Aggiungi un'altra sottoscrizione** e selezionare una pagina diversa.
     
    ![Riquadro Sottoscrivi](media/service-report-subscribe/power-bi-subscribe-pane.png)  

1. (Facoltativo) Specificare se includere un collegamento al contenuto in Power BI e se concedere agli utenti l'accesso al contenuto per cui si sta eseguendo la sottoscrizione.  Se si sceglie di includere un collegamento, per un'esperienza ottimale, assicurarsi che tutti gli utenti abbiano accesso al report.
2. Selezionare **Salva e chiudi**. Gli utenti con sottoscrizione ricevono un messaggio di posta elettronica e uno snapshot della pagina di report o del dashboard per la frequenza e l'ora selezionate. In tutto, si possono creare fino a 24 sottoscrizioni per report o dashboard ed è possibile specificare destinatari, frequenze e orari univoci per ogni sottoscrizione. Tutte le sottoscrizioni impostate su **Dopo l'aggiornamento dei dati** per il dashboard o report invieranno ancora un messaggio di posta elettronica dopo il primo aggiornamento pianificato.

    > [!TIP]
    > Se si vuole inviare il messaggio di posta elettronica da una sottoscrizione immediatamente o su richiesta in qualsiasi momento, selezionare **Esegui** per le sottoscrizioni per il dashboard o il report da inviare. Verrà visualizzata la notifica dell'invio di un messaggio di posta elettronica a tutti gli utenti per la sottoscrizione specifica. Questa azione non viene conteggiata per il limite di 24 esecuzioni pianificate al giorno per report o dashboard per la sottoscrizione. Tale esecuzione NON attiva l'aggiornamento dei dati del set di dati sottostante.
    >

## <a name="manage-your-subscriptions"></a>Gestire le sottoscrizioni

La sottoscrizione può essere gestita solo dalla persona che l'ha creata. Per accedere alla schermata per la gestione delle sottoscrizioni, è possibile procedere in due modi. Selezionare **Gestione di tutte le sottoscrizioni** nella finestra di dialogo **Sottoscrivere i messaggi di posta elettronica** (vedere il passaggio 4 precedente). Selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-report-subscribe/power-bi-settings-icon.png) di Power BI nella barra dei menu superiore e scegliere **Impostazioni**.

![Selezionare Impostazioni](media/service-report-subscribe/power-bi-subscribe-settings.png)

Le sottoscrizioni visualizzate variano in base all'area di lavoro attiva. Per vedere contemporaneamente tutte le sottoscrizioni per tutte le aree di lavoro, assicurarsi che **Area di lavoro personale** sia attivo. Per altre informazioni sulle aree di lavoro, vedere [Aree di lavoro in Power BI](service-create-workspaces.md).

![Visualizzare tutte le sottoscrizioni in Area di lavoro personale](media/service-report-subscribe/power-bi-subscriptions.png)

Una sottoscrizione termina nei casi seguenti:

- La licenza Pro scade.
- Il proprietario elimina il dashboard o il report.
- L'account utente usato per creare la sottoscrizione viene eliminato.

Gli amministratori di Power BI possono usare i log di controllo di Power BI per visualizzare i dettagli relativi alle sottoscrizioni. Tali dettagli includono:

- Autore
- Data creazione
- Contenuto sottoscritto
- Destinatari
- Frequenza
- Autore della modifica
- Data modifica

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

### <a name="general"></a>Generale

- In rare occasioni il recapito delle sottoscrizioni via posta elettronica ai destinatari può richiedere più di quindici minuti. In questo caso è consigliabile eseguire l'aggiornamento dei dati e la sottoscrizione via posta elettronica in momenti diversi per garantire il recapito tempestivo. Se il problema persiste, contattare il supporto di Power BI.
- Per evitare che i messaggi di posta elettronica di sottoscrizione vengano deviati alla cartella della posta indesiderata, aggiungere l'alias di posta elettronica di Power BI ([no-reply-powerbi@microsoft.com](mailto:no-reply-powerbi@microsoft.com)) ai propri contatti. Se si usa Microsoft Outlook, fare clic con il pulsante destro del mouse sull'alias e selezionare **Aggiungi ai contatti di Outlook**.
- Attualmente le sottoscrizioni tramite posta elettronica per report e dashboard che usano connessioni dinamiche non sono supportate per le sottoscrizioni di altri utenti, a eccezione dei report impaginati. È possibile eseguire la sottoscrizione a un report impaginato per altri utenti, usando il contesto di sicurezza. Per altre informazioni, vedere [Sottoscrizione di report impaginati](consumer/paginated-reports-subscriptions.md).
- Power BI sospende automaticamente l'aggiornamento nei set di dati associati ai dashboard e ai report che non vengono visitati da più di due mesi. Tuttavia, se si aggiunge una sottoscrizione a un dashboard o un report, l'aggiornamento non viene sospeso anche nel caso in cui non sia stato visitato.
- Se non si ricevono i messaggi di posta elettronica relativi alla sottoscrizione, assicurarsi che il Nome dell'entità utente sia in grado di ricevere messaggi di posta elettronica.
- Se il dashboard o il report è nella capacità Premium, è possibile usare alias di posta elettronica di gruppo per le sottoscrizioni anziché eseguire le sottoscrizioni per un indirizzo alla volta. Gli alias sono basati sull'istanza corrente di Active Directory.

### <a name="dashboards"></a>Dashboard

- È possibile che i dashboard con più di 25 riquadri aggiunti o più di 4 pagine report dinamiche aggiunte non vengano visualizzati interamente nei messaggi di posta elettronica della sottoscrizione inviati agli utenti. Le sottoscrizioni di dashboard con un numero superiore di riquadri non vengono bloccate. Tuttavia, vengono considerate senza supporto nel caso in cui si verifichino problemi. Considerare la possibilità di modificarli in modo da farli rientrare in un intervallo supportato.
- In rare occasioni il recapito delle sottoscrizioni via posta elettronica ai destinatari può richiedere più di quindici minuti. In questo caso è consigliabile eseguire l'aggiornamento dei dati e la sottoscrizione via posta elettronica in momenti diversi per garantire il recapito tempestivo. Se il problema persiste, contattare il supporto di Power BI.
- Per le sottoscrizioni via posta elettronica dei dashboard, i riquadri a cui è stata applicata la sicurezza a livello di riga non vengono visualizzati.
- Per le sottoscrizioni ai dashboard, alcuni tipi di riquadri non sono ancora supportati, tra cui: riquadri di streaming, riquadri video e riquadri di contenuto Web personalizzato.
- Se si condivide un dashboard con un collega al di fuori del tenant, non è possibile creare anche una sottoscrizione per il collega *a meno che* il dashboard non sia incluso in un'area di lavoro o in un'app Premium. Di conseguenza, se si è aaron@contoso.com è possibile condividere con anyone@fabrikam.com, ma non è possibile sottoscrivere anyone@fabrikam.com che non può sottoscrivere contenuto condiviso.

### <a name="reports"></a>Report

- Per le sottoscrizioni via posta elettronica dei report, gli utenti non possono creare una sottoscrizione da soli se il set di dati usa la sicurezza a livello di riga. Non è possibile sottoscrivere per altri utenti un report a cui è stata applicata la sicurezza a livello di riga, a eccezione dei report impaginati. È possibile eseguire la sottoscrizione a un report impaginato per altri utenti, usando il contesto di sicurezza. Per altre informazioni, vedere [Sottoscrizione di report impaginati](consumer/paginated-reports-subscriptions.md).
- Le sottoscrizioni alle pagine dei report sono associate al nome della pagina del report. Se si sottoscrive una pagina del report e dopo la si rinomina, è necessario ricreare la sottoscrizione.
- L'organizzazione potrebbe configurare determinate impostazioni in Azure Active Directory per limitare la possibilità di usare le sottoscrizioni tramite posta elettronica in Power BI. Queste limitazioni includono, a titolo di esempio, l'autenticazione a più fattori o la presenza di restrizioni dell'intervallo IP quando si accede alle risorse.
- Le sottoscrizioni via posta elettronica non supportano la maggior parte degli [oggetti visivi personalizzati](developer/power-bi-custom-visuals.md). L'unica eccezione è costituita dagli oggetti visivi personalizzati che sono stati [certificati](developer/power-bi-custom-visuals-certified.md).
- Attualmente le sottoscrizioni via posta elettronica non supportano oggetti visivi R personalizzati.
- Le sottoscrizioni tramite posta elettronica vengono inviate con gli stati di filtro e filtro dei dati predefinito del report. Eventuali modifiche ai valori predefiniti apportate dopo la sottoscrizione non vengono visualizzate nel messaggio di posta elettronica. I report impaginati supportano questa funzionalità e consentono di impostare i valori dei parametri specifici per ogni sottoscrizione.

## <a name="next-steps"></a>Passaggi successivi

- [Subscribe yourself and others to a paginated report in the Power BI service](consumer/paginated-reports-subscriptions.md) (Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI)
- Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)    
- [Leggere il post di blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
