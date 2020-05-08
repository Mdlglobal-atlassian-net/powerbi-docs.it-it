---
title: Confronto tra Server di report di Power BI e il servizio Power BI
description: Questo articolo mette a confronto le funzionalità di Server di report di Power BI e del servizio Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 03/04/2020
ms.openlocfilehash: 7762ace1da913713567b79a9650b3f07aa71146d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79381055"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Confronto tra Server di report di Power BI e il servizio Power BI

Server di report di Power BI e il servizio Power BI hanno molte caratteristiche in comune e alcune differenze fondamentali, che vengono illustrate nella tabella seguente.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funzionalità di Server di report di Power BI e del servizio Power BI

| Funzionalità | server di report di Power BI | Servizio Power BI | Note |
|---------|---------|---------|---------|
| Distribuzione | Cloud locale o ospitato | Cloud | Server di report di Power BI può essere distribuito nelle macchine virtuali di Azure (cloud ospitato) se concesso in licenza tramite Power BI Premium o SQL Server Enterprise con Software Assurance|
| Dati di origine | Cloud e/o locali | Cloud e/o locali |  |
| Licenza | Power BI Premium o SQL Server EE con Software Assurance (SA) | Power BI Pro e/o Power BI Premium | |  
| Ciclo di vita | Criteri moderni del ciclo di vita | Servizio completamente gestito |  |
| Ciclo di rilascio | Tre volte all'anno (gennaio, maggio, settembre) | Una volta al mese | Le correzioni e le funzionalità più recenti vengono introdotte innanzitutto nel servizio Power BI. In ogni versione di Server di report di Power BI viene eseguito un rollup delle funzionalità da versioni di Power BI Desktop per il servizio. La maggior parte delle altre funzionalità è prevista solo per il servizio Power BI. |
| Creare report di Power BI in Power BI Desktop | Yes | Yes |  |
| Creare report di Power BI nel browser | No | Yes |  |
| Ospitare e connettersi a set di dati condivisi di Power BI | No | Yes | [Introduzione ai set di dati in aree di lavoro diverse](../service-datasets-across-workspaces.md) |
| Gateway richiesto | No | Sì per le origini dati locali |  |
| Streaming in tempo reale | No | Yes | [Streaming in tempo reale in Power BI](../service-real-time-streaming.md) |
| Dashboards | No | Yes | [Dashboard nel servizio Power BI](../consumer/end-user-dashboards.md) |
| Distribuire un gruppo di report tramite app | No | Yes | [Creare e pubblicare app con dashboard e report](../service-create-distribute-apps.md) |
| Pacchetti di contenuto | No | Yes | [Pacchetti di contenuto aziendali: Introduzione](../service-organizational-content-pack-introduction.md) |
| Connettersi a servizi come Salesforce | Yes | Yes | [Connettersi ai servizi usati](../service-connect-to-services.md) con i pacchetti di contenuto nel servizio Power BI. In Server di report di Power BI usare connettori certificati per connettersi ai servizi. Per informazioni dettagliate, vedere [Origini dati dei report di Power BI nel server di report di Power BI](data-sources.md). |
| Domande e risposte | No | Yes | [Domande e risposte nel servizio Power BI e in Power BI Desktop](../power-bi-tutorial-q-and-a.md) 
| Informazioni rapide | No | Yes | [Generare automaticamente informazioni dettagliate sui dati con Power BI](../consumer/end-user-insights.md) |
| Analizza in Excel | No | Yes | [Analizza in Excel](../service-analyze-in-excel.md) 
| Report impaginati | Yes | Yes | [I report impaginati sono disponibili nel servizio Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md) in anteprima in una capacità Premium |
| App Power BI per dispositivi mobili | Yes | Yes | [Panoramica sulle app Power BI per dispositivi mobili](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mappe ArcGIS | No | Yes | [Mappe ArcGIS di Esri nel servizio Power BI e in Power BI Desktop](../visuals/power-bi-visualization-arcgis.md) |
| Sottoscrizioni tramite posta elettronica per i report di Power BI | No | Yes | [Sottoscrivere per se stessi o altri utenti](../service-report-subscribe.md) un report o dashboard nel servizio Power BI |
| Sottoscrizioni tramite posta elettronica per report impaginati | Yes | Yes | [Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI](../consumer/paginated-reports-subscriptions.md)<br><br>[Recapito tramite posta elettronica in Reporting Services](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Avvisi per i dati | No | Yes | [Avvisi per i dati](../service-set-data-alerts.md) nel servizio Power BI
| Sicurezza a livello di riga | Yes | Yes | Disponibile in modalità DirectQuery (origine dati) e importazione <br><br>Sicurezza a livello di riga nel [servizio Power BI](../service-admin-rls.md) <br><br>Sicurezza a livello di riga in [Server di report di Power BI](row-level-security-report-server.md) |
| Modalità schermo intero | No | Yes | [Modalità schermo intero](../consumer/end-user-focus.md) nel servizio Power BI |
| Collaborazione di Office 365 avanzata | No | Yes | [Collaborare in un'area di lavoro](../service-collaborate-power-bi-workspace.md) con Office 365 |
| Oggetti visivi R | No | Yes | [Creare oggetti visivi R](../desktop-r-visuals.md) in Power BI Desktop e pubblicarli nel servizio Power BI. Non è possibile salvare i report di Power BI con oggetti visivi R in Server di report di Power BI.  |
| Funzionalità in anteprima | No | Yes | [Acconsentire esplicitamente alle funzionalità di anteprima del servizio Power BI](../consumer/end-user-preview-features.md) |
| Oggetti visivi di Power BI | Yes | Yes | [Oggetti visivi di Power BI](../developer/visuals/power-bi-custom-visuals.md) |
| Modelli compositi | No | Yes |
| Power BI Desktop | Versione ottimizzata per Server di report, disponibile per il download con Server di report | Versione ottimizzata per il servizio Power BI, disponibile da Windows Store | [Power BI Desktop per il server di report](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop per il servizio Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Passaggi successivi

[Installare il server di report di Power BI](install-report-server.md)
