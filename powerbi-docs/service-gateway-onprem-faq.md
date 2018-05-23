---
title: Domande frequenti sul gateway dati locale
description: In questo articolo vengono riportate le domande frequenti sul gateway dati locale. In un'unica pagina vengono raccolte tutte le domande frequenti sul gateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b4ecec3b2e53c2fea0fcbb7d78d1114da1a105ed
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="on-premises-data-gateway-faq"></a>Domande frequenti sul gateway dati locale
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Domanda:** È possibile usare msdmpump.dll per creare mapping del nome utente effettivo personalizzati per Analysis Services?  
**Risposta:** No. Al momento questa operazione non è supportata.

**Domanda:** È possibile usare il gateway per connettersi a un'istanza multidimensionale (OLAP)?  
**Risposta:** Sì. Il gateway dati locale supporta connessioni in tempo reale a modelli tabulari e multidimensionali di Analysis Services.

**Domanda:** Cosa accade se si installa il gateway in un computer in un dominio diverso dal server locale che usa l'autenticazione di Windows?  
**Risposta:** Non viene offerta alcuna garanzia. Tutto dipende dalla relazione di trust tra i due domini. Se i due domini diversi si trovano in un modello di dominio trusted, il gateway potrebbe riuscire a connettersi al server Analysis Services e il nome utente effettivo potrà essere risolto. In caso contrario, potrebbe verificarsi un errore di accesso.

**Domanda:** Come è possibile trovare quale nome utente effettivo viene passato al server Analysis Services locale?  
**Risposta:** La risposta a questa domanda viene fornita nell'[articolo relativo alla risoluzione dei problemi](service-gateway-onprem-tshoot.md).

**Domanda:** Se in Analysis Services si hanno 25 database, è possibile abilitarli contemporaneamente per il gateway?  
**Risposta:** No. È una funzionalità prevista, ma non è ancora disponibile una data precisa.

## <a name="administration"></a>Amministrazione
**Domanda:** È possibile avere più amministratori per un gateway?  
**Risposta:** Sì. Quando si gestisce un gateway, è possibile aggiungere altri amministratori nella scheda dell'amministratore.

**Domanda:** È necessario che l'amministratore del gateway sia un amministratore nel computer in cui è installato il gateway?  
**Risposta:** No. L'amministratore del gateway viene usato per gestire il gateway all'interno del servizio.

**Domanda:** È possibile impedire agli utenti dell'organizzazione di creare un gateway?  
**Risposta:** No. È una funzionalità prevista, ma non è ancora disponibile una data precisa.

**Domanda:** È possibile ottenere informazioni sull'utilizzo e sulle statistiche dei gateway presenti nell'organizzazione?  
**Risposta:** No. È una funzionalità prevista, ma non è ancora disponibile una data precisa.

## <a name="power-bi"></a>Power BI
**Domanda:** È necessario eseguire l'aggiornamento del gateway personale?
**Risposta:** No, si può continuare a usare il gateway personale di Power BI.

**Domanda:** Con quale frequenza vengono aggiornati i riquadri in un dashboard in Power BI quando si è connessi tramite il gateway dati locale?  
**Risposta:** Circa dieci minuti. Le connessioni DirectQuery hanno esattamente questo scopo. Questo non significa che un riquadro inoltra una query al server locale e visualizza nuovi dati ogni dieci minuti.

**Domanda:** È possibile caricare le cartelle di lavoro di Excel con modelli di dati Power Pivot che si connettono alle origini dati locali? Per questo scenario è necessario un gateway?  
**Risposta:** Sì, è possibile caricare la cartella di lavoro. No, non è necessario un gateway. Ma, poiché i dati risiederanno nel modello di dati di Excel, i report in Power BI basati sulla cartella di lavoro di Excel non saranno in tempo reale. Per aggiornare i report in Power BI, è necessario caricare nuovamente una cartella di lavoro aggiornata ogni volta. In alternativa, usare il gateway con l'aggiornamento pianificato.

**Domanda:** Se gli utenti condividono i dashboard con una connessione DirectQuery, gli altri utenti potranno visualizzare i dati anche se non hanno le stesse autorizzazioni?  
**Risposta:** Per un dashboard connesso ad Analysis Services, gli utenti visualizzeranno solo i dati a cui hanno accesso. Se gli utenti non hanno le stesse autorizzazioni, non potranno visualizzare i dati. Per altre origini dati, tutti gli utenti condivideranno le credenziali immesse dall'amministratore per l'origine dati.

**Domanda:** perché non è possibile connettersi al server Oracle?  
**Risposta:** potrebbe essere necessario installare il client Oracle e configurare il file tnsnames.ora con le informazioni sul server corretto per consentire la connessione al server Oracle. Si tratta di un'installazione separata all'esterno del gateway. Per altre informazioni, vedere [Installazione del client Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Domanda:** il gateway funzionerà con ExpressRoute?  
**Risposta:** Sì. Per altre informazioni su ExpressRoute e Power BI, vedere [Power BI ed ExpressRoute](service-admin-power-bi-expressroute.md).

## <a name="next-steps"></a>Passaggi successivi
[Gateway dati locale](service-gateway-onprem.md)  
[Analisi approfondita del gateway dati locale](service-gateway-onprem-indepth.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

