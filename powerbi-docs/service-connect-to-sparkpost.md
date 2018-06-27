---
title: Connettersi a SparkPost con Power BI
description: SparkPost per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6f914a031c70c68703116083f42885e2fe79cf30
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34247896"
---
# <a name="connect-to-sparkpost-with-power-bi"></a>Connettersi a SparkPost con Power BI
Il pacchetto di contenuto di Power BI per SparkPost consente di estrarre tutti i set di dati importanti dall'account di SparkPost in un unico dashboard dettagliato. L'uso del pacchetto di contenuto SparkPost consente di visualizzare le statistiche di posta elettronica complessive, inclusi domini, campagne e impegno da parte del provider di servizi Internet.

Connettersi al [pacchetto di contenuto SparkPost per Power BI](https://app.powerbi.com/getdata/services/spark-post).

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-sparkpost/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-sparkpost/services.png)
3. Selezionare il pacchetto di contenuto **SparkPost** e fare clic su **Recupera**. 
   
   ![](media/service-connect-to-sparkpost/sparkpost.png)
4. Quando richiesto, specificare la chiave API SparkPost e selezionare Accedi. Per informazioni dettagliate su [come trovare questo parametro](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-sparkpost/creds.png)
5. Verrà avviato il caricamento dei dati, che a seconda delle dimensioni dell'account l'operazione potrebbe richiedere alcuni minuti. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il dashboard, il report e il set di dati predefiniti, popolati con le statistiche relative ai messaggi di posta elettronica degli ultimi 90 giorni. I nuovi elementi sono contrassegnati con un asterisco giallo \*.
   
   ![](media/service-connect-to-sparkpost/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto SparkPost per Power BI include informazioni come il numero di clic univoci e le percentuali di elementi accettati, non recapitati, ritardati, rifiutati e così via.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Il pacchetto di contenuto usa una chiave API per connettere l'account di SparkPost a Power BI. La chiave API è disponibile nell'account in Account \> API & SMTP (vedere [qui](https://support.sparkpost.com/customer/portal/articles/1933377-create-api-keys) per altre informazioni). È consigliabile usare una chiave API con le autorizzazioni per `Message Events: Read-only ` e `Metrics: Read-only`

![](media/service-connect-to-sparkpost/sparkpost1.png)

