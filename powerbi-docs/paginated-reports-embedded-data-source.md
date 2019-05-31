---
title: Origini dati incorporate per i report impaginati nel servizio Power BI (anteprima)
description: Questo articolo descrive come creare e modificare un'origine dati incorporata in un report impaginato nel servizio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/16/2019
ms.openlocfilehash: 4dd9ad935a9f7b286aa64d977a78364f2aed0e0f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853392"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service-preview"></a>Creare un'origine dati incorporata per i report impaginati nel servizio Power BI (anteprima)

Questo articolo descrive come creare e modificare un'origine dati incorporata per un report impaginato nel servizio Power BI. È possibile definire un'origine dati incorporata in un unico report e usarla solo in quel report. I report impaginati pubblicati nel servizio Power BI richiedono attualmente set di dati incorporati e origini dati incorporate e possono connettersi alle origini dati seguenti:

- Database SQL di Azure e Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Per queste origini dati, usare il [connessione di SQL Server Analysis Services](service-premium-connect-tools.md) opzione:

- Azure Analysis Services
- Set di dati di Power BI Premium

I report impaginati si connettono alle origini dati locali tramite un gateway, che può essere configurato solo dopo aver pubblicato il report nel servizio Power BI. Altre informazioni sui [gateway di Power BI](service-gateway-getting-started.md). 

## <a name="create-an-embedded-data-source"></a>Creare un'origine dati incorporata
  
1. Aprire Power BI Report Builder.

1. Sulla barra degli strumenti nel riquadro Dati report selezionare **Nuovo** > **Origine dati**. Viene visualizzata la finestra di dialogo **Proprietà origine dati**.

    ![Nuova origine dati](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  Nella casella di testo **Nome** digitare un nome per l'origine dati o accettare quello predefinito.  
  
3.  Selezionare **Usa una connessione incorporata nel report**.  
  
1.  Nell'elenco **Seleziona tipo di connessione** selezionare un tipo di origine dati. 

1.  Specificare una stringa di connessione usando uno dei metodi seguenti:  
  
    -   Digitare la stringa di connessione direttamente nella casella di testo **Stringa di connessione**. 
  
    -   Selezionare il pulsante espressione (**fx)** per creare un'espressione che restituisca una stringa di connessione. Nella finestra di dialogo **Espressione** digitare l'espressione nel riquadro Espressione. Selezionare **OK**. 
  
    -   Selezionare **Compila** per aprire la finestra di dialogo **Proprietà di connessione** relativa all'origine dati scelta nel passaggio 2.  
  
        Compilare i campi della finestra di dialogo **Proprietà di connessione** in base al tipo di origine dati. Le proprietà di connessione includono il tipo di origine dati, il nome dell'origine dati e le credenziali da usare. Dopo aver specificato i valori richiesti in questa finestra di dialogo, selezionare **Test connessione** per verificare che l'origine dati sia disponibile e che le credenziali specificate siano corrette.  
  
4.  Selezionare **Credenziali**.  
  
     Specificare le credenziali da usare per questa origine dati. Il proprietario dell'origine dati sceglie il tipo di credenziali supportate. Per altre informazioni, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
5.  Selezionare **OK**.  
  
     L'origine dati viene visualizzata nel riquadro Dati report.  

## <a name="next-steps"></a>Passaggi successivi

- [Creare un set di dati incorporato per un report impaginato nel servizio Power BI](paginated-reports-create-embedded-dataset.md)
- [Che cosa sono i report impaginati in Power BI Premium? (anteprima)](paginated-reports-report-builder-power-bi.md)
