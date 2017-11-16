---
title: Dati dinamici di SQL Server Analysis Services in Power BI
description: Dati dinamici di SQL Server Analysis Services in Power BI. Questi dati possono essere visualizzati attraverso un'origine dati configurata per un gateway aziendale.
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 207a779b38aade4c888a2dced503e25d3e7928f9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Dati dinamici di SQL Server Analysis Services in Power BI
In Power BI è possibile connettersi a un server SQL Server Analysis Services dinamico in due modi. In **Recupera dati** è possibile connettersi a un server SQL Server Analysis Services oppure è possibile connettersi a un [file di Power BI Desktop](service-desktop-files.md), o a una [cartella di lavoro di Excel](service-excel-workbook-files.md) che si connette già a un server Analysis Services.

 >[!IMPORTANT]
 >* Per connettersi a un server Analysis Services dinamico, è necessario che un gateway dati locale sia installato e configurato da un amministratore. Per altre informazioni, vedere [Gateway dati locale](service-gateway-onprem.md).
 >* Quando si usa il gateway, i dati rimangono in locale.  I report creati in base a tali dati vengono salvati nel servizio Power BI. 
 >* Le [domande e risposte per query in linguaggio naturale](service-q-and-a-direct-query.md) sono disponibili in anteprima per le connessioni dinamiche ad Analysis Services.

## <a name="to-connect-to-a-model-from-get-data"></a>Per connettersi a un modello da Recupera dati
1. Dall'**Area di lavoro personale** selezionare **Recupera dati**. È anche possibile passare a un'area di lavoro di un gruppo, se disponibile.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)
2. Selezionare **Database e altro**.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)
3. Selezionare **SQL Server Analysis Services** > **Connetti**. 
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)
4. Selezionare un server. Se non è elencato alcun server, significa che un gateway e un'origine dati non sono configurati o che l'account non è presente nella scheda **utenti** dell'origine dati, nel gateway. Rivolgersi all'amministratore.
5. Selezionare il modello a cui ci si vuole connettere. Può essere un modello tabulare o multidimensionale.

Dopo aver eseguito la connessione al modello, verrà visualizzato nel sito di Power BI in **Area di lavoro personale/Set di dati**. Se si è passati a un'area di lavoro del gruppo, il set di dati verrà visualizzato all'interno del gruppo.

![](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Riquadri del dashboard
Se si bloccano elementi visivi di un report sul dashboard, i riquadri bloccati vengono aggiornati automaticamente ogni 10 minuti. Se i dati nel server Analysis Services locale vengono aggiornati, i riquadri verranno aggiornati automaticamente dopo 10 minuti.

## <a name="next-steps"></a>Passaggi successivi
[Gateway dati locale](service-gateway-onprem.md)  
[Gestire origini dati di Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

