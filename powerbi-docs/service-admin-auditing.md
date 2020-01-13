---
title: Tenere traccia delle attività degli utenti in Power BI
description: Informazioni sulla modalità d'uso dei log attività e delle funzionalità di controllo con Power BI per monitorare ed esaminare le azioni eseguite.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 6cf298f6fd4d6d99163b2c0f5674b40cfc14bbfc
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "75657191"
---
# <a name="track-user-activities-in-power-bi"></a>Tenere traccia delle attività degli utenti in Power BI

Il fatto di sapere chi sta eseguendo un'azione su un determinato elemento del tenant di Power BI è essenziale per aiutare l'organizzazione a soddisfare i propri requisiti, ad esempio la conformità alle normative e la gestione dei record. Con Power BI sono disponibili due opzioni per tenere traccia delle attività degli utenti: Il [log attività di Power BI](#use-the-activity-log) e il [log di controllo di Office 365 unificato](#use-the-audit-log). Questi log contengono entrambi una copia completa dei [dati di controllo di Power BI](#operations-available-in-the-audit-and-activity-logs), ma esistono alcune differenze fondamentali, come riepilogato nella tabella seguente.

| **Log di controllo di Office 365 unificato** | **Log attività di Power BI** |
| --- | --- |
| Include eventi da SharePoint Online, Exchange Online, Dynamics 365 e altri servizi oltre agli eventi di controllo di Power BI. | Include solo gli eventi di controllo di Power BI. |
| Hanno accesso solo gli utenti con le autorizzazioni di sola visualizzazione per i log di controllo o per i log di controllo, come gli amministratori globali e i revisori. | Gli amministratori globali e gli amministratori del servizio Power BI hanno accesso. |
| Gli amministratori globali e i revisori possono eseguire ricerche nel log di controllo unificato usando Centro sicurezza e conformità di Office 365, il Centro sicurezza Microsoft 365 e il Centro conformità Microsoft 365. | Non esiste ancora un'interfaccia utente per la ricerca nel log attività. |
| Gli amministratori globali e i revisori possono scaricare le voci del log di controllo usando le API e i cmdlet di gestione di Office 365. | Gli amministratori globali e gli amministratori del servizio Power BI possono scaricare le voci del log attività usando un'API REST e un cmdlet di gestione di Power BI. |
| Conserva i dati di controllo per 90 giorni | Conserva i dati delle attività per 30 giorni (anteprima pubblica) |
| | |

## <a name="use-the-activity-log"></a>Usare il log attività

In qualità di amministratore del servizio Power BI, è possibile analizzare l'utilizzo di tutte le risorse di Power BI a livello di tenant usando report personalizzati basati sul log attività di Power BI. È possibile scaricare le attività usando un'API REST o un cmdlet di PowerShell. È anche possibile filtrare i dati delle attività in base a intervallo di date, utente e tipo di attività.

### <a name="activity-log-requirements"></a>Requisiti del log attività

Per accedere al log attività di Power BI, è necessario soddisfare i requisiti seguenti:

- È necessario essere un amministratore globale o un amministratore del servizio Power BI.
- Installare i [cmdlet di gestione di Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) in locale oppure usare i cmdlet di gestione di Power BI in Azure Cloud Shell.

### <a name="activityevents-rest-api"></a>API REST ActivityEvents

È possibile usare un'applicazione amministrativa basata sulle API REST di Power BI per esportare gli eventi di attività in un archivio BLOB o in un database SQL. È quindi possibile creare un report sull'utilizzo personalizzato in base ai dati esportati. Nella chiamata dell'API REST **ActivityEvents** è necessario specificare una data di inizio e una data di fine e, facoltativamente, un filtro per selezionare le attività in base al tipo di attività o all'ID utente. Poiché il log attività potrebbe contenere una grande quantità di dati, l'API **ActivityEvents** supporta attualmente solo il download fino a un giorno di dati per ogni richiesta. In altre parole, la data di inizio e la data di fine devono specificare lo stesso giorno, come nell'esempio seguente. Assicurarsi di specificare i valori DateTime nel formato UTC.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?startDateTime='2019-08-31T00:00:00'&endDateTime='2019-08-31T23:59:59'
```

Se il numero di voci è elevato, l'API **ActivityEvents** restituisce solo un numero di voci compreso all'incirca tra 5.000 e 10.000 e un token di continuazione. È quindi necessario chiamare di nuovo l'API **ActivityEvents** con il token di continuazione per ottenere il batch successivo di voci e così via fino a quando non vengono recuperate tutte le voci e non si riceve più un token di continuazione. L'esempio seguente illustra come usare il token di continuazione.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?continuationToken='%2BRID%3ARthsAIwfWGcVAAAAAAAAAA%3D%3D%23RT%3A4%23TRC%3A20%23FPC%3AARUAAAAAAAAAFwAAAAAAAAA%3D'
```

Indipendentemente dal numero di voci restituite, se i risultati includono un token di continuazione, assicurarsi di chiamare di nuovo l'API con tale token per recuperare i dati rimanenti, fino a quando non viene più restituito un token di continuazione. Può accadere che una chiamata restituisca un token di continuazione anche senza voci di evento. Nell'esempio seguente viene illustrato come eseguire il ciclo con un token di continuazione restituito nella risposta:

```
while(response.ContinuationToken != null)
{
   // Store the activity event results in a list for example
    completeListOfActivityEvents.AddRange(response.ActivityEventEntities);

    // Make another call to the API with continuation token
    response = GetPowerBIActivityEvents(response.ContinuationToken)
}
completeListOfActivityEvents.AddRange(response.ActivityEventEntities);
```

### <a name="get-powerbiactivityevent-cmdlet"></a>Cmdlet Get-PowerBIActivityEvent

È semplice scaricare gli eventi di attività usando i cmdlet di gestione Power BI per PowerShell, che includono un cmdlet **Get-PowerBIActivityEvent** che gestisce automaticamente il token di continuazione. Il cmdlet **Get-PowerBIActivityEvent** accetta un parametro StartDateTime e un parametro EndDateTime con le stesse restrizioni dell'API REST **ActivityEvents**. In altre parole, è necessario che la data di inizio e la data di fine facciano riferimento allo stesso valore di data perché è possibile recuperare i dati delle attività solo per un giorno alla volta.

Lo script seguente dimostra come scaricare tutte le attività di Power BI. Il comando converte i risultati da JSON in oggetti .NET per accedere in modo semplice alle singole proprietà delle attività.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' | ConvertFrom-Json

$activities.Count
$activities[0]

```

### <a name="filter-activity-data"></a>Filtrare i dati delle attività

È possibile filtrare gli eventi di attività in base al tipo di attività e all'ID utente. Lo script seguente dimostra come scaricare solo i dati degli eventi per l'attività **ViewDashboard**. Per altre informazioni sui parametri supportati, usare il comando `Get-Help Get-PowerBIActivityEvent`.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' -ActivityType 'ViewDashboard' | ConvertFrom-Json

$activities.Count
$activities[0]

```

## <a name="use-the-audit-log"></a>Usare il log di controllo

Se l'attività consiste nel tenere traccia delle attività degli utenti in Power BI e Office 365, è possibile usare le funzionalità di controllo nel Centro sicurezza e conformità di Office 365 o usare PowerShell. Il controllo si basa su funzionalità in Exchange Online, di cui viene eseguito automaticamente il provisioning per il supporto di Power BI.

È possibile filtrare i dati del controllo per intervallo di date, utente, dashboard, report, set di dati e tipo di attività. È anche possibile scaricare le attività in un file con estensione csv (valori delimitati da virgole) per l'analisi offline.

### <a name="audit-log-requirements"></a>Requisiti del log di controllo

Per accedere ai log di controllo, è necessario rispettare questi requisiti:

- È necessario essere un amministratore globale o avere il ruolo Audit Logs (Log di controllo) o View-Only Audit Logs (Log di controllo sola visualizzazione) in Exchange Online per accedere al log di controllo. Per impostazione predefinita questi ruoli sono assegnati ai gruppi di ruoli Gestione conformità e Gestione organizzazione nella pagina **Autorizzazioni** dell'interfaccia di amministrazione di Exchange.

    Per consentire l'accesso al log di controllo agli account senza privilegi di amministratore, è necessario aggiungere l'utente come membro di uno di questi gruppi di ruoli. In alternativa è possibile creare un gruppo di ruoli personalizzato nell'interfaccia di amministrazione di Exchange, assegnare il ruolo Audit Logs (Log di controllo) o View-Only Audit Logs (Log di controllo sola visualizzazione) a questo gruppo e quindi aggiungere l'account senza privilegi di amministratore al nuovo gruppo di ruoli. Per altre informazioni, vedere [Gestire i gruppi di ruoli in Exchange Online](/Exchange/permissions-exo/role-groups).

    Se non è possibile accedere all'interfaccia di amministrazione di Exchange dall'interfaccia di amministrazione di Microsoft 365, passare a https://outlook.office365.com/ecp ed eseguire l'accesso usando le credenziali personali.

- Se si può accedere al log di controllo ma non si è un amministratore globale o un amministratore del servizio Power BI, non sarà possibile accedere al portale di amministrazione di Power BI. In questo caso, è necessario usare un collegamento diretto al [Centro sicurezza e conformità di Office 365](https://sip.protection.office.com/#/unifiedauditlog).

### <a name="access-your-audit-logs"></a>Accedere ai log di controllo

Per poter accedere ai log abilitare la registrazione in Power BI. Per altre informazioni, vedere [Log di controllo](service-admin-portal.md#audit-logs) nella documentazione del portale di amministrazione. Tra l'abilitazione della funzione di controllo e la visualizzazione dei dati di controllo può verificarsi un ritardo massimo di 48 ore. Se i dati non vengono visualizzati immediatamente, controllare i log di controllo successivamente. Un ritardo simile può verificarsi tra l'assegnazione dell'autorizzazione per la visualizzazione dei log di controllo e l'accesso ai log.

I log di controllo di Power BI sono disponibili direttamente tramite il [Centro sicurezza e conformità di Office 365](https://sip.protection.office.com/#/unifiedauditlog). È disponibile un collegamento anche dal portale di amministrazione di Power BI:

1. In Power BI selezionare l'**icona a forma di ingranaggio** nell'angolo superiore destro e quindi selezionare **Portale di amministrazione**.

   ![Screenshot del menu a discesa dell'ingranaggio con l'opzione Portale di amministrazione evidenziata.](media/service-admin-auditing/powerbi-admin.png)

1. Selezionare **Log di controllo**.

1. Selezionare **Passa all'interfaccia di amministrazione di O365**.

   ![Screenshot del portale di amministrazione con le opzioni Log di controllo e Passa all'interfaccia di amministrazione di O365 evidenziate.](media/service-admin-auditing/audit-log-o365-admin-center.png)

### <a name="search-only-power-bi-activities"></a>Eseguire solo la ricerca delle attività di Power BI

Limitare i risultati alle sole attività di Power BI seguendo questa procedura. Per un elenco delle attività, vedere l'elenco delle [attività controllate da Power BI](#operations-available-in-the-audit-and-activity-logs) più avanti in questo articolo.

1. Nella pagina **Ricerca log di controllo** selezionare l'elenco a discesa **Attività** in **Cerca**.

2. Selezionare **Attività di Power BI**.

   ![Screenshot della pagina Ricerca log di controllo con le attività di Power BI evidenziate.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selezionare un punto qualsiasi all'esterno della casella di selezione per chiuderla.

Le ricerche restituiranno solo le attività di Power BI.

### <a name="search-the-audit-logs-by-date"></a>Eseguire la ricerca dei log di controllo per data

È possibile cercare i log in base all'intervallo di date usando i campi **Data di inizio** e **Data di fine**. La selezione predefinita corrisponde agli ultimi sette giorni. La data e l'ora vengono visualizzate in formato UTC (Coordinated Universal Time). L'intervallo massimo che è possibile specificare è 90 giorni. 

Se l'intervallo di date selezionato è maggiore di 90 giorni viene visualizzato un errore. Se si usa l'intervallo massimo di 90 giorni, selezionare l'ora corrente per **Data di inizio**. In caso contrario, un errore informerà che la data di inizio è precedente alla data di fine. Se il controllo è stato attivato negli ultimi 90 giorni, l'intervallo di date non può cominciare prima della data di attivazione del controllo.

![Screenshot della ricerca dei log di controllo con le opzioni Data di inizio e Data di fine evidenziate.](media/service-admin-auditing/search-audit-log-by-date.png)

### <a name="search-the-audit-logs-by-users"></a>Eseguire la ricerca dei log di controllo per utente

È possibile cercare le voci del log di controllo in base alle attività eseguite da utenti specifici. Immettere uno o più nomi utente nel campo **Utenti**. Il nome utente somiglia a un indirizzo di posta elettronica. Si tratta dell'account con il quale gli utenti accedono a Power BI. Lasciare questa casella vuota per visualizzare le voci di tutti gli utenti (e account del servizio) dell'organizzazione.

![Ricerca in base agli utenti](media/service-admin-auditing/search-audit-log-by-user.png)

### <a name="view-search-results"></a>Visualizzare i risultati della ricerca

Dopo aver selezionato **Cerca** vengono caricati i risultati della ricerca. Dopo alcuni istanti i risultati vengono visualizzati in **Risultati**. Al termine della ricerca viene visualizzato il numero di risultati trovati. In **Ricerca log di controllo** vengono visualizzati fino a 1000 eventi. Se gli eventi che soddisfano i criteri di ricerca sono più di 1000, l'app visualizza i 1000 eventi più recenti.

#### <a name="view-the-main-results"></a>Visualizzare i risultati principali

L'area **Risultati** contiene le informazioni seguenti per ogni evento restituito dalla ricerca. Per ordinare i risultati, selezionare un'intestazione di colonna in **Risultati**.

| **Colonna** | **Definizione** |
| --- | --- |
| Data |La data e l'ora (in formato UTC) in cui si è verificato l'evento. |
| Indirizzo IP |Indirizzo IP del dispositivo usato per l'attività registrata. L'app visualizza l'indirizzo IP in formato IPv4 o IPv6. |
| Utente |L'utente (o l'account del servizio) che ha eseguito l'azione che ha generato l'evento. |
| Attività |L'attività eseguita dall'utente. Questo valore corrisponde alle attività selezionate nell'elenco a discesa **Attività**. Per un evento proveniente dal registro di controllo dell'amministrazione di Exchange, il valore di questa colonna è un cmdlet di Exchange. |
| Item |Oggetto creato o modificato in seguito all'attività corrispondente. Ad esempio il file visualizzato o modificato o l'account utente aggiornato. Non tutte le attività presentano un valore in questa colonna. |
| Dettagli |Dettagli aggiuntivi su un'attività. Ancora una volta, non tutte le attività presentano un valore corrispondente. |

#### <a name="view-the-details-for-an-event"></a>Visualizzare i dettagli di un evento

Per visualizzare altri dettagli su un evento selezionare il record dell'evento nell'elenco dei risultati della ricerca. Viene visualizzata una pagina **Dettagli** che contiene le proprietà dettagliate del record dell'evento. Le proprietà visualizzate nella pagina **Dettagli** dipendono dal servizio Office 365 in cui si verifica l'evento.

Per visualizzare questi dettagli, selezionare **Altre informazioni**. Tutte le voci di Power BI hanno un valore pari a 20 per la proprietà RecordType. Per informazioni su altre proprietà, vedere [Proprietà dettagliate nel log di controllo](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Screenshot della finestra di dialogo Dettagli del controllo con l'opzione Altre informazioni evidenziata.](media/service-admin-auditing/audit-details.png)

### <a name="export-search-results"></a>Esportare i risultati della ricerca

Per esportare il log di controllo di Power BI in un file con estensione csv seguire questa procedura.

1. Selezionare **Esporta risultati**.

1. Selezionare **Salva risultati caricati** o **Scarica tutti i risultati**.

    ![Screenshot dell'opzione Esporta risultati.](media/service-admin-auditing/export-auditing-results.png)

### <a name="use-powershell-to-search-audit-logs"></a>Usare PowerShell per eseguire ricerche nei log di controllo

È anche possibile usare PowerShell per accedere ai log di controllo in base all'account di accesso. L'esempio seguente mostra come connettersi a Exchange Online PowerShell e quindi usare il comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) per il pull delle voci del log di controllo di Power BI. Per eseguire lo script, un amministratore deve disporre delle autorizzazioni appropriate, come descritto nella sezione [Requisiti del log di controllo](#audit-log-requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

### <a name="use-powershell-to-export-audit-logs"></a>Usare PowerShell per esportare i log di controllo

È anche possibile usare PowerShell per esportare i risultati della ricerca nei log di controllo. Nell'esempio seguente viene illustrato come inviare il comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) ed esportare i risultati usando il cmdlet [Export-CSV](/powershell/module/microsoft.powershell.utility/export-csv). Per eseguire lo script, un amministratore deve disporre delle autorizzazioni appropriate, come descritto nella sezione [Requisiti del log di controllo](#audit-log-requirements).

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

Per altre informazioni sulla connessione a Exchange Online, vedere [Connessione a Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Per un altro esempio di uso di PowerShell con i log di controllo, vedere [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Uso del log di controlli di Power BI e di PoweShell per assegnare licenze di Power BI Pro).

## <a name="operations-available-in-the-audit-and-activity-logs"></a>Operazioni disponibili nei log di controllo e attività

Le operazioni seguenti sono disponibili sia nel log di controllo che nei log attività.

| Nome descrittivo                                     | Nome operazione                              | Note                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Aggiunta origine dati a Power BI Gateway             | AddDatasourceToGateway                      |                                          |
| Accesso alla cartella di Power BI aggiunto                      | AddFolderAccess                             | Attualmente non in uso                       |
| Membri del gruppo di Power BI aggiunti                      | AddGroupMembers                             |                                          |
| Account di archiviazione del flusso di dati collegato al tenant dall'amministratore | AdminAttachedDataflowStorageAccountToTenant | Attualmente non in uso                       |
| Analizzato un set di dati di Power BI                         | AnalyzedByExternalApplication               |                                          |
| Report di Power BI analizzato                          | AnalyzeInExcel                              |                                          |
| Account di archiviazione del flusso di dati collegato                 | AttachedDataflowStorageAccount              |                                          |
| Set di dati di Power BI associato al gateway                | BindToGateway                               |                                          |
| Aggiornamento del flusso di dati annullato                        | CancelDataflowRefresh                       |                                          |
| Stato capacità modificato                            | ChangeCapacityState                         |                                          |
| Assegnazione utente capacità modificata                  | UpdateCapacityUsersAssignment               |                                          |
| Connessioni del set di dati di Power BI modificate              | SetAllConnections                           |                                          |
| Modificati gli amministratori del gateway di Power BI                   | ChangeGatewayAdministrators                 |                                          |
| Modificati gli utenti dell'origine dati del gateway di Power BI        | ChangeGatewayDatasourceUsers                |                                          |
| Pacchetto di contenuto di Power BI per l'organizzazione creato      | CreateOrgApp                                |                                          |
| App Power BI creata                              | CreateApp                                   |                                          |
| Dashboard di Power BI creato                        | CreateDashboard                             |                                          |
| Flusso di dati di Power BI creato                         | CreateDataflow                              |                                          |
| Set di dati di Power BI creato                          | CreateDataset                               |                                          |
| Sottoscrizione ai messaggi di posta elettronica di Power BI creata               | CreateEmailSubscription                     |                                          |
| Cartella di Power BI creata                           | CreateFolder                                |                                          |
| Creato gateway di Power BI                          | CreateGateway                               |                                          |
| Gruppo di Power BI creato                            | CreateGroup                                 |                                          |
| Report di Power BI creato                           | CreateReport                                |                                          |
| Migrazione del flusso di dati all'account di archiviazione esterno eseguita     | DataflowMigratedToExternalStorageAccount    | Attualmente non in uso                       |
| Autorizzazioni del flusso di dati aggiunte                        | DataflowPermissionsAdded                    | Attualmente non in uso                       |
| Autorizzazioni del flusso di dati rimosse                      | DataflowPermissionsRemoved                  | Attualmente non in uso                       |
| Pacchetto di contenuto di Power BI per l'organizzazione eliminato      | DeleteOrgApp                                |                                          |
| Commento di Power BI eliminato                          | DeleteComment                               |                                          |
| Dashboard di Power BI eliminato                        | DeleteDashboard                             | Attualmente non in uso                       |
| Flusso di dati di Power BI eliminato                         | DeleteDataflow                              | Attualmente non in uso                       |
| Set di dati di Power BI eliminato                          | DeleteDataset                               |                                          |
| Sottoscrizione ai messaggi di posta elettronica di Power BI eliminata               | DeleteEmailSubscription                     |                                          |
| Cartella di Power BI eliminata                           | DeleteFolder                                |                                          |
| Accesso alla cartella di Power BI eliminato                    | DeleteFolderAccess                          | Attualmente non in uso                       |
| Eliminato gateway di Power BI                          | DeleteGateway                               |                                          |
| Gruppo di Power BI eliminato                            | DeleteGroup                                 |                                          |
| Report di Power BI eliminato                           | DeleteReport                                |                                          |
| Origini dati del set di dati di Power BI individuate          | GetDatasources                              |                                          |
| Report di Power BI scaricato                        | DownloadReport                              |                                          |
| Proprietà del flusso di dati modificate                        | EditDataflowProperties                      |                                          |
| Autorizzazione di certificazione di Power BI modificata          | EditCertificationPermission                 | Attualmente non in uso                       |
| Dashboard di Power BI modificato                         | EditDashboard                               | Attualmente non in uso                       |
| Set di dati di Power BI modificato                           | EditDataset                                 |                                          |
| Proprietà del set di dati di Power BI modificate                | EditDatasetProperties                       | Attualmente non in uso                       |
| Report di Power BI modificato                            | EditReport                                  |                                          |
| Flusso di dati di Power BI esportato                        | ExportDataflow                              |                                          |
| Dati degli oggetti visivi dei report di Power BI esportati              | ExportReport                                |                                          |
| Dati del riquadro di Power BI esportati                       | ExportTile                                  |                                          |
| Non è stato possibile aggiungere le autorizzazioni del flusso di dati                | FailedToAddDataflowPermissions              | Attualmente non in uso                       |
| Non è stato possibile rimuovere le autorizzazioni del flusso di dati             | FailedToRemoveDataflowPermissions           | Attualmente non in uso                       |
| Token di firma di accesso condiviso del flusso di dati di Power BI generato             | GenerateDataflowSasToken                    |                                          |
| Token di incorporamento di Power BI generato                    | GenerateEmbedToken                          |                                          |
| File importato in Power BI                         | Importa                                      |                                          |
| App Power BI installata                            | InstallApp                                  |                                          |
| Migrazione dell'area di lavoro a una capacità eseguita                  | MigrateWorkspaceIntoCapacity                |                                          |
| Commento di Power BI pubblicato                           | PostComment                                 |                                          |
| Dashboard di Power BI stampato                        | PrintDashboard                              |                                          |
| Pagina di report di Power BI stampata                      | PrintReport                                 |                                          |
| Report di Power BI pubblicato sul Web                  | PublishToWebReport                          |                                          |
| Segreto del flusso di dati di Power BI ricevuto da Key Vault  | ReceiveDataflowSecretFromKeyVault           |                                          |
| Rimossa origine dati dal gateway di Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membri del gruppo di Power BI rimossi                    | DeleteGroupMembers                          |                                          |
| Area di lavoro rimossa da una capacità                 | RemoveWorkspacesFromCapacity                |                                          |
| Dashboard di Power BI rinominato                        | RenameDashboard                             |                                          |
| Aggiornamento del flusso di dati Power BI richiesto               | RequestDataflowRefresh                      | Attualmente non in uso                       |
| Aggiornamento del set di dati di Power BI richiesto                | RefreshDataset                              |                                          |
| Aree di lavoro di Power BI recuperate                     | GetWorkspaces                               |                                          |
| Impostazione del percorso di archiviazione del flusso di dati per un'area di lavoro     | SetDataflowStorageLocationForWorkspace      |                                          |
| Aggiornamento pianificato impostato sul flusso di dati di Power BI        | SetScheduledRefreshOnDataflow               |                                          |
| Aggiornamento pianificato impostato sul set di dati di Power BI         | SetScheduledRefresh                         |                                          |
| Dashboard di Power BI condiviso                         | ShareDashboard                              |                                          |
| Report di Power BI condiviso                            | ShareReport                                 |                                          |
| Avviata una versione di valutazione estesa di Power BI                   | OptInForExtendedProTrial                    | Attualmente non in uso                       |
| Versione di valutazione di Power BI avviata                            | OptInForProTrial                            |                                          |
| Origine dati di Power BI acquisita                   | TakeOverDatasource                          |                                          |
| Set di dati di Power BI acquisito                        | TakeOverDataset                             |                                          |
| Flusso di dati di Power BI acquisito                     | TookOverDataflow                             |                                          |
| Pubblicazione dell'app Power BI annullata                          | UnpublishApp                                |                                          |
| Aggiorna impostazioni di governance delle risorse di capacità      | UpdateCapacityResourceGovernanceSettings    | Attualmente non presente nell'interfaccia di amministrazione di Microsoft 365 |
| Amministratore della capacità aggiornato                            | UpdateCapacityAdmins                        |                                          |
| Nome visualizzato della capacità aggiornato                     | UpdateCapacityDisplayName                   |                                          |
| Autorizzazioni di assegnazione dell'archiviazione del flusso di dati aggiornate   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| Impostazioni Power BI dell'organizzazione aggiornate          | UpdatedAdminFeatureSwitch                   |                                          |
| App Power BI aggiornata                              | UpdateApp                                   |                                          |
| Flusso di dati di Power BI aggiornato                         | UpdateDataflow                              |                                          |
| Origini dati del set di dati di Power BI aggiornate             | UpdateDatasources                           |                                          |
| Parametri del set di dati di Power BI aggiornati               | UpdateDatasetParameters                     |                                          |
| Sottoscrizione ai messaggi di posta elettronica di Power BI aggiornata               | UpdateEmailSubscription                     |                                          |
| Cartella di Power BI aggiornata                           | UpdateFolder                                |                                          |
| Accesso alla cartella di Power BI aggiornato                    | UpdateFolderAccess                          |                                          |
| Credenziali dell'origine dati di Power BI Gateway aggiornate  | UpdateDatasourceCredentials                 |                                          |
| Dashboard di Power BI visualizzato                         | ViewDashboard                               |                                          |
| Flusso di dati di Power BI visualizzato                          | ViewDataflow                                |                                          |
| Report di Power BI visualizzato                            | ViewReport                                  |                                          |
| Riquadro di Power BI visualizzato                              | ViewTile                                    |                                          |
| Metriche di utilizzo di Power BI visualizzate                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Passaggi successivi

[Che cos'è l'amministrazione di Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portale di amministrazione di Power BI](service-admin-portal.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
