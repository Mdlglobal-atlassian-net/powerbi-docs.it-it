---
title: Connettersi a Ricerca di Azure con Power BI
description: Ricerca di Azure per Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d868c50a69381c1ef95a8b3a69590223eb066e90
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-azure-search-with-power-bi"></a>Connettersi a Ricerca di Azure con Power BI
Analisi del traffico di Ricerca di Azure consente di monitorare e comprendere il traffico diretto al servizio di ricerca di Azure. Il pacchetto di contenuto Ricerca di Azure per Power BI fornisce informazioni dettagliate sui dati di ricerca, incluse la ricerca, l'indicizzazione, le statistiche del servizio e la latenza degli ultimi 30 giorni. Altre informazioni sono reperibili nel [post di blog di Azure](https://azure.microsoft.com/en-us/blog/analyzing-your-azure-search-traffic/).

Connettersi al [pacchetto di contenuto Ricerca di Azure](https://app.powerbi.com/getdata/services/azure-search) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selezionare **Ricerca di Azure** \> **Recupera**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Specificare il nome dell'account di archiviazione tabelle in cui è archiviata l'analisi di Ricerca di Azure.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Selezionare **Chiave** come meccanismo di autenticazione e fornire la chiave dell'account di archiviazione. Fare clic su **Accedi** per iniziare il processo di caricamento.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Al termine del caricamento, nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo modello. Selezionare il dashboard per visualizzare i dati importati.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto Ricerca di Azure richiede che nell'account sia abilitato Analisi del traffico di Ricerca di Azure.

## <a name="troubleshooting"></a>Risoluzione dei problemi
Verificare che il nome dell'account di archiviazione e la chiave di accesso completa siano indicati correttamente. Il nome dell'account di archiviazione deve corrispondere all'account configurato con Analisi del traffico di Ricerca di Azure.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

