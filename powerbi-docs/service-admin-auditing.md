---
title: Uso del controllo nell'organizzazione
description: Informazioni sulla modalità d'uso della funzionalità di controllo con Power BI per monitorare ed esaminare le azioni eseguite. È possibile usare il Centro sicurezza e conformità o PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: bcf012d94dedfd912479c3e51e0de388b177c294
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34755025"
---
# <a name="using-auditing-within-your-organization"></a>Uso del controllo nell'organizzazione

Informazioni sulla modalità d'uso della funzionalità di controllo con Power BI per monitorare ed esaminare le azioni eseguite. È possibile usare il Centro sicurezza e conformità o PowerShell.

Essere a conoscenza di chi sta eseguendo un'azione su un determinato elemento del tenant di Power BI è di fondamentale importanza per aiutare l'organizzazione a soddisfare i suoi requisiti, come ad esempio la conformità alle normative e la gestione dei record. È possibile usare la funzione di controllo di Power BI per controllare le azioni eseguite dagli utenti, ad esempio "Visualizza report" e "Visualizza dashboard". Non è possibile usare la funzione di controllo per controllare le autorizzazioni. 

È possibile filtrare i dati del controllo per intervallo di date, utente, dashboard, report, set di dati e tipo di attività. È inoltre possibile scaricare le attività in un file csv (valori delimitati da virgola) per l'analisi offline.

## <a name="requirements"></a>Requisiti
Per accedere ai log di controllo, è necessario rispettare questi requisiti:

- Per accedere alla sezione di controllo del Centro sicurezza e conformità di Office 365, è necessario avere una licenza di Exchange Online, inclusa con sottoscrizioni di Office 365 Enterprise E3 ed E5.

- È necessario essere un amministratore globale o avere il ruolo di amministratore di Exchange che fornisce l'accesso al log di controllo. I ruoli di amministratore di Exchange vengono controllati tramite l'interfaccia di amministrazione di Exchange. Per altre informazioni, vedere [Permissions in Exchange Online](https://technet.microsoft.com/library/jj200692(v=exchg.150).aspx) (Autorizzazioni in Exchange Online).

- Se si può accedere al log di controllo ma non si è un amministratore globale o un amministratore del servizio Power BI, non sarà possibile accedere al portale di amministrazione di Power BI. In questo caso, è necessario ottenere un collegamento diretto al Centro sicurezza e conformità di Office 365.

- Per visualizzare i log di controllo per Power BI nel tenant, è necessario che nel tenant stesso sia disponibile almeno una licenza per cassette postali di Exchange.

## <a name="accessing-your-audit-logs"></a>Accesso ai log di controllo

Per controllare i log di Power BI, visitare il Centro di sicurezza e conformità di Office 365.

È possibile che tra l'abilitazione della funzione di controllo e la visualizzazione dei dati di controllo si verifichi un ritardo di un massimo di 48 ore. Se i dati non vengono visualizzati immediatamente, controllare i log di controllo successivamente. Un ritardo simile può verificarsi tra l'assegnazione dell'autorizzazione per la visualizzazione dei log di controllo e l'accesso ai log.

1. Selezionare **l'icona dell'ingranaggio** in alto a destra.

2. Selezionare **Portale di amministrazione**.
   
   ![](media/service-admin-auditing/powerbi-admin.png)

3. Selezionare **Log di controllo**.
 
4. Selezionare **Passa all'interfaccia di amministrazione di O365**.
   
   ![](media/service-admin-auditing/audit-log-o365-admin-center.png)

In alternativa, è possibile accedere tramite [Office 365 | Sicurezza e conformità](https://protection.office.com/#/unifiedauditlog).

Per fornire l'accesso al log di controllo agli account non amministratore, è necessario assegnare le autorizzazioni nell'interfaccia di amministrazione di Exchange Online. Ad esempio, è possibile assegnare un utente a un gruppo di ruoli esistente, ad esempio Gestione organizzazione, oppure crearne uno nuovo con il ruolo Log di controllo. Per altre informazioni, vedere [Permissions in Exchange Online](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx) (Autorizzazioni in Exchange Online).

## <a name="search-only-power-bi-activities"></a>Eseguire solo la ricerca delle attività di Power BI

È possibile limitare i risultati alle sole attività di Power BI eseguendo le operazioni seguenti.

1. Nella pagina **Ricerca dei registri di controllo** selezionare l'elenco a discesa delle **Attività** in **Cerca**.

2. Selezionare **Attività di PowerBI**.
   
   ![](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selezionare un punto qualsiasi all'esterno della casella di selezione per chiuderla.

Le ricerche verranno filtrate alle sole attività di Power BI.

## <a name="search-the-audit-logs-by-date"></a>Eseguire la ricerca dei log di controllo per data

È possibile cercare i log in base all'intervallo di date usando i campi "Data di inizio" e "Data di fine". Gli ultimi sette giorni sono selezionati per impostazione predefinita. La data e l'ora vengono visualizzate nel formato Coordinated Universal Time (UTC). L'intervallo massimo che è possibile specificare è 90 giorni. Se l'intervallo di date selezionato è maggiore a 90 giorni, viene visualizzato un errore.

> [!NOTE]
> Se si usa l'intervallo massimo di 90 giorni, selezionare l'ora corrente per la data di inizio. In caso contrario, un errore informerà che la data di inizio è precedente alla data di fine. Se il controllo è stato attivato negli ultimi 90 giorni, l'intervallo massimo non può cominciare prima della data in cui il controllo è stato attivato.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Eseguire la ricerca dei log di controllo per utente

È possibile cercare le voci del log di controllo in base alle attività eseguite dagli utenti specifici. A tale scopo, immettere uno o più nomi utente nel campo "Utenti".  Il risultato sarà il nome con cui gli utenti eseguono l'accesso a Power BI. Assomiglia a un indirizzo di posta elettronica.
Lasciare questa casella vuota per visualizzare le voci di tutti gli utenti (e account del servizio) dell'organizzazione.

![](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="viewing-search-results"></a>Visualizzazione dei risultati della ricerca

Dopo aver fatto clic sul pulsante di ricerca, i risultati della ricerca vengono caricati e visualizzati in Risultati nel giro di pochi secondi. Al termine della ricerca, viene visualizzato il numero di risultati trovati. 

> [!NOTE]
> Verrà visualizzato un massimo di 1000 eventi. Se più di 1000 eventi soddisfano i criteri di ricerca, verranno visualizzati i 1000 eventi più recenti.

I risultati contengono le informazioni seguenti per ogni evento restituito dalla ricerca.

| **Colonna** | **Definizione** |
| --- | --- |
| Data |La data e l'ora (in formato UTC) in cui si è verificato l'evento. |
| Indirizzo IP |L'indirizzo IP del dispositivo usato durante la registrazione dell'attività. L'indirizzo IP viene visualizzato in formato IPv4 o IPv6. |
| Utente |L'utente (o l'account del servizio) che ha eseguito l'azione che ha generato l'evento. |
| Attività |L'attività eseguita dall'utente. Questo valore corrisponde alle attività selezionate nell'elenco a discesa Attività. Per un evento proveniente dal registro di controllo dell'amministrazione di Exchange, il valore di questa colonna è un cmdlet di Exchange. |
| Elemento |L'oggetto creato o modificato in seguito all'attività corrispondente. Ad esempio, il file che è stato di visualizzato o modificato, oppure l'account utente che è stato aggiornato. Non tutte le attività presentano un valore in questa colonna. |
| Dettagli |Dettagli aggiuntivi su un'attività. Ancora una volta, non tutte le attività presentano un valore corrispondente. |

> [!NOTE]
> Per ordinare i risultati, selezionare un'intestazione di colonna in Risultati. È possibile ordinare i risultati dalla A alla Z o dalla Z alla A. Fare clic sull'intestazione Data per ordinare i risultati dal meno recente al più recente o viceversa.

## <a name="view-the-details-for-an-event"></a>Visualizzare i dettagli di un evento

È possibile visualizzare ulteriori dettagli su un evento selezionando il record dell'evento nell'elenco dei risultati della ricerca. Viene visualizzata una pagina che contiene le proprietà del record dell'evento. Le proprietà visualizzate dipendono dal servizio Office 365 in cui si verifica l'evento. Per visualizzare ulteriori dettagli, selezionare **Altre informazioni**.

La tabella seguente fornisce informazioni dettagliate su ciò che è possibile visualizzare.

| **Parametro o evento** | **Descrizione** | **Dettagli aggiuntivi** |
| --- | --- | --- |
| Report di Power BI scaricato |Questa attività viene registrata ogni volta che un report viene scaricato |Nome del report, Nome del set di dati |
| Creare report |Questa attività viene registrata ogni volta che viene creato un nuovo report. |Nome del report, Nome del set di dati |
| Modifica report |Questa attività viene registrata ogni volta che un report viene modificato. |Nome del report, Nome del set di dati |
| Creare set di dati |Questa attività viene registrata ogni volta che viene creato un set di dati. |Nome del set di dati, DataConnectivityMode |
| Eliminare set di dati |Questa attività viene registrata ogni volta che viene eliminato un set di dati. |Nome del set di dati, DataConnectivityMode |
| Creare un'app di Power BI |Questa attività viene registrata ogni volta che viene creata un'app di Power BI |Nome dell'app, Autorizzazioni, Nome dell'area di lavoro |
| Installare un'app di Power BI |Questa attività viene registrata ogni volta che viene installata un'app di Power BI |Nome dell'app |
| Aggiornare l'app di Power BI |Questa attività viene registrata ogni volta che viene aggiornata un'app di Power BI |Nome dell'app, Autorizzazioni, Nome dell'area di lavoro |
| Avviata una versione di valutazione estesa di Power BI |Questa attività viene registrata ogni volta che un utente accetta la versione di valutazione pro estesa che viene eseguita fino al 31 maggio 2018 | |
| Analizzato un set di dati di Power BI |Questa attività viene registrata ogni volta che un set di dati di Power BI viene analizzato in Excel. | |
| Creato gateway di Power BI |Questa attività viene registrata ogni volta che viene creato un nuovo gateway. |Nome del gateway, Tipo di gateway |
| Eliminato gateway di Power BI |Questa attività viene registrata ogni volta che viene eliminato un gateway. |Nome del gateway, Tipo di gateway |
| Aggiunta origine dati al gateway di Power BI |Questa attività viene registrata ogni volta che un'origine dati viene aggiunta al gateway |Nome del gateway, Tipo di gateway, Nome origine dati, Tipo origine dati |
| Rimossa origine dati dal gateway di Power BI |Questa attività viene registrata ogni volta che un'origine dati viene rimossa da un gateway |Nome del gateway, Tipo di gateway, Nome origine dati, Tipo origine dati |
| Modificati gli amministratori del gateway di Power BI |Questa attività viene registrata ogni volta che vengono modificati gli amministratori di un gateway (aggiunti/rimossi) |Nome del gateway, Utenti aggiunti, Utenti rimossi |
| Modificati gli utenti dell'origine dati del gateway di Power BI |Questa attività viene registrata ogni volta che vengono modificati gli utenti di un gateway (aggiunti/rimossi) |Nome del gateway, Utenti aggiunti, Utenti rimossi |
| SetScheduledRefresh |Questa attività viene registrata ogni volta che viene pianificato un nuovo aggiornamento per un set di dati |Nome del set di dati, Frequenza di aggiornamento (in minuti) |

## <a name="using-powershell-to-search"></a>Uso di PowerShell per la ricerca

È possibile usare PowerShell per accedere ai log di controllo in base all'account di accesso. Per eseguire questa operazione, accedere a Exchange Online. Ecco un esempio di comando per effettuare il pull delle voci di log di controllo di Power BI.

> [!NOTE]
> Per usare il comando New-PSSession, all'account deve essere assegnata una licenza di Exchange Online ed è necessario l'accesso al Registro di controllo per il tenant.

```
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2016 -EndDate 9/15/2016 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Per altre informazioni sulla connessione a Exchange Online, vedere [Connect to Exchange Online PowerShell](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx) (Connettersi a Exchange Online tramite PowerShell).

Per altre informazioni sui parametri e sull'utilizzo del comando Search-UnifiedAuditLog, vedere [Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx).

Per un esempio di uso di PowerShell per eseguire la ricerca nel Registro di controllo e quindi assegnare le licenze Power BI Pro basate sulle voci, vedere [Uso del Registro di controllo di Power BI e PowerShell per assegnare le licenze di Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="export-the-power-bi-audit-log"></a>Esportare il registro di controllo di Power BI

È possibile esportare il registro di controllo di Power BI in un file csv.

1. Selezionare **Esporta risultati**.

2. Selezionare **Salva risultati caricati** o **Scarica tutti i risultati**.
   
   ![](media/service-admin-auditing/export-auditing-results.png)

## <a name="record-and-user-types"></a>Tipi di record e di utenti

I dettagli delle voci di log di controllo includeranno un parametro RecordType e un parametro UserType. Tutte le voci di Power BI avranno un parametro RecordType con valore 20.

Per un elenco completo, vedere [Proprietà dettagliate nel log di controllo di Office 365](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="list-of-activities-audited-by-power-bi"></a>Elenco delle attività controllate da Power BI

| Attività | Descrizione | Dettagli aggiuntivi |
| --- | --- | --- |
| CreateDashboard |Questa attività viene registrata ogni volta che viene creato un nuovo dashboard. |- Nome del dashboard. |
| EditDashboard |Questa attività viene registrata ogni volta che un dashboard viene rinominato. |- Nome del dashboard. |
| DeleteDashboard |Questa attività viene registrata ogni volta che un dashboard viene eliminato. |- Nome del dashboard. |
| PrintDashboard |Questo evento viene registrato ogni volta che un dashboard viene stampato. |- Nome del dashboard.<br/>- Nome del set di dati. |
| ShareDashboard |Questa attività viene registrata ogni volta che un dashboard viene condiviso. |- Nome del dashboard.<br/>- Destinatario di posta elettronica.<br/>- Nome del set di dati.<br>- Autorizzazioni di ricondivisione. |
| ViewDashboard |Questa attività viene registrata ogni volta che un dashboard viene visualizzato. |- Nome del dashboard. |
| ExportTile |Questo evento viene registrato ogni volta che i dati vengono esportati da un riquadro del dashboard. |- Nome del riquadro.<br/>- Nome del set di dati. |
| DeleteReport |Questa attività viene registrata ogni volta che un report viene eliminato. |- Nome del report. |
| ExportReport |Questo evento viene registrato ogni volta che i dati vengono esportati da un riquadro del report. |- Nome del report.<br/>- Nome del set di dati. |
| PrintReport |Questo evento viene registrato ogni volta che un report viene stampato. |- Nome del report.<br/>- Nome del set di dati. |
| PublishToWebReport |Questo evento viene registrato ogni volta che un report viene pubblicato sul Web. |- Nome del report.<br/>- Nome del set di dati. |
| ViewReport |Questa attività viene registrata ogni volta che un report viene visualizzato. |- Nome del report. |
| ExploreDataset |Questo evento viene registrato ogni volta che si esplora un set di dati selezionandolo. |- Nome del set di dati. |
| DeleteDataset |Questo evento viene registrato ogni volta che un set di dati viene eliminato. |- Nome del set di dati. |
| CreateOrgApp |Questa attività viene registrata ogni volta che viene creato un pacchetto di contenuto aziendale. |Nome del pacchetto di contenuto - aziendale.<br/>- Nomi dei dashboard.<br/>- Nomi dei report.<br/>- Nomi dei set di dati. |
| CreateGroup |Questa attività viene generata ogni volta che viene creato un gruppo. |- Nome del gruppo. |
| AddGroupMembers |Questa attività viene registrata ogni volta che viene aggiunto un membro a un'area di lavoro di gruppo di Power BI. |- Nome del gruppo.<br/>- Indirizzi di posta elettronica. |
| UpdatedAdminFeatureSwitch |Questo evento viene registrato ogni volta che viene modificata un'opzione della funzionalità di amministrazione. |- Nome dell'opzione.<br/>- Nuovo stato dell'opzione. |
| OptInForProTrial |Questo evento viene registrato quando un utente sceglie di provare Power BI Pro all'interno del servizio. |- indirizzo di posta elettronica |

## <a name="next-steps"></a>Passaggi successivi

[Portale di amministrazione di Power BI](service-admin-portal.md)  
[Power BI Premium: di cosa si tratta?](service-premium.md)  
[Acquisto di Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Permissions in Exchange Online (Autorizzazioni in Exchange Online)](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx)  
[Connect to Exchange Online PowerShell (Connettersi a Exchange Online tramite PowerShell)](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx)  
[Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx)  
[Proprietà dettagliate nel log di controllo di Office 365](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
