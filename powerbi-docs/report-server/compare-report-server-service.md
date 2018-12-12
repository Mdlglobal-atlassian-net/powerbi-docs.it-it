---
title: Confronto tra Server di report di Power BI e il servizio Power BI
description: Questo articolo mette a confronto le funzionalità di Server di report di Power BI e del servizio Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 11/16/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: aca89b1e45c2ce236a4b5a960436077e089a5b01
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900567"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Confronto tra Server di report di Power BI e il servizio Power BI

Server di report di Power BI e il servizio Power BI hanno molte caratteristiche in comune e alcune differenze fondamentali, che vengono illustrate nella tabella seguente.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funzionalità di Server di report di Power BI e del servizio Power BI

| Funzionalità | server di report di Power BI | Servizio Power BI | Note
|---------|---------|---------|---------|
| Distribuzione | Cloud locale o ospitato | Cloud | Server di report di Power BI può essere distribuito nelle macchine virtuali di Azure (cloud ospitato) se concesso in licenza tramite Power BI Premium
| Dati di origine | Cloud e/o locali | Cloud e/o locali |  
| Licenza | Power BI Premium o SQL Server EE con SA | Power BI Pro e/o Power BI Premium |  
| Ciclo di vita | Criteri moderni del ciclo di vita | Servizio completamente gestito |  
| Ciclo di rilascio | Una volta ogni 4 mesi | Una volta al mese | Le correzioni e le funzionalità più recenti vengono introdotte innanzitutto nel servizio Power BI. La maggior parte delle funzionalità di base è disponibile in Server di report di Power BI nelle versioni immediatamente successive; alcune funzionalità sono pensate solo per il servizio Power BI.
| Creare report di Power BI in Power BI Desktop | Sì | Sì |  
| Creare report di Power BI nel browser | No | Sì |  
| Gateway richiesto | No | Sì per le origini dati locali |  
| Streaming in tempo reale | No | Sì | [Streaming in tempo reale in Power BI](../service-real-time-streaming.md)
| Dashboard | No | Sì | [Dashboard nel servizio Power BI](../consumer/end-user-dashboards.md) 
| Distribuire un gruppo di report tramite app | No | Sì | [Creare e pubblicare app con dashboard e report](../service-create-distribute-apps.md) 
| Pacchetti di contenuto | No | Sì | [Pacchetti di contenuto aziendali: Introduzione](../service-organizational-content-pack-introduction.md) 
| Connettersi a servizi come Salesforce | Sì | Sì | [Connettersi ai servizi usati](../service-connect-to-services.md) con i pacchetti di contenuto nel servizio Power BI. In Server di report di Power BI usare connettori certificati per connettersi ai servizi. Per informazioni dettagliate, vedere [Origini dati dei report di Power BI nel server di report di Power BI](data-sources.md).
| Domande e risposte | No | Sì | [Domande e risposte nel servizio Power BI e in Power BI Desktop](../consumer/end-user-q-and-a.md) 
| Informazioni rapide | No | Sì | [Generare automaticamente informazioni dettagliate sui dati con Power BI](../consumer/end-user-insights.md) 
| Analizza in Excel | No | Sì | [Analizza in Excel](../service-analyze-in-excel.md) 
| Report impaginati | Sì | Sì | [I report impaginati sono disponibili nel servizio Power BI](../paginated-reports-report-builder-power-bi.md) in anteprima in una capacità Premium
| App Power BI per dispositivi mobili | Sì | Sì | [Panoramica sulle app Power BI per dispositivi mobili](../consumer/mobile/mobile-apps-for-mobile-devices.md) 
| Mappe ArcGIS | No | Sì | [Mappe ArcGIS di Esri nel servizio Power BI e in Power BI Desktop](../power-bi-visualization-arcgis.md)
| Sottoscrizioni tramite posta elettronica per i report di Power BI | No | Sì | [Sottoscrivere un report o un dashboard](../consumer/end-user-subscribe.md) nel servizio Power BI 
| Sottoscrizioni tramite posta elettronica per report impaginati | Sì | No | [Recapito tramite posta elettronica in Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Avvisi per i dati | No | Sì | [Avvisi per i dati](../service-set-data-alerts.md) nel servizio Power BI
| Sicurezza a livello di riga | Solo tramite origine dati in modalità DirectQuery | Disponibile in modalità DirectQuery (origine dati) e importazione | [Sicurezza a livello di riga](../service-admin-rls.md) con Power BI 
| Modalità schermo intero | No | Sì | [Modalità schermo intero](../consumer/end-user-focus.md) nel servizio Power BI 
| Collaborazione di Office 365 avanzata | No | Sì | [Collaborare in un'area di lavoro per le app](../service-collaborate-power-bi-workspace.md) con Office 365 
| Oggetti visivi R | No | Sì | [Creare oggetti visivi R](../desktop-r-visuals.md) in Power BI Desktop e pubblicarli nel servizio Power BI. Non è possibile salvare i report di Power BI con oggetti visivi R in Server di report di Power BI.  
| Funzionalità di anteprima | No | Sì | [Acconsentire esplicitamente alle funzionalità di anteprima del servizio Power BI](../consumer/end-user-preview-features.md) 
| Oggetti visivi personalizzati | Sì | Sì | [Oggetti visivi personalizzati in Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Versione ottimizzata per Server di report, disponibile per il download con Server di report | Versione ottimizzata per il servizio Power BI, disponibile da Windows Store | [Power BI Desktop per il server di report](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop per il servizio Power BI](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Passaggi successivi
[Installare il server di report di Power BI](install-report-server.md)  



