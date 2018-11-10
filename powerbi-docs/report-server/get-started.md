---
title: Che cos'è Server di report di Power BI?
description: Una panoramica su Server di Report di Power BI e sulla sua interazione con SQL Server Reporting Services (SSRS) e il resto di Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 10/24/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 95a97c86ae7d17091b49fbf33cf5ec0d26053c3e
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101396"
---
# <a name="what-is-power-bi-report-server"></a>Che cos'è Server di report di Power BI?

Server di report di Power BI è un server di report locale con un portale Web in cui è possibile visualizzare e gestire report e indicatori KPI, oltre che gli strumenti per la creazione di report, report impaginati, report per dispositivi mobili e indicatori KPI di Power BI. Gli utenti possono accedere ai report in vari modi, ad esempio in un Web browser, in un dispositivo mobile o come messaggio di posta elettronica nella posta in arrivo.

![Portale Web del server di report di Power BI](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Confronto di Server di report di Power BI 
Server di report di Power BI è simile a SQL Server Reporting Services e al servizio Power BI online, ma per aspetti diversi. Come il servizio Power BI, Server di report di Power BI ospita report di Power BI (PBIX) e file di Excel. Come Reporting Services, è una soluzione locale e ospita report impaginati (RDL). Server di report di Power BI è un soprainsieme di Reporting Services: in Server di report di Power BI si può fare tutto ciò che si può fare in Reporting Services e altro ancora, con l'aggiunta del supporto per i report di Power BI. Per informazioni dettagliate, vedere [Confronto tra Server di report di Power BI e il servizio Power BI](compare-report-server-service.md).

## <a name="licensing-power-bi-report-server"></a>Licenze di Server di report di Power BI
Server di report di Power BI è disponibile tramite due diverse licenze: [Power BI Premium](../service-premium.md) e [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions) con Software Assurance. Con una licenza di Power BI Premium è possibile creare una distribuzione ibrida cloud e locale.  

> [!NOTE]
> Per Power BI Premium, Server di report di Power BI è incluso solo con gli SKU P. Non è incluso con gli SKU EM.

## <a name="web-portal"></a>Portale Web
Il punto di ingresso a Server di report di Power BI è un portale Web sicuro che può essere visualizzato in qualsiasi browser moderno. Qui è possibile accedere a tutti i report e agli indicatori KPI. Il contenuto sul portale Web è organizzato in una gerarchia di cartelle tradizionale. All'interno delle cartelle, il contenuto del portale è organizzato per tipo: report di Power BI, report per dispositivi mobili, report impaginati, indicatori KPI e cartelle di lavoro di Excel, più set di dati condivisi e origini dati condivise da usare come componenti essenziali per i propri report. È possibile contrassegnare gli elementi preferiti per visualizzarli in un'unica cartella. e creare direttamente gli indicatori KPI 

![Portale Web del server di report di Power BI](media/get-started/web-portal.png)

A seconda delle autorizzazioni di cui si dispone, è possibile gestire il contenuto nel portale Web. È possibile pianificare l'elaborazione dei report, accedere ai report su richiesta e sottoscrivere report pubblicati. È anche possibile [personalizzare](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) il portale Web. 

Altre informazioni sul [portale Web di Server di report di Power BI](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Report di Power BI
I report di Power BI (PBIX) si creano con la versione di Power BI Desktop ottimizzata per il server di report. Dopo la creazione, è possibile pubblicarli e visualizzarli nel portale Web nel proprio ambiente.

![Report di Power BI in Server di report di Power BI](media/get-started/powerbi-reports.png)

Un report di Power BI consente di visualizzare un modello di dati da più punti di vista, grazie a visualizzazioni che rappresentano conclusioni e approfondimenti diversi ottenuti da tale modello di dati.  Un report può includere una sola visualizzazione oppure contenere pagine con più visualizzazioni. In base al proprio ruolo, è possibile leggere ed esplorare i report oppure crearli per altri utenti.

[Installare Power BI Desktop ottimizzato per Server di report di Power BI](quickstart-create-powerbi-report.md).

## <a name="paginated-reports"></a>Report impaginati
I report impaginati (. RDL) sono report in formato documento con visualizzazioni, in cui tabelle si espandono orizzontalmente e verticalmente per mostrare tutti i dati, continuando da una pagina all'altra in base alle esigenze. Sono ideali per generare documenti con layout fisso e ad alta risoluzione grafica ottimizzati per la stampa, ad esempio file in formato PDF e Word.

![Report impaginati in Server di report di Power BI](media/get-started/paginated-reports.png)

È possibile creare report dall'aspetto moderno con [Generatore report](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) o Progettazione report in [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Report per dispositivi mobili di Reporting Services
I report per dispositivi mobili si connettono ai dati locali e hanno un layout reattivo che si adatta a diversi dispositivi e ai diversi modi per impugnarli. Si creano con Microsoft SQL Server Mobile Report Publisher.

Altre informazioni sui [Report per dispositivi mobili di Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Funzionalità di programmazione del server di report
È possibile sfruttare le funzionalità di programmazione di Server di report di Power BI in modo da estendere e personalizzare la funzionalità di creazione di report, con API che permettono di integrare o estendere l'elaborazione di dati e report nelle applicazioni personalizzate.

Altra [documentazione per sviluppatori di server di report](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Passaggi successivi
[Installare il server di report di Power BI](install-report-server.md)  
[Scaricare Generatore report](https://www.microsoft.com/download/details.aspx?id=53613)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)


