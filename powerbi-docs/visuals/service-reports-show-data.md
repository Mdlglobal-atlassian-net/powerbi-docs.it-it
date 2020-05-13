---
title: Visualizzare i dati usati per creare la visualizzazione di Power BI
description: Questo documento spiega come visualizzare i dati usati per creare un oggetto visivo in Power BI e come esportarli in un file in formato CSV.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b2c587be792e0ad6318dd066cb239949b30cc9e5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276560"
---
# <a name="display-a-visualizations-underlying-data"></a>Visualizzare i dati sottostanti di un oggetto visivo

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-nyyn.md)]    

## <a name="show-data"></a>Mostra i dati
Una visualizzazione di Power BI viene costruita sulla base dei dati dei set di dati dell'utente. Se si è interessati a visualizzare il "dietro le quinte", Power BI consente di *visualizzare* i dati usati per creare l'oggetto visivo. Quando si seleziona **Mostra i dati**, Power BI mostra i dati di sotto o accanto alla visualizzazione.

È anche possibile esportare i dati usati per creare la visualizzazione in un file con estensione xlsx o csv e visualizzarlo in Excel. Per altre informazioni, vedere [Esportare dati da visualizzazioni di Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> Le opzioni *Mostra i dati* ed *Esporta dati* sono disponibili nel servizio Power BI e in Power BI Desktop. Tuttavia, Power BI Desktop offre un livello di dettaglio aggiuntivo: [*Visualizza record* mostra le righe del set di dati effettive](../create-reports/desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Uso di *Mostra i dati* 
1. In Power BI Desktop selezionare una visualizzazione per attivarla.

2. Selezionare **Altre azioni** (...) e scegliere **Mostra i dati**. 
    ![Opzione di visualizzazione per Mostra i dati](media/service-reports-show-data/power-bi-more-action.png)


3. Per impostazione predefinita, i dati vengono visualizzati sotto l'oggetto visivo.
   
   ![Visualizzazione verticale dell'oggetto visivo e dei dati](media/service-reports-show-data/power-bi-show-data-below.png)

4. Per modificare l'orientamento, selezionare il layout verticale ![piccolo screenshot dell'icona usata per passare al layout verticale](media/service-reports-show-data/power-bi-vertical-icon-new.png) nell'angolo in alto a destra della visualizzazione.
   
   ![Visualizzazione orizzontale dell'oggetto visivo e dei dati](media/service-reports-show-data/power-bi-show-data-side.png)
5. Per esportare i dati in un file CSV, selezionare i puntini di sospensione e scegliere **Esporta dati**.
   
    ![Selezionare Esporta dati](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Per altre informazioni sull'esportazione dei dati in Excel, vedere [Esportare dati da visualizzazioni di Power BI](power-bi-visualization-export-data.md).
6. Per nascondere i dati, deselezionare **Esplora** > **Mostra i dati**.

## <a name="using-show-records"></a>Uso di Visualizza record
È anche possibile concentrarsi su un solo record di dati in una visualizzazione e analizzare i dati sottostanti. 

1. Per usare **Visualizza record** selezionare una visualizzazione per attivarla. 

2. Sulla barra multifunzione desktop selezionare la scheda **Strumenti visivi** > **Dati/Drill** > **Visualizza record**. 

    ![Screenshot con l'opzione Visualizza record selezionata.](media/service-reports-show-data/power-bi-see-record.png)

3. Selezionare un punto dati o una riga nella visualizzazione. In questo esempio è stata selezionata la quarta colonna da sinistra. Power BI mostra il record del set di dati per questo punto dati.

    ![Screenshot del singolo record del set di dati.](media/service-reports-show-data/power-bi-row.png)

4. Selezionare **Torna al report** per tornare nell'area di disegno report desktop. 

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

- Se il pulsante **Visualizza record** nella barra multifunzione è disabilitato e inattivo, significa che la visualizzazione selezionata non supporta questa opzione.
- Non è possibile cambiare i dati in Visualizza record e salvarli nel report.
- Non è possibile usare Visualizza record quando l'oggetto visivo usa una misura calcolata.
- Non è possibile usare Visualizza record quando si è connessi a un modello multidimensionale dinamico.  

## <a name="next-steps"></a>Passaggi successivi
[Esportare dati da visualizzazioni di Power BI](power-bi-visualization-export-data.md)    

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)


