---
title: Filtrare e condividere un report di Power BI
description: Informazioni su come filtrare un report di Power BI e condividerlo con i colleghi all'interno dell'organizzazione.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 636aaf59a3a949b5b3571012d12cecc234e9763b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347954"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtrare e condividere un report di Power BI
La *condivisione* è un approccio valido per consentire ad alcuni utenti di accedere ai dashboard e ai report. Cosa accade se si vuole condividere una versione filtrata di un report? Si può volere, ad esempio, che il report visualizzi solo i dati relativi a una città, a un venditore o a un anno specifico. Questo articolo illustra come filtrare un report e condividere la versione filtrata di questo. Un altro modo per condividere un report filtrato consiste nell'[aggiungere parametri di query all'URL del report](service-url-filters.md). In entrambi i casi, il report viene filtrato quando i destinatari lo aprono per la prima volta. I destinatari possono annullare le selezioni di filtro nel report.

![Report filtrato](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI offre anche [altri modi per collaborare e distribuire i report](service-how-to-collaborate-distribute-dashboards-reports.md). Con la condivisione, l'utente e i destinatari necessitano di una [licenza Power BI Pro](../fundamentals/service-features-license-type.md). In caso contrario, il contenuto deve avere una [capacità Premium](../admin/service-premium-what-is.md). 

## <a name="follow-along-with-sample-data"></a>Dati di esempio per l'apprendimento guidato

Questo articolo usa l'app modello di esempio Sales and Marketing. Si vuole provare? 

1. Installare l'[app modello di esempio Sales and Marketing](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Selezionare l'app e selezionare **Esplora app**.

   ![Esplorare dati di esempio](media/service-share-reports/power-bi-sample-explore-data.png)

3. Selezionare l'icona a forma di matita per aprire l'area di lavoro installata con l'app.

    ![Icona di modifica a forma di matita dell'app](media/service-share-reports/power-bi-edit-pencil-app.png)

4. Nell'elenco dei contenuti dell'area di lavoro selezionare **Report** e quindi selezionare il report **Sales and Marketing Sample PBIX** (PBIX di esempio Sales and Marketing).

    ![Aprire il report di esempio](media/service-share-reports/power-bi-open-sample-report.png)

    A questo punto è possibile iniziare l'apprendimento guidato.

## <a name="set-a-filter-in-the-report"></a>Impostare un filtro nel report

Aprire un report nella [visualizzazione di modifica](../consumer/end-user-reading-view.md) e applicare un filtro.

In questo esempio viene filtrata la pagina YTD Category dell'app modello di esempio Marketing and Sales in modo da visualizzare solo i valori dove **Region** è uguale a **Central**. 
 
![Riquadro Filtro report](media/service-share-reports/power-bi-share-report-filter.png)

Salvare il report.

## <a name="share-the-filtered-report"></a>Condividere il report filtrato

1. Selezionare **Condividi**.

   ![Seleziona Condividi](media/service-share-reports/power-bi-share.png)

2. Deselezionare **Invia notifica tramite posta elettronica ai destinatari** perché sia possibile inviare invece un collegamento filtrato, selezionare **Condividi il report con filtri e filtri dei dati correnti** e quindi selezionare **Condividi**.

    ![Condividere il report con filtri](media/service-share-reports/power-bi-share-with-filters.png)

4. Selezionare di nuovo **Condividi**.

   ![Seleziona Condividi](media/service-share-reports/power-bi-share.png)

5. Selezionare la scheda **Accesso** e quindi **Gestisci visualizzazioni report condivise**.

    ![Gestisci visualizzazioni report condivise](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Fare clic con il pulsante destro del mouse sull'URL voluto e selezionare **Copia collegamento**.

    ![Copiare il collegamento filtrato](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Quando si condividerà il collegamento, i destinatari visualizzeranno il report filtrato. 


## <a name="next-steps"></a>Passaggi successivi
* [Modalità per la condivisione del lavoro in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Share a dashboard (Condividi un dashboard)](service-share-dashboards.md)
* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/).
* Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).
