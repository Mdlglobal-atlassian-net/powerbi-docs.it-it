---
title: Ridimensionare la capacità di Power BI Embedded | Microsoft Docs
description: Questo articolo descrive in dettaglio come ridimensionare capacità di Power BI Embedded in Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: how-to
ms.date: 01/31/2019
ms.openlocfilehash: 18ce2f9b89e78fee3856bf1ceb93805ebc4d27b9
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79495620"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Ridimensionare la capacità di Power BI Embedded nel portale di Azure

Questo articolo descrive in dettaglio come ridimensionare capacità di Power BI Embedded in Microsoft Azure. Il ridimensionamento consente di aumentare o ridurre le dimensioni della capacità.

Questa operazione presuppone che sia stata creata capacità di Power BI Embedded. Se non è stata creata alcuna capacità, vedere [Creare capacità di Power BI Embedded nel portale di Azure](azure-pbie-create-capacity.md).

> [!NOTE]
> Un'operazione di ridimensionamento può richiedere circa un minuto. Durante questo periodo, la capacità non è disponibile e il caricamento di contenuto incorporato potrebbe non riuscire.

## <a name="scale-a-capacity"></a>Ridimensionare una capacità

1. Accedere al [portale di Azure](https://portal.azure.com/).

2. Per visualizzare le capacità, selezionare **Tutti i servizi** > **Power BI Embedded**.

    ![Tutti i servizi all'interno del portale di Azure](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Selezionare la capacità che si vuole ridimensionare.

    ![Elenco di capacità di Power BI Embedded all'interno del portale di Azure](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Selezionare **Piano tariffario** in **Scala** all'interno della capacità.

    ![Opzione Piano tariffario in Scala](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    Il piano tariffario corrente è evidenziato da un bordo azzurro.

    ![Piano tariffario corrente evidenziato da un bordo azzurro](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Per ridimensionare verso l'alto o verso il basso, selezionare il nuovo piano a cui passare. Se si seleziona un nuovo piano, attorno alla selezione viene visualizzato un bordo azzurro tratteggiato. Selezionare **Seleziona** per eseguire il ridimensionamento al nuovo piano.

    ![Selezionare un nuovo piano](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    Il ridimensionamento della capacità potrebbe richiedere uno o due minuti.

6. Verificare il piano tramite la scheda Panoramica. È visualizzato il piano tariffario corrente.

    ![Confermare il piano corrente](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Passaggi successivi

Per sospendere o avviare la capacità, vedere [Sospendere e avviare la capacità di Power BI Embedded nel portale di Azure](azure-pbie-pause-start.md).

Per iniziare a incorporare contenuto di Power BI all'interno dell'applicazione, vedere [Come incorporare dashboard, report e riquadri di Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
