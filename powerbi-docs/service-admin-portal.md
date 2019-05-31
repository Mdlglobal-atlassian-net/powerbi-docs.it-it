---
title: Portale di amministrazione di Power BI
description: Il portale di amministrazione consente la gestione del tenant di Power BI nell'organizzazione. Include elementi come le metriche di utilizzo, l'accesso all'interfaccia di amministrazione di Microsoft 365 e le impostazioni.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 6c9d59bbc2c6bf81242166bef4cd7584f52fb633
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941598"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Amministrazione di Power BI nel portale di amministrazione

Il portale di amministrazione consente di gestire un *tenant* Power BI per l'organizzazione. Il portale include elementi come le metriche di utilizzo, l'accesso all'interfaccia di amministrazione di Microsoft 365 e le impostazioni.

Il portale di amministrazione completo è accessibile a tutti gli utenti amministratori globali in Office 365 o a cui è stato assegnato il ruolo di amministratore del servizio Power BI. Se non si ha uno di questi ruoli, nel portale saranno visualizzate solo le **impostazioni di capacità**. Per altre informazioni sul ruolo di amministratore del servizio Power BI, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Come accedere al portale di amministrazione

Per ottenere l'accesso al portale di amministrazione di Power BI, l'account deve essere contrassegnato come **Amministratore globale** in Office 365 o in Azure Active Directory o avere ricevuto il ruolo di amministratore del servizio Power BI. Per altre informazioni sul ruolo di amministratore del servizio Power BI, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md). Per accedere al portale di amministrazione di Power BI, eseguire le operazioni seguenti.

1. Selezionare l'icona a forma di ingranaggio delle impostazioni in alto a destra nella pagina del servizio Power BI.

1. Selezionare **Portale di amministrazione**.

    ![Impostazioni per il portale di amministrazione](media/service-admin-portal/powerbi-admin-settings.png)

Sono disponibili nove schede nel portale. Il resto di questo articolo fornisce informazioni su ognuna di queste schede.

![Navigazione nel portale di amministrazione](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Metriche di utilizzo](#usage-metrics)
* [Utenti](#users)
* [Log di controllo](#audit-logs)
* [Impostazioni tenant](#tenant-settings)
* [Impostazioni capacità](#capacity-settings)
* [Codici di incorporamento](#embed-codes)
* [Oggetti visivi dell'organizzazione](#organization-visuals)
* [Archiviazione del flusso di dati (anteprima)](#dataflowStorage)
* [Aree di lavoro](#workspaces)

## <a name="usage-metrics"></a>Metriche di utilizzo

La scheda **Metriche di utilizzo** consente di monitorare l'utilizzo di Power BI per l'organizzazione. Consente inoltre di vedere quali sono gli utenti e i gruppi più attivi all'interno di Power BI per l'organizzazione.

> [!NOTE]
> Al primo accesso al dashboard o quando si accede di nuovo al dashboard dopo un lungo periodo di inutilizzo, è probabile che venga visualizzata una schermata di caricamento mentre viene caricato il dashboard.

Al termine del caricamento del dashboard vengono visualizzate due sezioni di riquadri. La prima sezione include i dati di utilizzo per i singoli utenti e la seconda sezione ha informazioni simili per i gruppi all'interno dell'organizzazione.

Di seguito è riportata la suddivisione dei dati visualizzati in ogni riquadro:

* Conteggio distinto di tutti i dashboard, i report e i set di dati nell'area di lavoro dell'utente
  
    ![Conteggio distinto di dashboard, report e set di dati](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* Dashboard più utilizzato in base al numero di utenti che possono accedervi. Ad esempio, se è disponibile un dashboard condiviso con 3 utenti e tale dashboard è stato aggiunto anche a un pacchetto di contenuto a cui sono connessi due utenti diversi, il conteggio sarebbe 6 (1 + 3 + 2)
  
    ![Dashboard più utilizzati](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Il contenuto più popolare a cui si sono connessi gli utenti. Si tratta di qualsiasi contenuto accessibile per gli utenti tramite il processo Recupera dati, quindi pacchetti di contenuto SaaS, pacchetti di contenuto aziendali, file o database.
  
    ![Pacchetti più utilizzati](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Una visualizzazione dei principali utenti in base al numero di dashboard che hanno: sia i dashboard creati da loro che quelli condivisi con loro.
  
    ![Principali utenti - dashboard](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Una visualizzazione dei principali utenti in base al numero di report che hanno.
  
    ![Principali utenti - report](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

La seconda sezione mostra lo stesso tipo di informazioni, ma in base ai gruppi. In questo modo è possibile stabilire quali sono i gruppi più attivi all'interno dell'organizzazione e quale tipo di contenuto usano.

Con queste informazioni è possibile ottenere informazioni dettagliate reali in merito alla modalità d'uso di Power BI all'interno dell'organizzazione ed è possibile individuare gli utenti e i gruppi particolarmente attivi nell'organizzazione.

## <a name="users"></a>Utenti

Gli utenti, i gruppi e gli amministratori di Power BI vengono gestiti nell'interfaccia di amministrazione di Microsoft 365. La scheda **Utenti** offre un collegamento all'interfaccia di amministrazione per il tenant.

![Passare all'interfaccia di amministrazione di Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Log di controllo

I log di controllo di Power BI vengono gestiti nel Centro sicurezza e conformità di Office 365. La scheda **Log di controllo** offre un collegamento al Centro sicurezza e conformità per il tenant. [Altre informazioni](service-admin-auditing.md)

Per usare i log di controllo, assicurarsi che l'impostazione [**Creare log di controllo per la verifica interna delle attività e ai fini della conformità**](#create-audit-logs-for-internal-activity-auditing-and-compliance) sia abilitata.

## <a name="tenant-settings"></a>Impostazioni tenant

La scheda **Impostazioni tenant** consente di controllare in modo dettagliato le funzionalità rese disponibili per l'organizzazione. Se i dati sensibili rappresentano una criticità, è possibile che alcune delle funzionalità non siano adatte all'organizzazione o che per un determinato gruppo sia preferibile rendere disponibile solo una specifica funzionalità.

L'immagine seguente mostra le prime due sezioni della scheda **Impostazioni tenant**.

![Impostazioni tenant](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Possono essere necessari fino a 10 minuti affinché la modifica di un'impostazione diventi effettiva per tutti gli utenti del tenant.

Le impostazioni possono avere tre stati:

* **Disabilitato per l'intera organizzazione**: nessuno all'interno dell'organizzazione può usare questa funzionalità.

    ![Impostazione per disabilitare la funzionalità per tutti](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Abilitato per l'intera organizzazione**: tutti all'interno dell'organizzazione possono usare questa funzionalità.

    ![Impostazione per abilitare la funzionalità per tutti](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Abilitato per un subset dell'organizzazione**: uno specifico subset di utenti o gruppi all'interno dell'organizzazione può usare questa funzionalità.

    È possibile abilitare la funzionalità per l'intera organizzazione, ad eccezione di un gruppo specifico di utenti.

    ![Impostazione per abilitare la funzionalità per un subset](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    È anche possibile abilitare la funzionalità solo per un gruppo specifico di utenti e disabilitarla per un altro gruppo di utenti. Con questo approccio si è certi che alcuni utenti non abbiano accesso alla funzionalità anche se fanno parte del gruppo autorizzato.

    ![Impostazione per abilitare la funzionalità con eccezioni](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

Le sezioni successive forniscono una panoramica dei diversi tipi di impostazioni del tenant.

## <a name="help-and-support-settings"></a>Guida e supporto tecnico di impostazioni

### <a name="publish-get-help-information"></a>Pubblicare le informazioni di "Get-Help"

Gli utenti dell'organizzazione possono passare alla Guida interna e supporta le risorse dal menu della Guida di Power BI. In particolare, questi parametri di modificano il comportamento delle voci di menu Guida fare riferimento alle informazioni della Community e Get.

È anche possibile specificare un URL per indirizzare gli utenti a una soluzione personalizzata per le richieste di licenze. Questo parametro consente di personalizzare l'URL di destinazione del pulsante di aggiornamento di account in grado di trovare un utente senza una licenza Power BI Pro nell'aggiornamento di Power BI Pro nella finestra di dialogo, nonché nella pagina Gestisci archiviazione personale.

## <a name="workspace-settings"></a>Impostazioni dell'area di lavoro

### <a name="create-workspaces"></a>Creare aree di lavoro

Gli amministratori usano il **creare aree di lavoro** impostazione per indicare quali utenti dell'organizzazione possono creare aree di lavoro di app per collaborare su dashboard, report e altro contenuto. Altre informazioni sulle [aree di lavoro app](service-create-the-new-workspaces.md).

Il portale di amministrazione ha un'altra sezione di impostazioni sulle aree di lavoro nel tenant. In questa sezione, è possibile ordinare e filtrare l'elenco delle aree di lavoro e visualizzare i dettagli per ogni area di lavoro. Visualizzare [aree di lavoro](#workspaces) per informazioni dettagliate.

Nel portale di amministrazione, è inoltre controllare quali utenti dispongono delle autorizzazioni per distribuire le App per l'organizzazione. Visualizzare [pubblicare i pacchetti di contenuto e App per l'intera organizzazione](#publish-content-packs-and-apps-to-the-entire-organization) in questo articolo per informazioni dettagliate.

## <a name="export-and-sharing-settings"></a>Impostazioni di esportazione e condivisione

### <a name="share-content-with-external-users"></a>Condividi contenuti con utenti esterni

Gli utenti dell'organizzazione possono condividere i dashboard con utenti esterni all'organizzazione. [Altre informazioni](service-share-dashboards.md#share-a-dashboard-or-report-with-people-outside-your-organization)

![Impostazione per gli utenti esterni](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

La figura seguente mostra il messaggio che viene visualizzato al momento della condivisione con un utente esterno.

![Condivisione con un utente esterno](media/service-admin-portal/powerbi-admin-sharing-external.png)  

### <a name="publish-to-web"></a>Pubblica sul Web

Gli utenti dell'organizzazione possono pubblicare report sul Web. [Altre informazioni](service-publish-to-web.md)

La figura seguente mostra il menu **File** per un report quando l'impostazione **Pubblica sul Web** è abilitata.

![Impostazione Pubblica sul Web](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Gli utenti possono vedere opzioni diverse nell'interfaccia utente in base all'impostazione di **Pubblica sul Web**.

|Feature |Abilitata per l'intera organizzazione |Disabilitata per l'intera organizzazione |Gruppi di sicurezza specifici   |
|---------|---------|---------|---------|
|**Pubblica sul Web** nel menu **File** del report.|Abilitata per tutti|Non visibile per tutti|Visibile solo per utenti o gruppi autorizzati.|
|**Gestisci codici di incorporamento** in **Impostazioni**|Abilitata per tutti|Abilitata per tutti|Abilitata per tutti<br><br>Opzione * **Elimina** solo per utenti o gruppi autorizzati.<br>Opzione * **Ottieni i codici** abilitata per tutti.|
|**Incorpora codici** nel portale di amministrazione|Stato indica una delle opzioni seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato|Stato indica **Disabilitato**|Stato indica una delle opzioni seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato<br><br>Se un utente non è autorizzato in base alla configurazione del tenant, lo stato indica **Violazione**.|
|Report pubblicati esistenti|Tutti abilitati|Tutti disabilitati|Il rendering di tutti i report viene continuato per tutti.|

### <a name="export-data"></a>Esporta dati

Gli utenti dell'organizzazione possono esportare dati da un riquadro o una visualizzazione. [Altre informazioni](visuals/power-bi-visualization-export-data.md)

La figura seguente mostra l'opzione per esportare i dati da un riquadro.

![Esportare dati da un riquadro](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Se si disabilita **Esporta dati**, si impedisce anche agli utenti di usare la funzionalità **Analizza in Excel** oltre alla connessione dinamica al servizio Power BI.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Esporta report come presentazioni di PowerPoint o documenti PDF

Gli utenti dell'organizzazione possono esportare i report di Power BI come file di PowerPoint o documenti PDF. [Altre informazioni](consumer/end-user-powerpoint.md)

La figura seguente illustra il menu **File** per un report quando l'impostazione **Esporta report come presentazioni di PowerPoint o documenti PDF** è abilitata.

![Esporta report come presentazioni di PowerPoint](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Stampare dashboard e report

Gli utenti dell'organizzazione possono stampare dashboard e report. [Altre informazioni](consumer/end-user-print.md)

La figura seguente mostra l'opzione per stampare un dashboard.

![Stampa dashboard](media/service-admin-portal/powerbi-admin-print-dashboard.png)

La figura seguente mostra il menu **File** per un report quando l'impostazione **Stampare dashboard e report** è abilitata.

![Stampare il report](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione
Gli utenti guest B2B di Azure possono modificare e gestire il contenuto dell'organizzazione. [Altre informazioni](service-admin-azure-ad-b2b.md)

L'immagine seguente mostra l'opzione Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione.

![Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

## <a name="content-pack-and-app-settings"></a>Impostazioni dell'app e del pacchetto di contenuto

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Pubblicare pacchetti di contenuto e app per l'intera organizzazione

Gli amministratori di usano questa impostazione per stabilire quali utenti possono pubblicare pacchetti di contenuto e App per l'intera organizzazione, piuttosto che solo determinati gruppi. Altre informazioni sulle [pubblicazione di app](service-create-distribute-apps.md).

La figura seguente mostra l'opzione **Intera organizzazione** quando si crea un pacchetto di contenuto.

![Pubblicare il pacchetto di contenuto per l'organizzazione](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Creare app di modello e pacchetti di contenuto aziendali

Gli utenti dell'organizzazione possono creare modello App e pacchetti di contenuto aziendali che usano set di dati basati su un'origine dati in Power BI Desktop. Altre informazioni sulle [App modello](template-content-pack-authoring.md).

### <a name="push-apps-to-end-users"></a>Push delle app agli utenti finali

Gli autori del report possono condividere le app direttamente con gli utenti finali senza richiedere l'installazione dal [AppSource](https://appsource.microsoft.com). Altre informazioni sulle [automaticamente l'installazione di App per gli utenti finali](service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Impostazioni di integrazione

### <a name="ask-questions-about-data-using-cortana"></a>Porre domande sui dati tramite Cortana

Gli utenti dell'organizzazione possono porre domande sui dati tramite Cortana. [Altre informazioni](service-cortana-enable.md)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Usare Analizza in Excel con set di dati locali

Gli utenti dell'organizzazione possono usare Excel per visualizzare set di dati di Power BI locali e interagire con essi. [Altre informazioni](service-analyze-in-excel.md)

> [!NOTE]
> Se si disabilita l'impostazione **Esporta dati**, gli utenti non possono usare neanche la funzionalità **Analizza in Excel**.

### <a name="use-arcgis-maps-for-power-bi"></a>Usa Mappe ArcGIS per Power BI

Gli utenti dell'organizzazione possono usare la visualizzazione ArcGIS Maps for Power BI offerta da Esri. [Altre informazioni](visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Usa la ricerca globale per Power BI (anteprima)

Gli utenti dell'organizzazione possono usare funzionalità di ricerca esterne basate su Ricerca di Azure. Gli utenti possono ad esempio usare Cortana per recuperare informazioni chiave direttamente dai dashboard e dai report di Power BI. [Altre informazioni](service-cortana-intro.md)

## <a name="custom-visuals-settings"></a>Impostazioni degli oggetti visivi personalizzati

### <a name="add-and-use-custom-visuals"></a>Aggiungi e usa oggetti visivi personalizzati

Gli utenti dell'organizzazione possono interagire con gli oggetti visivi personalizzati e condividerli. [Altre informazioni](power-bi-custom-visuals.md)

> [!NOTE]
> Questa impostazione può essere applicata all'intera organizzazione o limitata a gruppi specifici.


Power BI Desktop (a partire dalla versione del marzo '19) supporta l'utilizzo dei **Criteri di gruppo** per disabilitare l'uso di oggetti visivi personalizzati nei computer distribuiti di un'organizzazione.

<table>
<tr><th>Attributo</th><th>Valore</th>
</tr>
<td>chiave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

Il valore 1 (decimale) abilita l'uso di oggetti visivi personalizzati in Power BI (opzione predefinita).

Il valore 0 (decimale) disabilita l'uso di oggetti visivi personalizzati in Power BI.

### <a name="allow-only-certified-visuals"></a>Consenti solo oggetti visivi personalizzati certificati

Gli utenti dell'organizzazione a cui sono state assegnate le autorizzazioni per aggiungere e usare gli oggetti visivi personalizzati, tramite l'impostazione "Aggiungi e usa oggetti visivi personalizzati", potranno usare solo [oggetti visivi personalizzati certificati](https://go.microsoft.com/fwlink/?linkid=2002010) (gli oggetti visivi non certificati verranno bloccati e verrà visualizzato un messaggio di errore quando vengono usati). 


Power BI Desktop (a partire dalla versione del marzo '19) supporta l'utilizzo dei **criteri di gruppo** per disabilitare l'uso di oggetti visivi personalizzati non certificati nei computer distribuiti di un'organizzazione.

<table>
<tr><th>Attributo</th><th>Valore</th>
</tr>
<td>chiave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

Il valore 1 (decimale) abilita l'uso di oggetti visivi personalizzati non certificati in Power BI (opzione predefinita).

Il valore 0 (decimale) disabilita l'uso di oggetti visivi personalizzati non certificati in Power BI (questa opzione consente solo l'uso di [oggetti visivi personalizzati certificati](https://go.microsoft.com/fwlink/?linkid=2002010)).

## <a name="r-visuals-settings"></a>Impostazioni degli oggetti visivi R

### <a name="interact-with-and-share-r-visuals"></a>Interagire con gli oggetti visivi R e condividerli

Gli utenti dell'organizzazione possono interagire con gli oggetti visivi creati con script R e condividerli. [Altre informazioni](visuals/service-r-visuals.md)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="audit-and-usage-settings"></a>Impostazioni di controllo e utilizzo

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Creare log di controllo per la verifica interna delle attività e la conformità

Gli utenti dell'organizzazione possono usare il controllo per monitorare le azioni eseguite da altri utenti dell'organizzazione in Power BI. [Altre informazioni](service-admin-auditing.md)

Questa impostazione deve essere abilitata per la registrazione delle voci del log di controllo. È possibile che tra l'abilitazione della funzione di controllo e la visualizzazione dei dati di controllo si verifichi un ritardo di un massimo di 48 ore. Se i dati non vengono visualizzati immediatamente, controllare i log di controllo successivamente. Un ritardo simile può verificarsi tra l'assegnazione dell'autorizzazione per la visualizzazione dei log di controllo e l'accesso ai log.

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

### <a name="usage-metrics-for-content-creators"></a>Metriche di utilizzo per i creatori di contenuti

Gli utenti dell'organizzazione possono visualizzare le metriche di utilizzo dei dashboard e dei report creati. [Altre informazioni](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Dati per utente nelle metriche di utilizzo per i creatori di contenuti

Le metriche di utilizzo per i creatori di contenuti esporranno i nomi visualizzati e gli indirizzi di posta elettronica degli utenti che accedono ai contenuti. [Altre informazioni](service-usage-metrics.md)

Per impostazione predefinita, i dati per utente sono abilitati nelle metriche di utilizzo e le informazioni sull'account del creatore di contenuto sono incluse nel report delle metriche. Se non si desidera includere queste informazioni per alcuni o tutti gli utenti, disabilitare la funzionalità per specifici gruppi di sicurezza o per un'intera organizzazione. Le informazioni sull'account verranno quindi visualizzate nel report come *Senza nome*.

## <a name="dashboard-settings"></a>Impostazioni del dashboard

### <a name="data-classification-for-dashboards"></a>Classificazione dati per dashboard

Gli utenti dell'organizzazione possono contrassegnare i dashboard con classificazioni che ne indicano il livello di sicurezza. [Altre informazioni](service-data-classification.md)

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="developer-settings"></a>Impostazioni modalità sviluppatore

### <a name="embed-content-in-apps"></a>Incorporare il contenuto nelle app

Gli utenti dell'organizzazione possono incorporare i dashboard e i report di Power BI nelle applicazioni SaaS (Software as a Service). Se si disabilita questa impostazione, si impedisce agli utenti di usare le API REST per incorporare contenuto Power BI nelle loro applicazioni. [Altre informazioni](developer/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Consenti alle entità servizio di usare le API Power BI

Le app Web registrate in Azure Active Directory (Azure AD) utilizzerà un'entità di servizio assegnati per accedere alle API di Power BI senza utente connesso. Per consentire a un'app per usare l'autenticazione dell'entità servizio relativa entità servizio deve essere incluso in un gruppo di sicurezza consentiti. [Altre informazioni](developer/embed-service-principal.md)

> [!NOTE]
> Le entità servizio ereditano le autorizzazioni per tutte le impostazioni del tenant di Power BI dal relativo gruppo di sicurezza. Per limitare le autorizzazioni, creare un gruppo di sicurezza dedicato per le entità servizio e aggiungerlo all'elenco "Eccetto gruppi di sicurezza specifici" relativo alle impostazioni pertinenti abilitate di Power BI.

## <a name="dataflow-settings"></a>Impostazioni del flusso di dati

### <a name="create-and-use-dataflows"></a>Creare e usare flussi di dati

Gli utenti dell'organizzazione possono creare e usare flussi di dati. Per una panoramica dei flussi di dati, vedere [di preparazione dei dati self-servizi in Power BI](service-dataflows-overview.md). Per abilitare i flussi di dati in una capacità Premium, vedere [Configurare i carichi di lavoro](service-admin-premium-workloads.md).

> [!NOTE]
> Questa impostazione si applica all'intera organizzazione e non può essere limitata a gruppi specifici.

## <a name="template-apps-settings-preview"></a>Impostazioni app modello (anteprima)

Sono due le impostazioni che controllano le app modello. 

![Impostazioni di app modello del portale di amministrazione di Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="create-template-apps-preview"></a>Crea app modello (anteprima)

Gli utenti dell'organizzazione possono creare app di modello. Gli autori di app di modello possono quindi distribuirli ai client esterni all'organizzazione tramite [AppSource](https://appsource.microsoft.com) o altri metodi di distribuzione.

![Portale di amministrazione di Power BI, impostazione Crea app modello](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-preview"></a>Installare le app di modello (anteprima)

Gli utenti dell'organizzazione è possono scaricare e installare le app di modello dal [AppSource](https://appsource.microsoft.com) o un'altra origine.

> [!NOTE]
> Questa impostazione determina quali utenti possono installare le app di modello per i loro account Power BI.

## <a name="capacity-settings"></a>Impostazioni di capacità

### <a name="power-bi-premium"></a>Power BI Premium

La scheda **Power BI Premium** consente di gestire qualsiasi capacità di Power BI Premium (SKU EM o P) acquistata dall'organizzazione. La scheda **Power BI Premium** è visibile per tutti gli utenti dell'organizzazione, ma il suo contenuto è visibile solo per gli utenti ai quali è stato assegnato il ruolo di *Amministratore delle capacità* o a un utente che abbia autorizzazioni di assegnazione. Per gli utenti che non hanno autorizzazioni viene visualizzato il messaggio seguente.

![Nessun accesso alle impostazioni Premium](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

La scheda **Power BI Embedded** consente di visualizzare le capacità di Power BI Embedded (SKU A) acquistate per il cliente. Poiché è possibile acquistare solo SKU di Azure, si [Gestisci capacità incorporate in Azure](developer/azure-pbie-create-capacity.md) dalla **portale di Azure**.

Per altre informazioni su come gestire le impostazioni di Power BI Embedded (SKU) A, vedere [Che cos'è Azure Power BI Embedded](developer/azure-pbie-what-is-power-bi-embedded.md).

## <a name="embed-codes"></a>Codici di incorporamento

Un amministratore può visualizzare i codici di incorporamento generati per il tenant. È anche possibile revocare o eliminare i codici. [Altre informazioni](service-publish-to-web.md)

![Codici di incorporamento nel portale di amministrazione di Power BI](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals">Oggetti visivi dell'organizzazione</a>

La scheda **Oggetti visivi organizzazione** consente di distribuire e gestire gli oggetti visivi personalizzati all'interno dell'organizzazione. Con gli oggetti visivi dell'organizzazione, è possibile distribuire facilmente gli oggetti visivi proprietari nell'organizzazione, che gli autori dei report possono quindi individuare e importare nei report da Power BI Desktop. [Altre informazioni](power-bi-custom-visuals-organization.md)

> [!WARNING]
> Un oggetto visivo personalizzato può contenere codice rischioso a livello di sicurezza o privacy. Verificare che l'autore e l'origine dell'oggetto visivo personalizzato siano attendibili prima di distribuirlo nel repository dell'organizzazione.

La figura mostra tutti gli oggetti visivi personalizzati attualmente distribuiti nel repository di un'organizzazione.

![Oggetti visivi dell'organizzazione](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Aggiungere un nuovo oggetto visivo personalizzato

Per aggiungere un nuovo oggetto visivo personalizzato all'elenco, seguire questa procedura. 

1. Nel riquadro di destra selezionare **Aggiungi un oggetto visivo personalizzato**.

    ![Modulo per gli oggetti visivi personalizzati](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Compilare il modulo **Aggiungi oggetto visivo personalizzato**:

    * **Scegli un file con estensione pbiviz** (obbligatorio): selezionare un file di oggetto visivo personalizzato da caricare. Sono supportati solo oggetti visivi personalizzati basati su API con controllo della versione (vedere qui cosa significa).

    Prima di caricare un oggetto visivo personalizzato è necessario controllarne sicurezza e privacy per assicurarsi che sia conforme agli standard della propria organizzazione.

    * **Assegna un nome all'oggetto visivo personalizzato** (obbligatorio): assegnare un titolo breve all'oggetto visivo in modo gli utenti di Power BI Desktop ne possano comprendere facilmente gli scopi

    * **Icona**: file dell'icona che viene visualizzata nell'interfaccia utente di Power BI Desktop.

    * **Descrizione**: breve descrizione dell'oggetto visivo per fornire più contesto e informazioni utili all'utente

1. Selezionare **Aggiungi** per avviare la richiesta di caricamento. Se ha esito positivo, il nuovo elemento viene visualizzato nell'elenco. In caso di esito negativo, viene visualizzato un messaggio di errore appropriato

### <a name="delete-a-custom-visual-from-the-list"></a>Eliminare un oggetto visivo personalizzato dall'elenco

Per eliminare definitivamente un oggetto visivo, selezionare l'icona del Cestino per l'oggetto visivo nel repository.

> [!IMPORTANT]
> L'eliminazione è irreversibile. Una volta eliminato, viene interrotto immediatamente il rendering dell'oggetto visivo nei report esistenti. Anche se lo stesso oggetto visivo viene caricato nuovamente, non sostituirà quello precedente eliminato. Gli utenti possono tuttavia importare nuovamente il nuovo oggetto visivo e sostituire l'istanza presente nei report.

### <a name="disable-a-custom-visual-in-the-list"></a>Disabilitare un oggetto visivo personalizzato nell'elenco

Per disabilitare l'oggetto visivo dall'archivio dell'organizzazione, selezionare l'icona a forma di ingranaggio. Nella sezione **Accesso** disabilitare l'oggetto visivo personalizzato.

Dopo avere disabilitato l'oggetto visivo, non ne verrà eseguito il rendering nei report esistenti e viene visualizzato il messaggio di errore riportato di seguito.

*Questo oggetto visivo personalizzato non è più disponibile. Per informazioni dettagliate, contattare l'amministratore.*

Tuttavia, gli oggetti visivi con segnalibro continuano a funzionare.

Dopo qualsiasi aggiornamento o modifica dell'amministratore, agli utenti di Power BI Desktop devono riavviare l'applicazione o aggiornare il browser nel servizio Power BI per vedere gli aggiornamenti.

### <a name="update-a-visual"></a>Aggiornare un oggetto visivo

Per aggiornare l'oggetto visivo dall'archivio dell'organizzazione, selezionare l'icona a forma di ingranaggio. Cercare e caricare una nuova versione dell'oggetto visivo.

Assicurarsi che l'ID dell'oggetto visivo rimanga invariato. Il nuovo file sostituisce il file precedente per tutti i report in tutta l'organizzazione. Tuttavia, se esiste la possibilità che la nuova versione dell'oggetto visivo comprometta l'utilizzo o la struttura di dati della versione precedente dell'oggetto visivo, evitare di sostituire la versione precedente. In questo caso, è invece necessario creare una nuova voce per la nuova versione dell'oggetto visivo. Ad esempio, aggiungere un nuovo numero di versione (versione x.x) al titolo del nuovo oggetto visivo presentato. In questo modo risulta chiaro che si tratta dello stesso oggetto visivo solo con un numero di versione aggiornato e che la funzionalità dei report esistenti non verrà compromessa. Assicurarsi anche in questo caso che l'ID dell'oggetto visivo rimanga invariato. Al successivo accesso al repository dell'organizzazione da Power BI Desktop, gli utenti possono importare la nuova versione e viene loro richiesto di sostituire la versione corrente disponibile nei report.

Per altre informazioni, vedere le [Domande frequenti sugli oggetti visivi personalizzati di Power BI](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#organizational-custom-visuals).

## <a name="dataflowStorage">Archiviazione del flusso di dati (anteprima)</a>

Per impostazione predefinita, i dati usati con Power BI vengono archiviati nello spazio di archiviazione interno fornito da Power BI. Con l'integrazione di flussi di dati e Azure Data Lake Storage Gen2 (ADLS Gen2), è possibile archiviare i flussi di dati nell'account di Azure Data Lake Storage Gen2 della propria organizzazione. Per altre informazioni, vedere [Integrazione di flussi di dati e Azure Data Lake (anteprima)](service-dataflows-azure-data-lake-integration.md).

## <a name="workspaces"></a>Aree di lavoro

Come amministratore, è possibile visualizzare le aree di lavoro esistenti nel tenant. È possibile ordinare e filtrare l'elenco delle aree di lavoro e visualizzare i dettagli per ognuna di esse. Le colonne della tabella corrispondono alle proprietà restituite dai [API Rest di amministrazione di Power BI](/rest/api/power-bi/admin) per aree di lavoro. Le aree di lavoro personale sono di tipo **PersonalGroup**, sono di tipo classici aree di lavoro **gruppo**, e la nuova area di lavoro esperienza le aree di lavoro sono di tipo **area di lavoro**. Per altre informazioni, vedere [creare le nuove aree di lavoro in Power BI](service-create-the-new-workspaces.md).

![Elenco delle aree di lavoro](media/service-admin-portal/workspaces-list.png)


## <a name="next-steps"></a>Passaggi successivi

[Amministrazione di Power BI nell'organizzazione](service-admin-administering-power-bi-in-your-organization.md)  
[Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md)  
[Controllo di Power BI nell'organizzazione](service-admin-auditing.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
