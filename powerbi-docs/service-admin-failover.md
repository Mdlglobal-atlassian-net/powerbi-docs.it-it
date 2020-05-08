---
title: Domande frequenti su disponibilità elevata, failover e ripristino di emergenza in Power BI
description: Informazioni sulle modalità con cui il servizio Power BI garantisce la disponibilità elevata e offre la continuità operativa e il ripristino di emergenza agli utenti.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3dd50d4f57b3146135cde5e91062ed3b2a0eecc1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77527339"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Domande frequenti su disponibilità elevata, failover e ripristino di emergenza in Power BI

Questo articolo illustra le modalità con cui il servizio Power BI garantisce la disponibilità elevata e offre la continuità operativa e il ripristino di emergenza agli utenti. Dopo aver letto questo articolo si comprenderà meglio come viene implementata la disponibilità elevata, in quali circostanze Power BI esegue un failover e cosa aspettarsi dal servizio in caso di failover.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Che cosa significa "disponibilità elevata" per Power BI?

Power BI è una soluzione Software as a Service (SaaS) completamente gestita.  Microsoft lo ha progettato e lo gestisce in modo che sia resiliente agli errori dell'infrastruttura e che gli utenti siano sempre in grado di accedere ai loro report.  Il servizio è supportato da un [Contratto di servizio 99,9%](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>Che cos'è un failover di Power BI?

Power BI mantiene più istanze di ogni componente nei data center di Azure (detti anche aree) per garantire la continuità operativa. Se si verifica un'interruzione del servizio o un problema per cui Power BI non è accessibile o utilizzabile in un'area, tutti i componenti di Power BI in tale area vengono sottoposti a failover su un'istanza di backup. Il failover ripristina la disponibilità e il funzionamento dell'istanza del servizio Power BI in una nuova area (in genere nella stessa posizione geografica, come specificato in [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Un'istanza del servizio Power BI sottoposta a failover supporta solo _operazioni di lettura_, ovvero le operazioni seguenti non sono supportate durante il failover: aggiornamenti, operazioni di pubblicazione di report, modifiche a dashboard o report e altre operazioni che richiedono modifiche ai metadati Power BI (ad esempio l'aggiunta di un commento a un report).  Le operazioni di lettura, ad esempio la visualizzazione di dashboard e di report (non basata su DirectQuery o Live Connect per origini dati locali) continuano a funzionare normalmente.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>In che modo le istanze di backup vengono mantenute sincronizzate con i dati degli utenti?

Tutti i componenti del servizio Power BI sincronizzano periodicamente le istanze di backup. L'obiettivo è una sincronizzazione temporizzata ogni 15 minuti per qualsiasi contenuto caricato o modificato in Power BI. In caso di failover Power BI usa la [replica con ridondanza geografica di Archiviazione di Azure](/azure/storage/common/storage-redundancy-grs) e la [replica con ridondanza geografica di Azure SQL](/azure/sql-database/sql-database-active-geo-replication) per garantire la presenza di istanze di backup in altre aree e il loro uso in caso di failover.

## <a name="where-are-the-failover-clusters-located"></a>Dove si trovano i cluster di failover?

Le istanze di backup si trovano nella stessa località geografica (area geografica) selezionata quando l'organizzazione ha effettuato la registrazione a Power BI, salvo diversa indicazione in [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Un'area geografica può contenere diverse aree e Microsoft può replicare i dati in una qualsiasi area inclusa in un'area geografica, per garantire la resilienza dei dati. Microsoft non replica né sposta i dati dei clienti al di fuori dell'area geografica. Per una mappa delle aree geografiche offerte da Power BI e delle aree al loro interno, vedere [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Su cosa si basa la decisione di Microsoft di eseguire il failover?

Due sistemi diversi indicano quando potrebbe essere necessario eseguire un failover:

- I probe di monitoraggio interni ed esterni segnalano la mancanza di disponibilità o l'impossibilità di garantire il funzionamento ottimale. Tali indicazioni possono basarsi su interruzioni del servizio rilevate in componenti di Power BI o in uno o più servizi dai quali dipende Power BI in una determinata area.
- Il team operativo centrale di Microsoft Azure segnala a Microsoft un'interruzione critica in un'area.

In entrambi i casi la decisione di eseguire il failover spetta ai membri del team executive Power BI; questa decisione non è automatizzata. Dopo che è stata presa la decisione il processo di failover si svolge automaticamente.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Come si determina che Power BI è in modalità di failover?

Viene pubblicata una notifica nella pagina del supporto di Power BI ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). La notifica include le operazioni principali che non sono disponibili durante il failover, tra cui la pubblicazione, l'aggiornamento, la creazione di dashboard, la duplicazione di dashboard e le modifiche alle autorizzazioni.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Quanto dura il processo di failover di Power BI?

La riattivazione di Power BI richiede circa 15 minuti dopo che è stata rilevata la necessità di un failover. Il tempo necessario per identificare la necessità di un failover varia a seconda dello scenario in cui si è verificata l'interruzione. 

Una volta attivata la modalità di failover, per eseguire il failover Power BI usa la replica geografica di Archiviazione di Azure. Queste repliche hanno in genere un punto di ripristino di 15 minuti, ma [Archiviazione di Azure non garantisce questo intervallo di tempo](https://docs.microsoft.com/azure/storage/common/storage-redundancy) con un contratto di servizio e pertanto nemmeno Power BI è in grado di garantirlo. 


## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Quando l'istanza di Power BI torna all'area di origine?

Le istanze del servizio Power BI tornano alla rispettiva area di origine quando viene risolto il problema che ha causato il failover. Visitare la pagina del supporto tecnico di Power BI: Quando il problema viene risolto, il team di Power BI rimuove la notifica che descrive il failover. A questo punto viene ripristinato il funzionamento normale.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>L'organizzazione è responsabile della disponibilità della propria soluzione Power BI?

Se la soluzione di Power BI usata nell'organizzazione include uno dei seguenti elementi, l'organizzazione deve adottare alcune misure per garantire la disponibilità elevata della soluzione:

- Se l'organizzazione usa Power BI Premium deve assicurarsi che la capacità Premium sia dimensionata in modo da soddisfare le richieste di carico della distribuzione.  Il [white paper Pianificazione e distribuzione di Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) e l'[app Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) possono aiutare a eseguire la pianificazione e a soddisfare questo requisito. Periodicamente vengono aggiunte nuove funzionalità all'app per le metriche e al portale di amministrazione di Power BI.
- Se l'organizzazione accede a origini dati locali tramite il gateway dati locale, è necessario configurare il gateway per il supporto della disponibilità elevata [come descritto in questo articolo](/data-integration/gateway/service-gateway-high-availability-clusters). Seguire queste linee guida sia che si stiano aggiornando i report in modalità di importazione o che si stia accedendo a dati o modelli di dati tramite DirectQuery o Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>I gateway funzionano quando è attiva la modalità di failover?

No. I dati richiesti dalle origini dati locali (qualsiasi report e dashboard basato su DirectQuery e Live Connect) non funziona durante un failover. Tuttavia la configurazione del gateway resta invariata: quando l'istanza di Power BI torna allo stato originale, i gateway tornano a funzionare normalmente.
