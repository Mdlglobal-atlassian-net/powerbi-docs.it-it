---
title: Gateway dati locale
description: Questa è una panoramica del gateway dati locale per Power BI. È possibile usare questo gateway per usare le origini dati DirectQuery. È anche possibile usare questo gateway per aggiornare i set di dati cloud con dati locali.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 06/05/2018
ms.openlocfilehash: 9a739efdba84279e938fd8e13d6521cf975d0b9d
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679019"
---
# <a name="on-premises-data-gateway"></a>Gateway dati locale

Il gateway dati locale viene usato come collegamento, fornendo un trasferimento di dati rapido e sicuro tra i dati locali, ovvero dati non sul cloud, e i servizi Power BI, Microsoft Flow, App per la logica e PowerApps.

È possibile usare un singolo gateway con diversi servizi contemporaneamente. Se si usa Power BI, oltre a PowerApps, è possibile usare per entrambi un singolo gateway. Il gateway dipende dall'account con cui si accede.

> [!NOTE]
> Il gateway di dati locale implementa la compressione dei dati e la crittografia del trasporto in tutte le modalità.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Limitazioni di connessioni dinamiche ad Analysis Services

È possibile usare una connessione dinamica su istanze tabulari o multidimensionali.

| **Versione del server** | **SKU necessario** |
| --- | --- |
| 2012 SP1 CU4 o versione successiva |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU standard o versione successiva |

* La formattazione a livello di cella e le funzionalità di conversione non sono supportate.
* Azioni e set denominati non sono esposti in Power BI. È comunque possibile connettersi a cubi multidimensionali che contengono anche azioni o set denominati e creare oggetti visivi e report.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Scaricare e installare il gateway dati locale

Per scaricare il gateway, selezionare **Gateway dati** nel menu Download. Scaricare il [gateway dati locale](http://go.microsoft.com/fwlink/?LinkID=820925).

Si noti che per aggiornare il gateway dati locale è necessario installare di nuovo il gateway, come descritto in questa sezione. Se si installa una versione più recente del gateway, vengono mantenute le impostazioni esistenti. Se si installa la stessa versione, l'operazione viene considerata una reinstallazione completa e le impostazioni non vengono mantenute.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Installare il gateway in modalità personale

> [!NOTE]
> La versione personale del gateway funziona solo con Power BI.

Dopo l'installazione del gateway personale, sarà necessario avviare la **configurazione guidata di Power BI Gateway - Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Sarà quindi necessario accedere a Power BI per registrare il gateway nel servizio cloud.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Sarà anche necessario fornire il nome utente e la password di Windows con cui verrà eseguito il servizio di Windows. È possibile specificare un account Windows diverso dal proprio. Il servizio del gateway verrà eseguito usando questo account.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Al termine dell'installazione, sarà necessario passare ai set di dati in Power BI e assicurarsi che vengano immesse credenziali per le origini dati locali.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Archiviazione di credenziali crittografate nel cloud

Quando si aggiunge un'origine dati al gateway, è necessario fornire le credenziali per l'origine dati. Tutte le query all'origine dati verranno eseguite utilizzando queste credenziali. Le credenziali vengono crittografate in modo sicuro, utilizzando la crittografia asimmetrica, in modo che non possono essere decrittografate nel cloud, prima di essere archiviate nel cloud. Le credenziali vengono inviate al computer che esegue il gateway, in locale dove vengono decrittografate durante l'accesso alle origini dati.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

* [Azure Information Protection](https://docs.microsoft.com/microsoft-365/enterprise/protect-files-with-aip
) non è attualmente supportato
* L'[accesso online](https://products.office.com/en-us/access) non è attualmente supportato

## <a name="tenant-level-administration"></a>Amministrazione a livello di tenant

Attualmente non è disponibile un'unica posizione dalla quale gli amministratori tenant possono gestire tutti i gateway installati e configurati da altri utenti.  Si consiglia agli amministratori tenant di chiedere agli utenti dell'organizzazione di essere aggiunti come amministratore per ogni gateway che installano. In questo modo l'amministratore può gestire tutti i gateway dell'organizzazione tramite la pagina Impostazioni gateway o tramite i [ comandi di PowerShell](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Abilitare le connessioni in uscita di Azure

Il gateway dati locale usa il bus di servizio di Azure per la connettività cloud e di conseguenza stabilisce connessioni in uscita all'area di Azure associata. Per impostazione predefinita, questo è il percorso del tenant di Power BI. Vedere [Dove si trova il tenant di Power BI?](https://powerbi.microsoft.com/en-us/documentation/powerbi-admin-where-is-my-tenant-located/)
Se un firewall blocca le connessioni in uscita, è necessario configurare il firewall per consentire le connessioni in uscita dal gateway dati locale all'area di Azure associata. Per informazioni dettagliate sugli intervalli di indirizzi IP di ogni centro dati Azure, vedere [Microsoft Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653) (Intervalli IP dei data center di Microsoft Azure).
> [!NOTE]
> Gli intervalli di indirizzi IP possono variare nel tempo. Scaricare le informazioni più recenti a intervalli regolari. 

## <a name="troubleshooting"></a>Risoluzione dei problemi

In caso di problemi durante l'installazione e la configurazione di un gateway, vedere [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md). Se si ritiene di avere un problema con il firewall, vedere la sezione [firewall o proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) dell'articolo sulla risoluzione dei problemi.

Se si ritiene che i problemi con il gateway riguardino il proxy, vedere [Configurazione delle impostazioni del proxy per Power BI Gateway](service-gateway-proxy.md).

## <a name="next-steps"></a>Passaggi successivi

[Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Analisi approfondita del gateway dati locale](service-gateway-onprem-indepth.md)  
[On-premises data gateway (personal mode) - the new version of the personal gateway (Gateway dati locale (modalità personale) - Nuova versione del gateway personale)](service-gateway-personal-mode.md)  
[Configurazione delle impostazioni del proxy per il gateway dati locale](service-gateway-proxy.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
