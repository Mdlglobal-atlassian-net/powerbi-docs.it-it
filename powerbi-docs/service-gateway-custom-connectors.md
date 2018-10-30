---
title: Usare i connettori dati personalizzati con il gateway dati locale
description: È possibile usare i connettori dati personalizzati con il gateway dati locale.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 08/08/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 75e760c1ad808d05986de46cf2bc427bb078e3ce
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101279"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Usare i connettori dati personalizzati con il gateway dati locale

I connettori dati per Power BI consentono di connettersi e accedere ai dati da un'applicazione, un servizio o un'origine dati. È possibile sviluppare connettori dati personalizzati e usarli in Power BI Desktop.

Per altre informazioni su come sviluppare connettori dati personalizzati per Power BI, consultare la documentazione [qui](http://aka.ms/dataconnectors).

Quando si creano report in Power BI Desktop che usano connettori dati personalizzati, è possibile usare il gateway dati locale per aggiornare i report dal servizio Power BI.

## <a name="here-is-a-guide-on-how-to-enable-and-use-this-capability"></a>Ecco una guida su come abilitare e usare questa funzionalità

Quando si installa la versione di luglio 2018 del gateway dati locale o una versione successiva, è possibile visualizzare una scheda "Connettori" nello strumento di configurazione con un'opzione per scegliere una cartella da cui caricare i connettori personalizzati. Assicurarsi di selezionare una cartella accessibile dall'utente che esegue il servizio gateway ("NT SERVICE\PBIEgwService" per impostazione predefinita). Il gateway carica automaticamente i file del connettore personalizzato che si trovano in tale cartella e dovrebbero diventare visibili nell'elenco dei connettori dati.

![Connettore personalizzato 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Se si usa la versione personale del gateway dati locale, a questo punto sarà possibile caricare il report di Power BI nel servizio Power BI e usare il gateway per aggiornarlo.

Per la versione aziendale del gateway, sarà ancora necessario creare un'origine dati per il connettore personalizzato. Nella pagina delle impostazioni del gateway nel servizio Power BI viene visualizzata una nuova opzione quando si seleziona il cluster del gateway per consentire l'uso dei connettori personalizzati con questo cluster. Assicurarsi che in tutti i gateway del cluster sia installata la versione di aggiornamento di luglio 2018 o un versione successiva, affinché questa opzione sia disponibile. Selezionare ora questa opzione per consentire l'uso dei connettori personalizzati con questo cluster.

![Connettore personalizzato 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Quando questa opzione è abilitata, i connettori personalizzati vengono visualizzati come origini dati disponibili che è possibile creare in questo cluster di gateway. Dopo aver creato un'origine dati usando il nuovo connettore personalizzato, è ora possibile aggiornare i report di Power BI usando questo connettore personalizzato nel servizio Power BI.

![Connettore personalizzato 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Assicurarsi che la cartella creata sia accessibile per il servizio gateway in background. In genere, le cartelle nella cartella di Windows o le cartelle di sistema dell'utente non saranno accessibili. Lo strumento di configurazione del gateway mostra un messaggio se la cartella non è accessibile (ciò non vale per la versione personale del gateway)
* Affinché i connettori personalizzati possano interagire con il gateway dati locale, è necessario implementare una sezione "TestConnection" nel codice del connettore personalizzato. Ciò non è necessario quando si usano connettori personalizzati con Power BI Desktop. È possibile avere un connettore personalizzato che funziona con la versione desktop, ma non con il gateway per questo motivo. Vedere [questa documentazione](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) per informazioni su come implementare una sezione TestConnection.

## <a name="next-steps"></a>Passaggi successivi

* [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)  
* [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  
* [Analisi approfondita del gateway dati locale](service-gateway-onprem-indepth.md)  
* [Gateway dati locale (modalità personale)](service-gateway-personal-mode.md)
* [Configurazione delle impostazioni del proxy per il gateway dati locale](service-gateway-proxy.md)  
* [Usare Kerberos per l'accesso Single Sign-On (SSO) da Power BI alle origini dati locali](service-gateway-sso-kerberos.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
