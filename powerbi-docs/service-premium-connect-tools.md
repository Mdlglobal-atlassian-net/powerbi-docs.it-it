---
title: Connettersi ai set di dati di Power BI Premium con le applicazioni client e gli strumenti (anteprima)
description: Viene descritto come connettersi ai set di dati in Power BI Premium da strumenti e applicazioni client.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941514"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Connettersi ai set di dati con le applicazioni client e gli strumenti (anteprima)

Supporto di aree di lavoro e set di dati di BI Premium di Power *sola lettura* le connessioni da Microsoft e strumenti e applicazioni client di terze parti. 

> [!NOTE]
> Questo articolo è destinato solo a introdurre la connettività di sola lettura per le aree di lavoro di Power BI Premium e i set di dati. Si *non è* concepito per offrire informazioni approfondite su programmabilità, gli strumenti specifici e le applicazioni, architettura e gestione dell'area di lavoro e set di dati. Gli argomenti descritti di seguito richiedono una conoscenza approfondita dell'architettura di database modello tabulare di Analysis Services e l'amministrazione.

## <a name="protocol"></a>Protocollo

Power BI Premium Usa la [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) protocollo (XMLA) per le comunicazioni tra le applicazioni client e il motore che gestisce le aree di lavoro e set di dati. Queste comunicazioni sono tramite ciò che viene comunemente fatto riferimento come endpoint XMLA. XMLA è lo stesso protocollo di comunicazione usato dal motore di Microsoft Analysis Services, che, dietro le quinte, esegue Power BI Semantic Model modellazione, governance, ciclo di vita e gestione dei dati. 

La maggior parte delle applicazioni e strumenti client in modo esplicito non comunicare con il motore con gli endpoint XMLA. Al contrario, usano le librerie client, ad esempio MSOLAP, ADOMD e AMO come intermediario tra l'applicazione client e il motore che comunica esclusivamente tramite XMLA.


## <a name="supported-tools"></a>Strumenti supportati

Questi strumenti supportano l'accesso di sola lettura per le aree di lavoro di Power BI Premium e i set di dati:

**SQL Server Management Studio (SSMS)** -oggetto TraceEvent, MDX, XMLA e DAX supporta le query. Richiede la versione 18.0. Scaricare [qui](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** -incluso con SSMS 18.0 (anteprima), questo strumento offre analisi e debug di eventi del server. È possibile acquisire e salvare i dati su ogni evento in un file o tabella da analizzare in un secondo momento. Mentre ufficialmente deprecato per SQL Server Profiler continua a essere incluso in SQL Server Management Studio e rimane supportata per Analysis Services e a questo punto, Power BI Premium. Per altre informazioni, vedere [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX Studio** - Open source, lo strumento della community per l'esecuzione e l'analisi DAX esegue una query in Analysis Services. Richiede la versione 2.8.2 o versione successiva. Per altre informazioni, vedere [daxstudio.org](https://daxstudio.org/).

**Tabelle pivot di Excel** -versione a portata di clic di Office 16.0.11326.10000 o versione successiva è obbligatorio.

**Terze parti** : include le applicazioni di visualizzazione dei dati client e gli strumenti che possono connettersi a, query e usare set di dati in Power BI Premium. La maggior parte degli strumenti richiedono le versioni più recenti delle librerie client MSOLAP, ma alcuni possono utilizzare ADOMD.

## <a name="client-libraries"></a>Librerie client

Le librerie client sono necessari per le applicazioni client e gli strumenti per la connessione alle aree di lavoro di Power BI Premium. Le stesse librerie client utilizzate per la connessione ad Analysis Services sono supportate anche in Power BI Premium. Le applicazioni client di Microsoft, ad esempio Excel, SQL Server Management Studio (SSMS) e SQL Server Data Tools (SSDT) installano queste tre librerie client e aggiornarle con gli aggiornamenti regolari dell'applicazione. In alcuni casi, in particolare con le applicazioni di terze parti e gli strumenti, potrebbe essere necessario installare versioni più recenti delle librerie client. Le librerie client vengono aggiornate ogni mese. Per altre informazioni, vedere [librerie Client per la connessione ad Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>La connessione a un'area di lavoro Premium

È possibile connettersi alle aree di lavoro assegnati alla capacità Premium dedicata. Aree di lavoro assegnati a una capacità dedicata includono una stringa di connessione nel formato dell'URL. 

Per ottenere la stringa di connessione dell'area di lavoro in Power BI, in **delle impostazioni dell'area di lavoro**via le **Premium** nella scheda **connessione dell'area di lavoro**, fare clic su **copiare**.

![Stringa di connessione dell'area di lavoro](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Le connessioni dell'area di lavoro usano il formato di URL seguente per risolvere un'area di lavoro come se fosse un nome del server Analysis Services:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Per esempio `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` è di maiuscole e minuscole e possono includere spazi. 

### <a name="to-connect-in-ssms"></a>Per la connessione in SSMS

Nelle **Connetti al Server** > **tipo Server**, selezionare **Analysis Services**. Nelle **nome Server**, immettere l'URL. Nelle **Authentication**, selezionare **Active Directory - universale con supporto MFA**e quindi in **nome utente**, immettere l'ID utente dell'organizzazione. 

Quando si è connessi, l'area di lavoro viene visualizzato come un server Analysis Services e i set di dati nell'area di lavoro vengono visualizzati come i database.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Catalogo iniziale

Alcuni strumenti, ad esempio SQL Server Profiler, si potrebbe essere necessario specificare un *Initial Catalog*. Specificare un set di dati (database) nell'area di lavoro. Nelle **Connetti al Server**, fare clic su **opzioni**. Nel **Connetti al Server** finestra di dialogo via il **proprietà connessione** nella scheda **Connetti al database**, immettere il nome del set di dati.

### <a name="duplicate-workspace-name"></a>Nome dell'area di lavoro è duplicato

Quando ci si connette a un'area di lavoro con lo stesso nome di un'altra area di lavoro, potrebbe essere visualizzato l'errore seguente: **Non è possibile connettersi a powerbi://api.powerbi.com/v1.0/ [nome del tenant] / [nome area di lavoro].**

Per risolvere questo errore, oltre al nome dell'area di lavoro, specificare il ObjectIDGuid, che possono essere copiati da objectID dell'area di lavoro nell'URL. Aggiungere il parametro objectID all'URL della connessione. Ad esempio, 'powerbi://api.powerbi.com/v1.0/myorg/Contoso vendite - 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>Nome set di dati duplicati

Quando ci si connette a un set di dati con lo stesso nome di un altro set di dati nella stessa area di lavoro, aggiungere il guid del set di dati al nome del set di dati. È possibile ottenere sia nome set di dati *e* guid quando si è connessi all'area di lavoro in SQL Server Management Studio. 

### <a name="delay-in-datasets-shown"></a>Ritardo in set di dati visualizzati

Quando ci si connette a un'area di lavoro, le modifiche dal set di dati nuovi, eliminati e rinominati possono richiedere fino a 5 minuti prima della visualizzazione. 

### <a name="unsupported-datasets"></a>Set di dati non supportato

Set di dati seguenti non sono accessibili tramite endpoint XMLA. Questi set di dati *non* visualizzato sotto l'area di lavoro in SQL Server Management Studio o in altri strumenti: 

- Set di dati con una connessione dinamica a un modelli di Analysis Services. 
- Set di dati con i dati di Push con l'API REST.
- I set di dati della cartella di lavoro di Excel. 

Set di dati seguenti non sono supportati nel servizio Power BI:   

- Set di dati con una connessione dinamica a un set di dati di Power BI.

## <a name="audit-logs"></a>Log di controllo 

Quando le applicazioni client e gli strumenti di connettano a un'area di lavoro, accesso tramite endpoint XMLA viene registrato nei log di controllo di Power BI con il **GetWorkspaces** operazione. Per altre informazioni, vedere [controllo di Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Vedere anche

[Riferimenti di Analysis Services](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services Tabular Protocol](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Viste a gestione dinamica (DMV)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
