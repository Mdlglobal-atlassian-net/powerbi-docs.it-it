---
title: Connettersi a Microsoft Azure Consumption Insights con Power BI
description: Microsoft Azure Consumption Insights per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222137"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Connettersi a Microsoft Azure Consumption Insights con Power BI
Esplorare e monitorare i dati relativi ai consumi di Microsoft Azure in Power BI con il pacchetto di contenuto Power BI. I dati vengono aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selezionare **Microsoft Azure Consumption Insights** \> **Scarica adesso**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Specificare il numero dei mesi di dati da importare e il numero di iscrizione di Azure Enterprise. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Specificare la chiave di accesso per la connessione. È possibile trovare la chiave di registrazione nel portale Azure EA. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Il processo di importazione inizia automaticamente. Al termine dell'esercitazione, un nuovo dashboard, report e modello vengono visualizzati nel riquadro di spostamento. Selezionare il dashboard per visualizzare i dati importati.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Mentre il set di dati è pianificata per vengono aggiornati ogni giorno, è possibile modificare la pianificazione dell'aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Microsoft Azure Consumption Insights include dati per l'intervallo di mesi specificato durante la connessione di report mensili. L'intervallo è una finestra mobile, in modo che le date incluse vengono aggiornate quando viene aggiornato il set di dati.

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto richiede l'accesso alle funzionalità Enterprise nel portale di Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Report di Power BI è disponibile per EA Direct, Partner e clienti indiretti che è possibile visualizzare le informazioni di fatturazione. Leggere di seguito per informazioni su come trovare i valori si aspetta che il flusso di connessione.

**Numero di mesi**

* Il numero di mesi (1-36) di dati di oggi che si desidera importare.

**Numero di registrazione**

* Il numero di registrazione di Azure Enterprise, che trova al [Azure Enterprise Portal](https://ea.azure.com/) schermata home in **dettagli della registrazione**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Chiave di accesso**

* È possibile trovare la chiave di accesso nel portale di Azure Enterprise, sotto **Scarica utilizzo** > **chiave di accesso API**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Guida aggiuntiva**

* Per altre informazioni sull'installazione il pacchetto Azure Enterprise Power BI, accedere al portale aziendale di Azure e visualizzare il File della Guida API sotto **aiutare**. È anche possibile trovare istruzioni aggiuntive sotto **Reports** -> **Scarica utilizzo** -> **chiave di accesso API**.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

