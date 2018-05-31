---
title: Confronto tra Server di report di Power BI e il servizio Power BI
description: Questo articolo mette a confronto le funzionalità di Server di report di Power BI e del servizio Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: c47722fda28fc45289858f082a0838f583b53dbb
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34296783"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Confronto tra Server di report di Power BI e il servizio Power BI

Server di report di Power BI e il servizio Power BI hanno molte caratteristiche in comune e alcune differenze fondamentali, che vengono illustrate nella tabella seguente.

| Funzionalità | Server di report Power BI | Servizio Power BI | Note
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
| Dashboard | No | Sì | [Dashboard nel servizio Power BI](../service-dashboards.md) 
| Distribuire un gruppo di report tramite app | No | Sì | [Creare e pubblicare app con dashboard e report](../service-create-distribute-apps.md) 
| Pacchetti di contenuto | No | Sì | [Pacchetti di contenuto aziendali: Introduzione](../service-organizational-content-pack-introduction.md) 
| Connettersi a servizi come Salesforce | No | Sì | [Connettersi ai servizi usati](../service-connect-to-services.md) con il servizio Power BI
| Domande e risposte | No | Sì | [Domande e risposte nel servizio Power BI e in Power BI Desktop](../power-bi-q-and-a.md) 
| Informazioni rapide | No | Sì | [Generare automaticamente informazioni dettagliate sui dati con Power BI](../service-insights.md) 
| Analizza in Excel | No | Sì | [Analizza in Excel](../service-analyze-in-excel.md) 
| Report impaginati | Sì | No | I report impaginati non sono disponibili nel servizio Power BI, ma è possibile [aggiungere elementi dei report impaginati ai dashboard di Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| App Power BI per dispositivi mobili | Sì | Sì | [Panoramica sulle app Power BI per dispositivi mobili](../mobile-apps-for-mobile-devices.md) 
| Mappe ArcGIS | No | Sì | [Mappe ArcGIS di Esri nel servizio Power BI e in Power BI Desktop](../power-bi-visualization-arcgis.md)
| Sottoscrizioni tramite posta elettronica per i report di Power BI | No | Sì | [Sottoscrivere un report o un dashboard](../service-report-subscribe.md) nel servizio Power BI 
| Sottoscrizioni tramite posta elettronica per report impaginati | Sì | No | [Recapito tramite posta elettronica in Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Avvisi per i dati | No | Sì | [Avvisi per i dati](../service-set-data-alerts.md) nel servizio Power BI
| Sicurezza a livello di riga | Solo tramite origine dati in modalità DirectQuery | Disponibile in modalità DirectQuery (origine dati) e importazione | [Sicurezza a livello di riga](../service-admin-rls.md) con Power BI 
| Modalità schermo intero | No | Sì | [Modalità schermo intero](../service-fullscreen-mode.md) nel servizio Power BI 
| Collaborazione di Office 365 avanzata | No | Sì | [Collaborare in un'area di lavoro per le app](../service-collaborate-power-bi-workspace.md) con Office 365 
| Oggetti visivi R | No | Sì | [Creare oggetti visivi R](../service-r-visuals.md) nel servizio Power BI  
| Funzionalità in anteprima | No | Sì | [Acconsentire esplicitamente alle funzionalità di anteprima del servizio Power BI](../service-preview-features.md) 
| Oggetti visivi personalizzati | Sì | Sì | [Oggetti visivi personalizzati in Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Versione ottimizzata per Server di report, disponibile per il download con Server di report | Versione ottimizzata per il servizio Power BI, disponibile da Windows Store | [Power BI Desktop per il server di report](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop per il servizio Power BI](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Passaggi successivi
[Installare il server di report di Power BI](install-report-server.md)  



