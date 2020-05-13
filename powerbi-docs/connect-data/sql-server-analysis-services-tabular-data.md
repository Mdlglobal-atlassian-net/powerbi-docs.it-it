---
title: Dati dinamici di SQL Server Analysis Services in Power BI
description: Dati dinamici di SQL Server Analysis Services in Power BI. Questi dati possono essere visualizzati attraverso un'origine dati configurata per un gateway aziendale.
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: Minewiskan
ms.author: owend
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: 3bbe3763ecf17fe80d1b3859f18e105e566e14ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83281531"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Dati dinamici di SQL Server Analysis Services in Power BI

In Power BI è possibile connettersi a un server SQL Server Analysis Services dinamico in due modi. In **Recupera dati** è possibile connettersi a un server SQL Server Analysis Services oppure è possibile connettersi a un [file di Power BI Desktop](service-desktop-files.md), o a una [cartella di lavoro di Excel](service-excel-workbook-files.md) che si connette già a un server Analysis Services. Come procedura consigliata, Microsoft consiglia di usare Power BI Desktop grazie alla completezza del set di strumenti e alla possibilità di mantenere una copia di backup del file di Power BI Desktop in locale.

>[!IMPORTANT]
> * Per connettersi a un server Analysis Services dinamico, è necessario che un gateway dati locale sia installato e configurato da un amministratore. Per altre informazioni, vedere [Gateway dati locale](service-gateway-onprem.md).
> * Quando si usa il gateway, i dati rimangono in locale.  I report creati in base a tali dati vengono salvati nel servizio Power BI. 
> * Le [domande e risposte per query in linguaggio naturale](../create-reports/service-q-and-a-direct-query.md) sono disponibili in anteprima per le connessioni dinamiche ad Analysis Services.

## <a name="to-connect-to-a-model-from-get-data"></a>Per connettersi a un modello da Recupera dati

1. Dall'**Area di lavoro personale** selezionare **Recupera dati**. È anche possibile passare a un'area di lavoro di un gruppo, se disponibile.

   ![Connettersi al pulsante Recupera dati](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. Selezionare **Database e altro**.

   ![Connettersi a Recupera dati 1](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. Selezionare **SQL Server Analysis Services** > **Connetti**.

   ![Connettersi a Recupera dati 2](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. Selezionare un server. Se non è elencato alcun server, significa che un gateway e un'origine dati non sono configurati o che l'account non è presente nella scheda **utenti** dell'origine dati, nel gateway. Rivolgersi all'amministratore.

5. Selezionare il modello a cui ci si vuole connettere. Può essere un modello tabulare o multidimensionale.

Dopo aver eseguito la connessione al modello, verrà visualizzato nel sito di Power BI in **Area di lavoro personale/Set di dati**. Se si è passati a un'area di lavoro di gruppo, il set di dati verrà visualizzato all'interno del gruppo.

![Connettersi al set di dati](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Riquadri del dashboard

Se si bloccano elementi visivi di un report sul dashboard, i riquadri bloccati vengono aggiornati automaticamente ogni 10 minuti. Se i dati nel server Analysis Services locale vengono aggiornati, i riquadri verranno aggiornati automaticamente dopo 10 minuti.

## <a name="common-issues"></a>Problemi comuni

* Non è possibile caricare l'errore dello schema del modello - Questo errore si verifica quando l'utente che si connette a SSAS non ha accesso a database SSAS, cubo e modello.

## <a name="next-steps"></a>Passaggi successivi

* [Gateway dati locale](service-gateway-onprem.md)  
* [Gestire origini dati di Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)