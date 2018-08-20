---
title: URL di Power BI
description: Gli endpoint devono essere raggiungibili per i clienti che usano Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101132"
---
# <a name="power-bi-urls"></a>URL di Power BI

**Il servizio online Power BI**, noto anche come applicazione Software as a Service (SaaS) di Power BI, richiede la connettività a Internet. Gli endpoint seguenti devono essere raggiungibili per i clienti che usano il servizio online Power BI.

Per usare il servizio online Power BI, è necessario avere accesso per connettersi agli endpoint contrassegnati come **obbligatori** nelle tabelle riportate di seguito e a tutti gli endpoint contrassegnati come **obbligatori** nei siti collegati. Se il collegamento a un sito esterno fa riferimento a una sezione specifica, è sufficiente esaminare gli endpoint in tale sezione.

Gli endpoint contrassegnati come **facoltativi** possono anche essere inclusi nell'**elenco elementi consentiti** per funzionalità specifiche.

Il servizio online Power BI richiede solo l'apertura della porta TCP 443 per gli endpoint elencati.

I caratteri jolly (*) rappresentano tutti i livelli sotto il dominio radice e l'indicazione N/D significa che non sono disponibili informazioni. La colonna **Destinazione/i** è un elenco di nomi di dominio completo/domini e collegamenti a siti esterni, che contengono altre informazioni sugli endpoint.

>[!Important]
>Le informazioni nelle tabelle seguenti non riguardano il **cloud U.S. Government**, il **cloud Germania** e il **cloud Cina**.

## <a name="authentication"></a>Autenticazione

Power BI dipende dagli endpoint obbligatori indicati nelle sezioni Autenticazione e identità di Office 365. Per usare Power BI, è necessario essere in grado di connettersi agli endpoint nel sito collegato riportato di seguito.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** autenticazione e identità | Vedere la [sezione Autenticazione e identità di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) dal sito dell'elenco elementi consentiti di Office 365 | N/D |

## <a name="general-site-usage"></a>Utilizzo generale del sito

Per l'uso generale di Power BI, è necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** API back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obbligatorio:** integrazione di Office 365 | Vedere la [sezione Portale e condivisione di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) dal sito dell'elenco elementi consentiti di Office 365 | N/D |
| 3 | **Obbligatorio:** portale | app.powerbi.com | TCP 443 |
| 4 | **Obbligatorio:** dati di telemetria del servizio | dc.services.visualstudio.com | TCP 443 |
| 5 | **Facoltativo:** messaggi informativi | dynmsg.modpim.com | TCP 443 |
| 6 | **Facoltativo:** sondaggi NPS | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Amministrazione

Per eseguire funzioni amministrative all'interno di Power BI, è necessario essere in grado di connettersi agli endpoint nei siti collegati riportati di seguito.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** per la gestione degli utenti e la visualizzazione dei log di controllo | Vedere la [sezione Portale e condivisione di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) dal sito dell'elenco elementi consentiti di Office 365 | N/D |

## <a name="get-data"></a>Recupera dati

Per essere in grado di ottenere dati da origini dati specifiche, ad esempio OneDrive, è necessario essere in grado di connettersi agli endpoint nella tabella seguente.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** AppSource (app interne o esterne in Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Facoltativo:** importare file dall'area OneDrive personale | Vedere il [sito Required URLs and ports for OneDrive](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) (URL e porte necessari per OneDrive) | N/D |
| 3 | **Facoltativo:** video di esercitazione Power BI in 60-Seconds (Power BI in un minuto) | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Facoltativo:** origini dati di streaming PubNub | Vedere la [documentazione PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |

## <a name="dashboard-and-report-integration"></a>Integrazione di report e dashboard 

Power BI dipende da determinati endpoint per supportare dashboard e report. È necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** integrazione di Excel | Vedere la [sezione Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) dal sito dell'elenco elementi consentiti di Office 365 | N/D |

## <a name="custom-visuals"></a>Oggetti visivi personalizzati

Power BI dipende da determinati endpoint per la visualizzazione e l'accesso agli oggetti visivi personalizzati. È necessario essere in grado di connettersi agli endpoint nella tabella e nei siti collegati seguenti.

| Riga | Scopo | Destinazione/i | Porta/e |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obbligatorio:** importare un oggetto visivo personalizzato dall'interfaccia del Marketplace e da un file | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Facoltativo:** Bing Maps | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Facoltativo:** PowerApps | Vedere la [sezione Servizi necessari](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) dal sito dei requisiti di sistema di PowerApps | N/D |
| 4 | **Facoltativo:** Visio | Vedere la [sezione Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) dal sito dell'elenco elementi consentiti di Office 365 | N/D |