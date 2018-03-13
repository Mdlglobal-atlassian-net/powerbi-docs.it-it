---
title: Portale di amministrazione di Power BI
description: Il portale di amministrazione consente la gestione del tenant di Power BI nell'organizzazione. Include elementi come le metriche di utilizzo, l'accesso all'interfaccia di amministrazione di Office 365 e le impostazioni.
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/23/2018
ms.author: maghan
LocalizationGroup: Administration
ms.openlocfilehash: 15d1f391ba7a9c32ce1f8abd9620e84f16206e26
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi-admin-portal"></a>Portale di amministrazione di Power BI

Il portale di amministrazione consente la gestione del tenant di Power BI nell'organizzazione. Include elementi come le metriche di utilizzo, l'accesso all'interfaccia di amministrazione di Office 365 e le impostazioni.

La gestione del tenant di Power BI per l'azienda viene eseguita tramite il portale di amministrazione di Power BI. Il portale di amministrazione è accessibile a tutti gli utenti amministratori globali in Office 365 o a cui è stato assegnato il ruolo di amministratore del servizio Power BI. Per altre informazioni sul ruolo di amministratore del servizio Power BI, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md).

Tutti gli utenti vedranno **Portale di amministrazione** sotto all'icona a forma d'ingranaggio. Se gli utenti non sono amministratori, vedranno solo la sezione **Impostazioni Premium** e le capacità per le quali dispongono dei diritti di gestione.

## <a name="how-to-get-to-the-admin-portal"></a>Come accedere al portale di amministrazione

Per ottenere l'accesso al portale di amministrazione di Power BI, l'account deve essere contrassegnato come **Amministratore globale** in Office 365 o in Azure Active Directory o avere ricevuto il ruolo di amministratore del servizio Power BI. Per altre informazioni sul ruolo di amministratore del servizio Power BI, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md). Per accedere al portale di amministrazione di Power BI, eseguire le operazioni seguenti.

1. Selezionare l'icona a forma di ingranaggio delle impostazioni in alto a destra nella pagina del servizio Power BI.
2. Selezionare **Portale di amministrazione**.

![](media/service-admin-portal/powerbi-admin-settings.png)

All'interno del portale sono disponibili sei schede, descritte di seguito.

* [Metriche di utilizzo](#usage-metrics)
* [Utenti](#users)
* [Log di controllo](#audit-logs)
* [Impostazioni tenant](#tenant-settings)
* [Impostazioni Premium](#premium-settings)
* [Codici di incorporamento](#embed-codes)
* [Oggetti visivi dell'organizzazione](#Organization-visuals)

![](media/service-admin-portal/powerbi-admin-landing-page.png)

## <a name="usage-metrics"></a>Metriche di utilizzo
La prima scheda nel portale di amministrazione è **Metriche di utilizzo**. Il report delle metriche di utilizzo offre la possibilità di monitorare l'utilizzo all'interno di Power BI per l'organizzazione. Consente inoltre di vedere quali sono gli utenti e i gruppi più attivi all'interno di Power BI per l'organizzazione.

> [!NOTE]
> Al primo accesso al dashboard o quando si accede di nuovo al dashboard dopo un lungo periodo di inutilizzo, è probabile che venga visualizzata una schermata di caricamento mentre viene caricato il dashboard.

Al termine del caricamento del dashboard verranno visualizzate due sezioni di riquadri. La prima sezione include i dati di utilizzo per i singoli utenti e la seconda sezione ha informazioni simili per i gruppi all'interno dell'organizzazione.

Di seguito è riportata la suddivisione dei dati visualizzati in ogni riquadro:

* Conteggio distinto di tutti i dashboard, i report e i set di dati nell'area di lavoro dell'utente
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* Dashboard più utilizzato in base al numero di utenti che possono accedervi. Ad esempio, se si dispone di un dashboard condiviso con 3 utenti e tale dashboard è stato aggiunto anche a un pacchetto di contenuto a cui sono connessi due utenti diversi, il conteggio sarebbe 6 (1 + 3 + 2)
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Il contenuto più popolare a cui si sono connessi gli utenti. Si tratta di qualsiasi contenuto accessibile per gli utenti tramite il processo Recupera dati, quindi pacchetti di contenuto SaaS, pacchetti di contenuto aziendali, file o database.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Una visualizzazione dei principali utenti in base al numero di dashboard che hanno: sia i dashboard creati da loro che quelli condivisi con loro.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Una visualizzazione dei principali utenti in base al numero di report che hanno.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

La seconda sezione mostra lo stesso tipo di informazioni, ma in base ai gruppi. In questo modo sarà possibile stabilire quali sono i gruppi più attivi all'interno dell'organizzazione e quale tipo di informazioni usano.

Con queste informazioni si ottengono dati analitici reali in merito alla modalità di utilizzo di Power BI all'interno dell'organizzazione ed è possibile individuare gli utenti e i gruppi particolarmente attivi nell'organizzazione.

## <a name="users"></a>Users

La seconda scheda nel portale di amministrazione è **Gestisci utenti**. La gestione degli utenti, per Power BI, viene eseguita nell'interfaccia di amministrazione di Office 365, pertanto questa sezione consente di raggiungere rapidamente l'area per gestire utenti, amministratori e gruppi all'interno di Office 365.

![](media/service-admin-portal/powerbi-admin-manage-users.png)

Facendo clic su **Passa all'interfaccia di amministrazione di O365** si passa direttamente alla pagina di destinazione dell'interfaccia di amministrazione di Office 365 per gestire gli utenti del tenant.

![](media/service-admin-portal/powerbi-admin-o365-admin-center.png)

## <a name="audit-logs"></a>Log di controllo

La terza scheda nel portale di amministrazione è **Log di controllo**. I log si trovano all'interno del Centro sicurezza e conformità di Office 365. Questa sezione consente di accedere rapidamente a tale area all'interno di Office 365. 

Per altre informazioni sui log di controllo, vedere [Controllo di Power BI nell'organizzazione](service-admin-auditing.md)

## <a name="tenant-settings"></a>Impostazioni tenant

La terza scheda nel portale di amministrazione è **Impostazioni tenant**. Le impostazioni del tenant consentono di esercitare un maggiore controllo sulle funzionalità da rendere disponibili per l'organizzazione. Se i dati sensibili rappresentano una criticità, è possibile che alcune delle nostre funzionalità non siano adatte all'organizzazione o che per un determinato gruppo sia preferibile rendere disponibile solo una specifica funzionalità. In questi casi, è possibile disattivare specifiche funzionalità nel tenant.

![](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Possono essere necessari fino a 10 minuti affinché l'impostazione diventi effettiva per tutti gli utenti del tenant.

Le impostazioni possono avere tre stati in base alla configurazione.

### <a name="disabled-for-the-entire-organization"></a>Disabilitato per l'intera organizzazione

È possibile disabilitare una funzionalità e fare in modo che gli utenti non possano usarla.

![](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

### <a name="enabled-for-the-entire-organization"></a>Abilitato per l'intera organizzazione

È possibile abilitare una funzionalità per l'intera organizzazione in modo da renderla accessibile a tutti gli utenti.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

### <a name="enabled-for-a-subset-of-the-organization"></a>Abilitato per un subset dell'organizzazione

È anche possibile abilitare una funzionalità per una parte dell'organizzazione. Questo obiettivo può essere raggiunto in diversi modi. È possibile abilitarla per l'intera organizzazione, ad eccezione di un gruppo specifico di utenti.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

È anche possibile abilitare la funzionalità solo per un gruppo di utenti e disattivarla per un altro gruppo di utenti. In questo modo, alcuni utenti non avrebbero accesso alla funzionalità anche se fanno parte del gruppo autorizzato.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

## <a name="export-and-sharing-settings"></a>Impostazioni di esportazione e condivisione

### <a name="share-content-to-external-users"></a>Condividere contenuto con utenti esterni

Gli utenti dell'organizzazione possono condividere i dashboard con utenti esterni all'organizzazione.

![](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Pubblica sul Web

Gli utenti dell'organizzazione possono pubblicare report sul Web. [Altre informazioni](service-publish-to-web.md)

![](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Gli utenti vedranno opzioni diverse nell'interfaccia utente in base all'impostazione per la pubblicazione sul Web.

|Funzionalità |Abilitata per l'intera organizzazione |Disabilitata per l'intera organizzazione |Gruppi di sicurezza specifici   |
|---------|---------|---------|---------|
|**Pubblica sul Web** nel menu **File** del report.|Abilitata per tutti|Non visibile per tutti|Visibile solo per utenti o gruppi autorizzati.|
|**Gestisci codici di incorporamento** in **Impostazioni**|Abilitata per tutti|Abilitata per tutti|Abilitata per tutti<br><br>Opzione * **Elimina** solo per utenti o gruppi autorizzati.<br>Opzione * **Ottieni i codici** abilitata per tutti.|
|**Incorpora codici** nel portale di amministrazione|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato|Lo stato sarà **Disabilitato**|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato<br><br>Se un utente non è autorizzato in base alla configurazione del tenant, lo stato sarà **Violazione**.|
|Report pubblicati esistenti|Tutti abilitati|Tutti disabilitati|Il rendering di tutti i report viene continuato per tutti.|

### <a name="export-data"></a>Esporta dati

Gli utenti dell'organizzazione possono esportare dati da un riquadro o una visualizzazione. [Altre informazioni](power-bi-visualization-export-data.md)

![](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Se si disabilita **Esporta dati**, si impedisce anche agli utenti di usare la funzionalità **Analizza in Excel** oltre alla connessione dinamica al servizio Power BI.

### <a name="export-reports-as-powerpoint-presentations"></a>Esporta report come presentazioni di PowerPoint

Gli utenti dell'organizzazione possono esportare report di Power BI come file di PowerPoint. [Altre informazioni](service-publish-to-powerpoint.md)

![](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Stampare dashboard e report

Gli utenti dell'organizzazione possono stampare dashboard e report. [Altre informazioni](service-print.md)

![](media/service-admin-portal/powerbi-admin-print-dashboard.png)

![](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-settings"></a>Impostazioni del pacchetto di contenuto

### <a name="publish-content-packs-to-the-entire-organization"></a>Pubblicare pacchetti di contenuto per l'intera organizzazione

Gli utenti dell'organizzazione possono pubblicare pacchetti di contenuto per l'intera organizzazione.

![](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs"></a>Creare pacchetti di contenuto modello aziendali

Gli utenti dell'organizzazione possono creare modelli di pacchetti di contenuto che usano set di dati basati su una sola origine dati in Power BI Desktop.

### <a name="push-apps-to-end-users"></a>Push delle app agli utenti finali

L'amministratore del tenant abilita il push delle app in **Impostazioni tenant**.

   ![Abilitare il push delle app](media/service-create-distribute-apps/power-bi-apps-pushapps01.png)

È possibile configurare l'impostazione **Abilitato** e quindi specificare chi ottiene questa funzionalità, se l'intera organizzazione o gruppi di sicurezza specifici.

> [!NOTE]
> Tenere presente che le modifiche alle impostazioni del tenant possono richiedere tempo per diventare effettive.

Sono disponibili altre informazioni sul [push delle app](service-create-distribute-apps.md#how-to-install-an-app-automatically-for-end-users).

## <a name="integration-settings"></a>Impostazioni di integrazione

### <a name="ask-questions-about-data-using-cortana"></a>Porre domande sui dati tramite Cortana
Gli utenti dell'organizzazione possono porre domande sui dati tramite Cortana.

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Usare Analizza in Excel con set di dati locali
Gli utenti dell'organizzazione possono usare Excel per visualizzare set di dati di Power BI locali e interagire con essi. [Altre informazioni](service-analyze-in-excel.md)

> [!NOTE]
> Se si disabilita l'impostazione **Esporta dati**, gli utenti non potranno usare neanche la funzionalità **Analizza in Excel**.

### <a name="user-arcgis-maps-for-power-bi-preview"></a>Usare Mappe ArcGIS per Power BI (anteprima)

Gli utenti dell'organizzazione possono usare la visualizzazione Mappe ArcGIS per Power BI (anteprima) fornita da Esri. [Altre informazioni](power-bi-visualization-arcgis.md)


## <a name="custom-visuals-settings"></a>Impostazioni degli oggetti visivi personalizzati
### <a name="enable-custom-visuals-for-the-entire-organization"></a>Abilitare oggetti visivi personalizzati per l'intera organizzazione
Gli utenti dell'organizzazione possono interagire con gli oggetti visivi personalizzati e condividerli. [Altre informazioni](power-bi-custom-visuals.md)

![Impostazioni degli oggetti visivi personalizzati](media/service-admin-portal/powerbi-admin-custom-visuals.png)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="r-visuals-settings"></a>Impostazioni degli oggetti visivi R

### <a name="interact-with-an-dshare-r-visuals"></a>Interagire con gli oggetti visivi R e condividerli

Gli utenti dell'organizzazione possono interagire con gli oggetti visivi creati con script R e condividerli. [Altre informazioni](service-r-visuals.md)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="audit-settings"></a>Impostazioni di controllo

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Creare log di controllo per la verifica interna delle attività e la conformità

Gli utenti dell'organizzazione possono usare il controllo per monitorare le azioni eseguite da altri utenti dell'organizzazione in Power BI. [Altre informazioni](service-admin-auditing.md)

Questa impostazione deve essere abilitata per la registrazione delle voci del log di controllo.

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="dashboard-settings"></a>Impostazioni del dashboard

### <a name="data-classification-for-dashboards"></a>Classificazione dati per dashboard

Gli utenti dell'organizzazione possono contrassegnare i dashboard con classificazioni che ne indicano il livello di sicurezza. [Altre informazioni](service-data-classification.md)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="developer-settings"></a>Impostazioni modalità sviluppatore

### <a name="embed-content-in-apps"></a>Incorporare il contenuto nelle app

Gli utenti dell'organizzazione possono incorporare i dashboard e i report di Power BI nelle applicazioni SaaS (Software as a Service). Se si disabilita questa impostazione, si impedisce agli utenti di usare le API REST per incorporare contenuto Power BI nelle loro applicazioni.

## <a name="premium-settings"></a>Impostazioni Premium

La scheda Impostazioni Premium consente di gestire qualsiasi capacità Premium di Power BI acquistata dall'organizzazione. La scheda Impostazioni Premium è visibile a tutti gli utenti dell'organizzazione, ma il suo contenuto è visibile solo agli utenti ai quali è stato assegnato il ruolo di **Amministratore delle capacità** o a un utente che abbia autorizzazioni di assegnazione. Per gli utenti che non hanno autorizzazioni verrà visualizzato il messaggio mostrato di seguito.

![](media/service-admin-portal/premium-settings-no-access.png "Nessun accesso alle impostazioni Premium")

Per altre informazioni sulla gestione delle impostazioni Premium, vedere [Gestione di Power BI Premium](service-admin-premium-manage.md).

## <a name="embed-codes"></a>Codici di incorporamento

![Codici di incorporamento nel portale di amministrazione di Power BI](media/service-admin-portal/embed-codes.png)

Un amministratore può visualizzare i codici di incorporamento generati per il tenant. Sono disponibili le azioni per la visualizzazione del report e l'eliminazione del codice di incorporamento per rimuoverlo.

## <a name="organization-visuals"></a>Oggetti visivi dell'organizzazione

La scheda Oggetti visivi organizzazione consente di distribuire e gestire gli oggetti visivi personalizzati all'interno dell'organizzazione, in modo da poter distribuire facilmente oggetti visivi personalizzati proprietari all'interno dell'organizzazione e consentire agli autori di report di individuare e importare facilmente tali oggetti visivi direttamente da Power BI Desktop nei loro report.
 
La pagina mostra tutti gli oggetti visivi personalizzati attualmente distribuiti nel repository dell'organizzazione.
 
![](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Aggiungere un nuovo oggetto visivo personalizzato

Per aggiungere un nuovo oggetto visivo personalizzato all'elenco, selezionare **Aggiungi un oggetto visivo personalizzato**

![](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

> [!WARNING]
> Un oggetto visivo personalizzato può contenere codice rischioso a livello di sicurezza o privacy. Verificare che l'autore e l'origine dell'oggetto visivo personalizzato siano attendibili prima di distribuirlo nel repository di origine.
> 

Compilare i campi:
 
* Scegli un file con estensione pbiviz (obbligatorio): selezionare un file di oggetto visivo personalizzato da caricare. Sono supportati solo oggetti visivi personalizzati basati su API con controllo della versione (vedere qui cosa significa).
Prima di caricare un oggetto visivo personalizzato è necessario controllarne sicurezza e privacy per assicurarsi che sia conforme agli standard della propria organizzazione. Altre informazioni sulla sicurezza degli oggetti visivi personalizzati.
 
* Nome degli oggetti visivi personalizzati (obbligatorio): assegnare un titolo breve all'oggetto visivo in modo gli utenti di Power BI Desktop ne possano comprendere facilmente gli scopi
 
* Icona (obbligatorio): file dell'icona che verrà visualizzata nell'interfaccia utente di Power BI Desktop.
 
* Descrizione: breve descrizione dell'oggetto visivo per fornire più contesto e informazioni utili all'utente
 
Selezionare "Applica" per avviare la richiesta di caricamento. Se ha esito positivo, il nuovo elemento verrà visualizzato nell'elenco. In caso di esito negativo, verrà visualizzato un messaggio di errore appropriato
 
### <a name="delete-a-custom-visual-from-the-list"></a>Eliminare un oggetto visivo personalizzato dall'elenco

Selezionare l'icona del Cestino per eliminare definitivamente l'oggetto visivo dal repository.
Importante: l'eliminazione è irreversibile. Una volta eliminato, verrà interrotto immediatamente il rendering dell'oggetto visivo nei report esistenti. Anche se si carica lo stesso oggetto visivo nuovamente, questo non sostituirà quello precedente eliminato. Gli utenti dovranno importare nuovamente il nuovo oggetto visivo e sostituire l'istanza presente nei report.
 
### <a name="how-to-update-a-visual"></a>Come aggiornare un oggetto visivo

Se si desidera aggiornare un oggetto visivo nel repository, perché è disponibile una nuova versione dell'oggetto visivo (ad esempio, correzioni di bug, nuove funzionalità e così via), caricare il nuovo file (assicurarsi che l'ID dell'oggetto visivo rimanga invariato) come nuova voce nell'elenco e assicurarsi di specificare i dettagli corretti nel titolo e nella descrizione (ad esempio, "Oggetto visivo personalizzato v 2.0"). Al successivo accesso al repository dell'organizzazione da Power BI Desktop, gli utenti potranno importare la nuova versione e verrà loro richiesto di sostituire la versione corrente disponibile nei report.
 
## <a name="next-steps"></a>Passaggi successivi

[Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md)  
[Controllo di Power BI nell'organizzazione](service-admin-auditing.md)  
[Gestione di Power BI Premium](service-admin-premium-manage.md)  
[Amministrazione di Power BI nell'organizzazione](service-admin-administering-power-bi-in-your-organization.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)