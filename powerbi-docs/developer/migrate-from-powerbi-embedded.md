---
title: Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI Embedded in Power BI
description: Informazioni su come eseguire la migrazione da Power BI Embedded al servizio Power BI e sfruttare i miglioramenti per l'incorporamento nelle app.
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
ms.date: 08/24/2018
ms.author: maghan
ms.openlocfilehash: 59d395d11839903108f811ff4a6022ea04cadc8f
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="how-to-migrate-power-bi-embedded-workspace-collection-content-to-power-bi"></a>Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI Embedded in Power BI
Informazioni su come eseguire la migrazione da Power BI Embedded al servizio Power BI e sfruttare i miglioramenti per l'incorporamento nelle app.

Microsoft ha recentemente [annunciato Power BI Premium](https://powerbi.microsoft.com/blog/microsoft-accelerates-modern-bi-adoption-with-power-bi-premium/), un nuovo modello di gestione delle licenze basato sulla capacità che aumenta la flessibilità di accesso, condivisione e distribuzione del contenuto per gli utenti. L'offerta aggiunge anche ulteriore scalabilità e rendimento al servizio Power BI.

Con l'introduzione di Power BI Premium, Power BI Embedded e il servizio Power BI convergono per migliorare la modalità di incorporamento del contenuto di Power BI nelle app. Questo significa che si avrà una sola superficie dell'API, un set coerente di funzionalità e l'accesso alle ultime funzionalità di Power BI, ad esempio dashboard, gateway e aree di lavoro per le app, quando si incorpora il contenuto. In futuro sarà possibile iniziare con Power BI Desktop e passare alla distribuzione con Power BI Premium, che sarà disponibile a livello generale alla fine del secondo trimestre del 2017.

Il corrente servizio Power BI Embedded continuerà a essere disponibile per un periodo di tempo limitato in seguito alla disponibilità generale dell'offerta cumulativa: i clienti che hanno sottoscritto un contratto Enterprise Agreement avranno accesso fino alla scadenza dei contratti esistenti; i clienti che hanno acquistato Power BI Embedded attraverso canali diretti o CSP potranno accedere per un anno a partire dalla disponibilità generale di Power BI Premium.  Questo articolo contiene alcune informazioni per la migrazione dal servizio di Azure al servizio Power BI e su quali modifiche aspettarsi nell'applicazione.

> [!IMPORTANT]
> Mentre la migrazione richiederà una dipendenza nel servizio Power BI, non esiste una dipendenza in Power BI per gli utenti dell'applicazione quando si usa un **token di incorporamento**. Gli utenti non dovranno eseguire l'iscrizione a Power BI per visualizzare il contenuto incorporato nell'applicazione. È possibile usare questo approccio di incorporamento per gli utenti esterni a Power BI del servizio.
> 
> 

![](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

## <a name="prepare-for-the-migration"></a>Preparare la migrazione
Per prepararsi alla migrazione dal servizio Power BI Embedded di Azure al servizio Power BI occorre eseguire alcune operazioni. È necessario un tenant disponibile, oltre a un utente che abbia una licenza di Power BI Pro.

1. Accertarsi di avere accesso a un tenant di Azure Active Directory (Azure AD).
   
    È necessario determinare l'impostazione del tenant da usare.
   
   * Usare il tenant di Power BI aziendale esistente?
   * Usare un tenant diverso per l'applicazione?
   * Usare un tenant diverso per ogni cliente?
     
     Se si decide di creare un nuovo tenant per l'applicazione o di crearne uno per ogni cliente, vedere [Creare un tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md) o [Come ottenere un tenant di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant).
2. Creare un utente all'interno di questo nuovo tenant che verrà usato come account "master" dell'applicazione. È necessario che l'account in questione si iscriva a Power BI e che gli sia stata assegnata una licenza di Power BI Pro.

## <a name="accounts-within-azure-ad"></a>Account in Azure AD
I seguenti account dovranno esistere all'interno del tenant.

> [!NOTE]
> Le licenze di Power BI Pro sono necessarie per usare le aree di lavoro per le app.
> 
> 

1. Un utente amministratore tenant.
   
    È consigliabile che l'utente sia un membro di tutte le aree di lavoro per le app create allo scopo dell'incorporamento.
2. Account per gli analisti che creeranno il contenuto.
   
    Questi utenti devono essere assegnati alle aree di lavoro per le app in base alle esigenze.
3. Un account utente *master* dell'applicazione o un account di servizio.
   
    Il back-end delle applicazioni memorizza le credenziali per l'account e le userà per acquisire un token di Azure AD da usare con le API REST di Power BI. Questo account verrà usato per generare il token di incorporamento per l'applicazione. Questo account deve anche essere un amministratore delle aree di lavoro per le app create per l'incorporamento.
   
   > [!NOTE]
   > Si tratta solo di un normale account utente nell'organizzazione che verrà usato a scopo di incorporamento.
   > 
   > 

## <a name="app-registration-and-permissions"></a>Registrazione e autorizzazioni dell'app
È necessario registrare un'applicazione in Azure AD e concedere alcune autorizzazioni.

### <a name="register-an-application"></a>Registrare un'applicazione
Sarà necessario registrare l'applicazione in Azure AD per effettuare chiamate all'API REST. Questa procedura include il passaggio al portale di Azure per l'applicazione di configurazione aggiuntiva, oltre alla pagina di registrazione dell'app Power BI. Per altre informazioni, vedere [Registrare un'app di Azure AD per incorporare il contenuto di Power BI](register-app.md).

È necessario registrare l'applicazione usando l'account **master** dell'applicazione.

## <a name="create-app-workspaces-required"></a>Creare aree di lavoro per le app (obbligatorio)
È possibile sfruttare le aree di lavoro per le app per fornire un migliore isolamento se l'applicazione sta rispondendo a più clienti. I dashboard e i report sarebbero isolati tra i clienti. È quindi possibile usare un account di Power BI per ogni area di lavoro per le app per isolare ulteriormente le esperienze delle applicazioni tra i clienti.

> [!IMPORTANT]
> Non è possibile usare un'area di lavoro personale per sfruttare l'incorporamento per gli utenti esterni a Power BI.
> 
> 

Per creare un'area di lavoro per le app all'interno di Power BI è necessario che un utente che abbia una licenza Pro. Per impostazione predefinita, l'utente di Power BI che crea l'area di lavoro per le app sarà un amministratore della stessa.

> [!NOTE]
> L'account *master* dell'applicazione deve essere un amministratore dell'area di lavoro.
> 
> 

## <a name="content-migration"></a>Migrazione del contenuto
La migrazione del contenuto dalle raccolte dell'area di lavoro nel servizio Power BI può essere eseguita in parallelo alla soluzione attuale e non richiede alcun tempo di inattività.

Per agevolare la copia del contenuto da Power BI Embedded al servizio Power BI è disponibile uno **strumento di migrazione**. In particolare se la quantità del contenuto è elevata. Per altre informazioni, vedere [Power BI Embedded migration tool](migrate-tool.md) (Strumento di migrazione di Power BI Embedded).

La migrazione del contenuto si basa principalmente su due API.

1. Download PBIX: questa API può scaricare i file PBIX che sono stati caricati in Power BI a partire da novembre 2016.
2. Import PBIX: questa API consente di caricare qualsiasi file PBIX in Power BI.

Per alcuni frammenti di codice correlati, vedere [Code snippets for migrating content from Power BI Embedded](migrate-code-snippets.md) (Frammenti di codice per eseguire la migrazione del contenuto da Power BI Embedded).

### <a name="report-types"></a>Tipi di report
Esistono diversi tipi di report, ognuno dei quali richiede un flusso di migrazione leggermente diverso.

#### <a name="cached-dataset--report"></a>Report e set di dati memorizzati nella cache
I set di dati memorizzati nella cache fanno riferimento ai file PBIX che contengono dati importati e non dispongono di una connessione in tempo reale o DirectQuery.

**Flusso**

1. Chiamare l'API Download PBIX dall'area di lavoro PaaS.
2. Salvare i file PBIX.
3. Chiamare Import PBIX nell'area di lavoro SaaS.

#### <a name="directquery-dataset--report"></a>Report e set di dati DirectQuery
**Flusso**

1. Chiamare GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources e salvare la stringa di connessione ricevuta.
2. Chiamare l'API Download PBIX dall'area di lavoro PaaS.
3. Salvare i file PBIX.
4. Chiamare Import PBIX nell'area di lavoro SaaS.
5. Aggiornare la stringa di connessione chiamando - POST https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. Ottenere l'ID GW e dell'origine dei dati chiamando - GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. Aggiornare le credenziali dell'utente chiamando - PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

#### <a name="old-dataset--reports"></a>Report e set di dati precedenti
Si tratta di set di dati o report creati prima di ottobre 2016. Download PBIX non supporta i file PBIX che sono stati caricati prima di ottobre 2016

**Flusso**

1. Ottenere il file PBIX dall'ambiente di sviluppo (controllo della sorgente interna).
2. Chiamare Import PBIX nell'area di lavoro SaaS.

#### <a name="push-dataset--report"></a>Report e set di dati push
Download PBIX non supporta i set di dati dell'*API Push*. I dati del set di dati dell'API push non possono essere trasferiti da PaaS a SaaS.

**Flusso**

1. Chiamare l'API "Create dataset" con i set di dati JSON per creare i set di dati nell'area di lavoro SaaS.
2. Ricompilare il report per i set di dati creati*.

È possibile usare alcune soluzioni alternative per eseguire la migrazione del report dell'API Push da PaaS a SaaS eseguendo le operazioni seguenti.

1. Caricare i file PBIX fittizi nell'area di lavoro PaaS.
2. Clonare il report dell'API Push e associarlo al file PBIX fittizio del passaggio 1.
3. Scaricare il report dell'API Push con il file PBIX fittizio.
4. Caricare il file PBIX fittizio nell'area di lavoro di SaaS.
5. Creare set di dati push nell'area di lavoro SaaS.
6. Riassociare il report al set di dati dell'API Push.

## <a name="create-and-upload-new-reports"></a>Creare e caricare i nuovi report
Oltre al contenuto migrato dal servizio di Azure di Power BI Embedded, è possibile creare report e set di dati tramite Power BI Desktop e quindi pubblicare i report in un'area di lavoro per le app. Per pubblicare in un'area di lavoro per le app l'utente finale che pubblica i report deve avere una licenza di Power BI Pro.

## <a name="rebuild-your-application"></a>Ricompilare l'applicazione
1. È necessario modificare l'applicazione per usare le API REST di Power BI e il percorso del report in powerbi.com.
2. Ricompilare l'autenticazione AuthN/AuthZ usando l'account *master* per l'applicazione. È possibile sfruttare l'uso di un [token di incorporamento](https://msdn.microsoft.com/library/mt784614.aspx) per consentire all'utente di agire per conto di altri utenti.
3. Incorporare i report da powerbi.com nell'applicazione.

## <a name="map-your-users-to-a-power-bi-user"></a>Eseguire il mapping degli utenti a un utente di Power BI
All'interno dell'applicazione, verrà eseguito il mapping degli utenti gestiti all'interno dell'applicazione alle credenziali dell'account *master* di Power BI ai fini dell'applicazione. Le credenziali per questo account *master* di Power BI verranno memorizzate all'interno dell'applicazione e usate per creare token di incorporamento.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Cosa fare quando si è pronti per la produzione
Quando si è pronti a passare alla produzione, è necessario eseguire le operazioni seguenti.

* Se si usa un tenant diverso per lo sviluppo, è necessario assicurarsi che l'area di lavoro per le app, insieme ai dashboard e ai report, sia disponibile nell'ambiente di produzione. È inoltre necessario assicurarsi di aver creato l'applicazione in Azure AD per il tenant di produzione e di aver assegnato le autorizzazioni di dell'app adeguate, come indicato nel Passaggio 1.
* Acquistare una capacità adatta alle proprie esigenze. Per valutare al meglio la quantità e il tipo di capacità necessari, vedere [Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità per l'analisi incorporata). È possibile [acquistare capacità](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) in Azure.
* Modificare l'area di lavoro per le app e assegnarle una capacità Premium in Opzioni avanzate.
 
    ![](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity.png)
    
* Distribuire l'applicazione aggiornata nell'ambiente di produzione e iniziare a incorporare i report del servizio Power BI.

## <a name="after-migration"></a>Dopo la migrazione
È necessario eseguire alcune operazioni di pulitura all'interno di Azure.

* Rimuovere tutte le aree di lavoro dalla soluzione distribuita all'interno del servizio Azure di Power BI Embedded.
* Eliminare eventuali raccolte di aree di lavoro esistenti all'interno di Azure.

## <a name="next-steps"></a>Passaggi successivi
[Incorporamento con Power BI](embedding.md)  
[Power BI Embedded migration tool](migrate-tool.md) (Strumento di migrazione di Power BI Embedded)  
[Code snippets for migrating content from Power BI Embedded](migrate-code-snippets.md) (Frammenti di codice per eseguire la migrazione del contenuto da Power BI Embedded).  
[Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md)  
[Power BI Premium - what is it?](../service-premium.md) (Power BI Premium: definizione)  
[Archivio GIT API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Archivio GIT C# di Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Esempio di incorporamento JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata)  
[White paper su Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

