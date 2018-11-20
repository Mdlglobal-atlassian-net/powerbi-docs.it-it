---
title: Requisiti hardware e software per l'installazione del server di report di Power BI
description: Questo articolo elenca i requisiti minimi di hardware e software per l'installazione e l'esecuzione del server di report di Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 11/08/2018
ms.author: maghan
ms.openlocfilehash: c8904f3025a0a60557b1d3efb54ea6bc18c20da4
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507907"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Requisiti hardware e software per l'installazione del server di report di Power BI
Questo articolo elenca i requisiti minimi di hardware e software per l'installazione e l'esecuzione del server di report di Power BI.

## <a name="processor-memory-and-operating-system-requirements"></a>Requisiti di processore, memoria e sistema operativo

| Componente | Requisito |
| --- | --- |
| .NET Framework |4.6<br><br>È possibile installare manualmente .NET Framework da [Microsoft .NET Framework 4.6 (programma di installazione Web) per Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Per altre informazioni, suggerimenti e indicazioni su .NET Framework 4.6 vedere [Guida alla distribuzione di .NET Framework per gli sviluppatori](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>Windows 8.1, and Windows Server 2012 R2 richiedono [KB2919355](http://support.microsoft.com/kb/2919355) prima dell'installazione di .NET Framework 4.6. |
| Disco rigido |Il server di report di Power BI richiede almeno 1 GB di spazio su disco disponibile.<br><br>Sarà necessario spazio aggiuntivo nel server di database che ospita il database del server di report. |
| Memoria |**Minimo:** 1 GB<br/><br/> **Consigliato:** almeno 4 GB |
| Velocità del processore |**Minimo:** processore x64: 1,4 GHz<br/><br/> **Consigliato:** 2,0 GHz o superiore |
| Tipo di processore |x64 Processor: AMD Opteron, AMD Athlon 64, Intel Xeon con supporto Intel EM64T, Intel Pentium IV con supporto EM64T |
| Sistema operativo |Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> L'installazione del server di report di Power BI è supportata solo nei processori x64.
> 
> 

## <a name="database-server-version-requirements"></a>Requisiti della versione del server di database
SQL Server viene usato per ospitare i database del server di report. L'istanza del motore di database di SQL Server può essere locale o remota. Di seguito sono elencate le versioni supportate del motore di database di SQL Server che possono essere usate per ospitare i database del server di report:

* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Quando si crea il database del server di report in un computer remoto, è necessario configurare la connessione in modo da usare un account utente di dominio o un account del servizio con accesso alla rete. Se si decide di usare un'istanza remota di SQL Server, valutare attentamente quali credenziali il server di report deve usare per connettersi all'istanza di SQL Server. Per altre informazioni, vedere [Configurare una connessione al database del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considerazioni
Il server di Report di Power BI installerà i valori predefiniti per configurare le impostazioni principali necessarie per rendere operativo un server di report. Presenta i requisiti seguenti:

* Disponibilità di un motore di database di SQL Server dopo l'installazione e prima della configurazione del database per il server di report. L'istanza del motore di database ospita il database del server di report che verrà creato da Reporting Services Configuration Manager. Il motore di database non è necessario per l'effettiva esperienza di configurazione.
- [Funzionalità di Reporting Services supportate dalle edizioni di SQL Server](https://docs.microsoft.com/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) descrive le differenze tra le edizioni di SQL Server.
* L'account utente che esegue il programma di installazione deve essere un membro del gruppo di amministratori locali.
* L'account che esegue Gestione configurazione Reporting Services deve avere l'autorizzazione per accedere e creare database nell'istanza del motore di database che ospita i database del server di report.
* Il programma di installazione deve poter usare i valori predefiniti per prenotare gli URL che forniscono l'accesso al server di report e al portale Web. Questi valori sono la porta 80, un carattere jolly complesso e i nomi delle directory virtuali nel formato **ReportServer** e **Report**.

## <a name="read-only-domain-controller-rodc"></a>Controller di dominio di sola lettura (RODC)
 È possibile installare il server di report in un ambiente con un controller di dominio di sola lettura (RODC). Tuttavia, Reporting Services deve accedere a un controller di dominio di lettura/scrittura per funzionare correttamente. Se Reporting Services può accedere solo a un RODC, si possono verificare errori quando si prova ad amministrare il servizio.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Report di Power BI e connessioni dinamiche di Analysis Services
È possibile usare una connessione dinamica su istanze tabulari o multidimensionali. Per il corretto funzionamento, il server di Analysis Services deve usare la versione ed edizione corretta.

| **Versione del server** | **SKU necessario** |
| --- | --- |
| 2012 SP1 CU4 o versione successiva |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 e versioni successive |SKU standard o versione successiva |

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Server di report di Power BI?](get-started.md)  
[Panoramica amministratore](admin-handbook-overview.md)  
[Installare il server di report di Power BI](install-report-server.md)  
[Scaricare Generatore report](https://www.microsoft.com/download/details.aspx?id=53613)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

