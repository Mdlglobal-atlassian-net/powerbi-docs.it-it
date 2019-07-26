---
title: Usare i connettori dati personalizzati con il gateway dati locale
description: È possibile usare i connettori dati personalizzati con il gateway dati locale.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271782"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Usare i connettori dati personalizzati con il gateway dati locale

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

I connettori dati per Power BI consentono di connettersi e accedere ai dati da un'applicazione, un servizio o un'origine dati. È possibile sviluppare connettori dati personalizzati e usarli in Power BI Desktop.

Per altre informazioni su come sviluppare connettori dati personalizzati per Power BI, consultare la [pagina di GitHub relativa all'SDK Data Connector](http://aka.ms/dataconnectors). Questo sito include informazioni introduttive ed esempi per Power BI e Power Query.

Quando si creano report in Power BI Desktop che usano connettori dati personalizzati, è possibile usare il gateway dati locale per aggiornare i report dal servizio Power BI.

## <a name="how-to-enable-and-use-this-capability"></a>Come abilitare e usare questa funzionalità

Quando si installa la versione di luglio 2018 del gateway dati locale o una versione successiva, è possibile visualizzare una scheda **Connettori** nell'app del gateway dati locale con un'opzione per scegliere una cartella da cui caricare i connettori personalizzati. Assicurarsi di selezionare una cartella accessibile dall'utente che esegue il servizio gateway (*NT SERVICE\PBIEgwService* per impostazione predefinita). Il gateway carica automaticamente i file del connettore personalizzato che si trovano in tale cartella e diventano visibili nell'elenco dei connettori dati.

![Connettore personalizzato 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Se si usa il gateway dati locale (modalità personale), a questo punto sarà possibile caricare il report di Power BI nel servizio Power BI e usare il gateway per aggiornarlo.

Per il gateway dati locale, sarà ancora necessario creare un'origine dati per il connettore personalizzato. Nella pagina delle impostazioni del gateway nel servizio Power BI viene visualizzata una nuova opzione quando si seleziona il cluster del gateway per consentire l'uso dei connettori personalizzati con questo cluster. Assicurarsi che in tutti i gateway del cluster sia installata la versione di aggiornamento di luglio 2018 o un versione successiva, affinché questa opzione sia disponibile. Selezionare ora questa opzione per consentire l'uso dei connettori personalizzati con questo cluster.

![Connettore personalizzato 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Quando questa opzione è abilitata, i connettori personalizzati vengono visualizzati come origini dati disponibili che è possibile creare in questo cluster di gateway. Dopo aver creato un'origine dati usando il nuovo connettore personalizzato, è ora possibile aggiornare i report di Power BI usando questo connettore personalizzato nel servizio Power BI.

![Connettore personalizzato 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Assicurarsi che la cartella creata sia accessibile per il servizio gateway in background. In genere, le cartelle nella cartella di Windows o le cartelle di sistema dell'utente non saranno accessibili. L'app del gateway dati locale visualizza un messaggio se la cartella non è accessibile (ciò non vale per la versione personale del gateway)
* Affinché i connettori personalizzati possano interagire con il gateway dati locale, è necessario implementare una sezione "TestConnection" nel codice del connettore personalizzato. Ciò non è necessario quando si usano connettori personalizzati con Power BI Desktop. È possibile avere un connettore personalizzato che funziona con la versione desktop, ma non con il gateway per questo motivo. Vedere [questa documentazione](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) per informazioni su come implementare una sezione TestConnection.

## <a name="next-steps"></a>Passaggi successivi

* [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)  
* [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [Configurare le impostazioni del proxy per il gateway dati locale](/data-integration/gateway/service-gateway-proxy)  
* [Usare Kerberos per l'accesso Single Sign-On (SSO) da Power BI alle origini dati locali](service-gateway-sso-kerberos.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
