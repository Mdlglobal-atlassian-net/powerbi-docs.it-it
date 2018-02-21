---
title: Connettersi a Microsoft Azure Consumption Insights con Power BI
description: Microsoft Azure Consumption Insights per Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggies
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
ms.openlocfilehash: e2844283e82943c38a4c8262fee97817ebf68973
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Connettersi a Microsoft Azure Consumption Insights con Power BI
Esplorare e monitorare i dati relativi ai consumi di Microsoft Azure in Power BI con il pacchetto di contenuto Power BI. I dati verranno aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selezionare **Microsoft Azure Consumption Insights** \> **Recupera**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Specificare il numero dei mesi di dati da importare e il numero di iscrizione di Azure Enterprise. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Specificare la chiave di accesso per la connessione. La chiave per l'iscrizione è reperibile nel portale Azure EA. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Microsoft Azure Consumption Insights include dati di report mensili per l'intervallo di mesi specificato durante il flusso di connessione. L'intervallo è una finestra mobile, quindi le date incluse vengono aggiornate quando viene aggiornato il set di dati.

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto richiede l'accesso alle funzionalità aziendali nel portale di Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
I report di Power Bi sono disponibili per EA Direct, partner e clienti indiretti che riescono a visualizzare le informazioni di fatturazione. Leggere di seguito per informazioni dettagliate su come trovare i valori previsti dal flusso di connessione.

**Numero di mesi**

* Deve essere un numero compreso tra 1 e 36 che rappresenta il numero di mesi di dati (dalla data odierna) che si vuole importare.

**Numero di registrazione**

* Si tratta del numero di registrazione di Azure Enterprise indicato nella schermata iniziale di [Azure Enterprise Portal](https://ea.azure.com/) in "Dettagli della registrazione".
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Chiave di accesso**

* La chiave è reperibile nel portale di Azure Enterprise, in "Scarica utilizzo" > "Chiave di accesso API"
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Guida aggiuntiva**

* Per informazioni aggiuntive sulla configurazione del pacchetto Azure Enterprise per Power BI, accedere ad Azure Enterprise Portal per visualizzare il file della Guida dell'API disponibile in "Guida". Altre informazioni sono disponibili in Report -> Scarica utilizzo -> Chiave di accesso API. 

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

