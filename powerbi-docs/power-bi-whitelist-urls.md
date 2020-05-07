---
title: URL di Power BI per l'elenco elementi consentiti
description: Questo articolo elenca gli endpoint e le porte URL per l'elenco di indirizzi attendibili per connettersi a Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.custom: seodec18
ms.openlocfilehash: 1426cb2926641ca93bcbff3e55ea151f829f290a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82191615"
---
# <a name="power-bi-urls-for-whitelisting"></a>URL di Power BI per l'elenco elementi consentiti
[//]: # "suparnap, miwehnia sono contatti per la manutenzione di questo elenco"

**Il servizio online Power BI**, noto anche come applicazione SaaS (software come servizio) di Power BI, richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che usano il servizio online Power BI.

Per usare il servizio online Power BI, è necessario potersi connettere agli endpoint contrassegnati come **obbligatori** nelle tabelle riportate di seguito e a tutti gli endpoint contrassegnati come **obbligatori** nei siti collegati. Se il collegamento a un sito esterno fa riferimento a una sezione specifica, è sufficiente esaminare gli endpoint in tale sezione.

Gli endpoint contrassegnati come **facoltativi** possono anche essere inclusi nell'**elenco elementi consentiti** per funzionalità specifiche.

Il servizio online Power BI richiede solo l'apertura della porta TCP 443 per gli endpoint elencati.

I caratteri jolly (*) rappresentano tutti i livelli sotto il dominio radice e l'indicazione N/D significa che non sono disponibili informazioni. La colonna **Destinazione/i** è un elenco di nomi di dominio completo/domini e collegamenti a siti esterni, che contengono altre informazioni sugli endpoint.

>[!Important]
>Le informazioni nelle tabelle seguenti non riguardano il **cloud US Government**, il **cloud Germania** o il **cloud Cina**.

## <a name="authentication"></a>Authentication

Power BI dipende dagli endpoint obbligatori indicati nelle sezioni Autenticazione e identità di Office 365. Per usare Power BI, è necessario essere in grado di connettersi agli endpoint nel sito collegato riportato di seguito.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** autenticazione e identità | Vedere la documentazione di Office 365 per [Office Online e URL comuni](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/D |

## <a name="general-site-usage"></a>Utilizzo generale del sito

Per l'uso generale di Power BI, è necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** API back-end | *. analysis.windows.net | TCP 443 |
| 2 | **Obbligatorio:** API back-end | *.pbidedicated.windows.net | TCP 443 |
| 3 | **Obbligatorio:** integrazione di Office 365 | Vedere la documentazione di Office 365 per [Office Online e URL comuni](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| 4 | **Obbligatorio:** portale | app.powerbi.com | TCP 443 |
| 5 | **Obbligatorio:** dati di telemetria del servizio | dc.services.visualstudio.com | TCP 443 |
| 6 | **Facoltativo:** messaggi informativi | dynmsg.modpim.com | TCP 443 |
| 7 | **Facoltativo:** sondaggi NPS | nps.onyx.azure.net | TCP 443 |
| 8 | **Facoltativo:** Rete per la distribuzione di contenuti (CDN) | content.powerapps.com | TCP 443 |
| | | |

## <a name="administration"></a>Amministrazione

Per eseguire funzioni amministrative in Power BI, è necessario potersi connettere agli endpoint nei siti collegati riportati di seguito.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** per la gestione degli utenti e la visualizzazione dei log di controllo | Vedere la documentazione di Office 365 per [Office Online e URL comuni](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="getting-data"></a>Acquisizione dei dati

Per ottenere dati da origini dati specifiche, ad esempio OneDrive, è necessario potersi connettere agli endpoint nella tabella seguente. Potrebbe essere necessario accedere a URL e domini Internet aggiuntivi per origini dati specifiche usate nell'organizzazione.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** AppSource (app interne o esterne in Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Facoltativo:** accedere e ottenere i dati per i pacchetti di contenuto | Dipende dai pacchetti di contenuto usati | Dipende dai pacchetti di contenuto usati |
| 3 | **Facoltativo:** importare file dall'area OneDrive personale | Vedere il [sito Required URLs and ports for OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports) (URL e porte necessari per OneDrive) | N/D |
| 4 | **Facoltativo:** video di esercitazione Power BI in 60-Seconds (Power BI in un minuto) | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Facoltativo:** origini dati di streaming PubNub | Vedere la [documentazione PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |
| | | |

## <a name="dashboard-and-report-integration"></a>Integrazione di report e dashboard

Power BI dipende da determinati endpoint per supportare dashboard e report. È necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** integrazione di Excel | Vedere la documentazione di Office 365 per [Office Online e URL comuni](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="power-bi-visuals"></a>Oggetti visivi di Power BI

Power BI dipende da determinati endpoint per visualizzare e accedere agli oggetti visivi di Power BI. È necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Obbligatorio:** importare un oggetto visivo personalizzato dall'interfaccia del Marketplace o da un file | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Facoltativo:** Bing Mappe | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Facoltativo:** PowerApps | Vedere la [sezione Servizi necessari](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) dal sito dei requisiti di sistema di PowerApps | N/D |
| 4 | **Facoltativo:** Visio | Vedere la documentazione di Office 365 per [Office Online e URL comuni](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), nonché per [SharePoint Online e OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/D |
| | | |

## <a name="related-external-sites"></a>Siti esterni correlati

Power BI si collega ad altri siti correlati. Si tratta di siti relativi a documentazione, supporto, richieste di nuove funzionalità e altro ancora. L'accesso a questi siti non influirà sulla funzionalità di Power BI, quindi l'elenco elementi consentiti è facoltativo.

| Riga | Scopo | Destinazione/i | Porte |
| --- | --- | --- | --- |
| 1 | **Facoltativo:** sito della community | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Facoltativo:** Sito della documentazione | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Facoltativo:** sito di download (per Power BI Desktop e così via) | download.microsoft.com | TCP 443 |
| 4 | **Facoltativo:** reindirizzamenti esterni | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Facoltativo:** sito di commenti e suggerimenti Ideas| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Facoltativo:** sito di Power BI: pagina di destinazione, collegamenti ad altre informazioni, sito del supporto, collegamenti di download, showcase dei partner e altro ancora. | powerbi.microsoft.com | TCP 443 |
| 7 | **Facoltativo:** Power BI Dev Center | dev.powerbi.com | TCP 443 |
| 8 | **Facoltativo:** sito del supporto tecnico | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
