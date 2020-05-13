---
title: Domande frequenti sul gateway dati locale - Power BI
description: Questo articolo include le domande frequenti sul gateway dati locale per Power BI. L'articolo raccoglie le domande frequenti sul gateway usato in Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: f64fcd86d54c20e1318d38c2a73e9bca2174558a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302668"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Domande frequenti sul gateway dati locale - Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Domanda:** È necessario aggiornare il gateway dati locale (modalità personale)?

**Risposta:** No, è possibile continuare a usare il gateway (modalità personale) per Power BI.

**Domanda:** Sono necessarie autorizzazioni speciali per installare il gateway e gestirlo nel servizio Power BI?

**Risposta:** Non sono richieste autorizzazioni speciali.

**Domanda:** è possibile caricare le cartelle di lavoro di Excel con modelli di dati Power Pivot che si connettono alle origini dati locali? Per questo scenario è necessario un gateway? 

**Risposta:** sì, è possibile caricare la cartella di lavoro. No, non è necessario un gateway. Poiché tuttavia i dati risiederanno nel modello di dati di Excel, i report in Power BI basati sulla cartella di lavoro di Excel non saranno animati. Per aggiornare i report in Power BI, è necessario caricare ogni volta una cartella di lavoro aggiornata. In alternativa, usare il gateway con l'aggiornamento pianificato.

**Domanda:** se gli utenti condividono i dashboard con una connessione DirectQuery, gli altri utenti potranno visualizzare i dati anche se non hanno le stesse autorizzazioni? 

**Risposta:** per un dashboard connesso ad Azure Analysis Services, gli utenti visualizzeranno solo i dati a cui hanno accesso. Se gli utenti non hanno le stesse autorizzazioni, non potranno visualizzare i dati. Per altre origini dati, tutti gli utenti condivideranno le credenziali immesse dall'amministratore per l'origine dati.

**Domanda:** perché non è possibile connettersi al server Oracle? 

**Risposta:** potrebbe essere necessario installare il client Oracle e configurare il file tnsnames.ora con le informazioni sul server corretto per consentire la connessione al server Oracle. Si tratta di un'installazione separata all'esterno del gateway. Per altre informazioni, vedere [Installazione del client Oracle](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Domanda:** l'uso di script R è supportato?

**Risposta:** gli script R sono supportati solo per la modalità personale.

## <a name="analysis-services-in-power-bi"></a>Analysis Services in Power BI

**Domanda:** è possibile usare msdmpump.dll per creare mapping del nome utente effettivo personalizzati per Analysis Services? 

**Risposta:** No. Al momento questa operazione non è supportata.

**Domanda:** è possibile usare il gateway per connettersi a un'istanza multidimensionale (OLAP)? 

**Risposta:** Sì. Il gateway dati locale supporta connessioni in tempo reale a modelli tabulari e multidimensionali di Analysis Services.

**Domanda:** cosa accade se si installa il gateway in un computer in un dominio diverso dal server locale che usa l'autenticazione di Windows? 

**Risposta:** non viene offerta alcuna garanzia. Tutto dipende dalla relazione di trust tra i due domini. Se i due domini diversi si trovano in un modello di dominio trusted, il gateway può connettersi al server Analysis Services e il nome utente effettivo può essere risolto. In caso contrario, si verifica un errore di accesso.

**Domanda:** come è possibile trovare quale nome utente effettivo viene passato al server Analysis Services locale? 

**Risposta:** la risposta a questa domanda viene fornita nell'[articolo relativo alla risoluzione dei problemi](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Passaggi successivi

* [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)

Altre domande? Provare la [Community di Power BI](https://community.powerbi.com/).
