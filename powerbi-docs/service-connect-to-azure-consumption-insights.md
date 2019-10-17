---
title: Connettersi a Microsoft Azure Consumption Insights con Power BI
description: Microsoft Azure Consumption Insights per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020426"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Connettersi a Microsoft Azure Consumption Insights con Power BI
Esplorare e monitorare i dati relativi ai consumi di Microsoft Azure nel servizio Power BI con il pacchetto di contenuto Power BI. I dati vengono aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto Informazioni dettagliate sul consumo di Microsoft Azure](https://app.powerbi.com/getdata/services/azureconsumption) per il servizio Power BI.

> [!NOTE]
> Per una configurazione più personalizzata, provare a usare il connettore [Informazioni dettagliate sul consumo di Azure](desktop-connect-azure-consumption-insights.md) in Power BI Desktop.

## <a name="how-to-connect"></a>Come connettersi
1. Nel servizio Power BI selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![Recupera dati](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![Ottieni servizi](media/service-connect-to-azure-consumption-insights/services.png)
3. Selezionare **Informazioni dettagliate sul consumo di Microsoft Azure** \> **Scarica adesso**. 
   
   ![Scarica adesso](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Specificare il numero dei mesi di dati da importare e il numero di iscrizione di Azure Enterprise. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
    ![Connetti a Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Specificare la chiave di accesso per la connessione. La chiave di registrazione è disponibile in Microsoft Azure Enterprise Portal. 
   
    ![Informazioni dettagliate sul consumo di Microsoft Azure: chiave](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Il processo di importazione inizia automaticamente. Al termine nel riquadro di spostamento vengono visualizzati un nuovo dashboard, un nuovo report e un nuovo modello. Selezionare il dashboard per visualizzare i dati importati.
   
   ![Dashboard Informazioni dettagliate sul consumo di Microsoft Azure](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Informazioni dettagliate sul consumo di Microsoft Azure include dati di report mensili per l'intervallo di mesi specificato durante la connessione. Poiché l'intervallo è una finestra mobile, le date incluse vengono aggiornate quando viene aggiornato il set di dati.

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto richiede l'accesso alle funzionalità Enterprise nel portale di Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
I report di Power BI sono disponibili per EA Direct, partner e clienti indiretti che possono visualizzare le informazioni di fatturazione. Leggere di seguito per informazioni dettagliate su come trovare i valori previsti dal flusso di connessione.

**Numero di mesi**

* Il numero di mesi (1-36) di dati da oggi che si vuole importare.

**Numero di registrazione**

* Numero di registrazione di Azure Enterprise indicato nella schermata iniziale di [Azure Enterprise Portal](https://ea.azure.com/) in **Dettagli della registrazione**.
  
    ![Numero di registrazione](media/service-connect-to-azure-consumption-insights/params2.png)

**Chiave di accesso**

* La chiave di accesso è disponibile in Azure Enterprise Portal, in **Scarica utilizzo** > **Chiave di accesso API**.
  
    ![Chiave di accesso](media/service-connect-to-azure-consumption-insights/creds2.png)

**Guida aggiuntiva**

* Per altre informazioni sulla configurazione di Azure Enterprise Power BI Pack, accedere ad Azure Enterprise Portal e visualizzare il file della Guida dell'API in **Guida**. Altre istruzioni sono disponibili in **Report** -> **Scarica utilizzo** -> **Chiave di accesso API**.
* Per una configurazione più personalizzata, provare a usare il connettore [Informazioni dettagliate sul consumo di Azure](desktop-connect-azure-consumption-insights.md) in Power BI Desktop.

## <a name="next-steps"></a>Passaggi successivi

[Connettore Informazioni dettagliate sul consumo di Microsoft Azure](desktop-connect-azure-consumption-insights.md) in Power BI Desktop

[Recuperare dati in Power BI](service-get-data.md)

