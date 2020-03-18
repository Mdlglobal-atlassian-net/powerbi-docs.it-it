---
title: Sospendere e avviare la capacità di Power BI Embedded nel portale di Azure | Microsoft Docs
description: Questo articolo descrive in dettaglio come sospendere e avviare capacità di Power BI Embedded in Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: how-to
ms.date: 09/28/2017
ms.openlocfilehash: 492750e232173480d71bd49b83623d41244bb83b
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79495597"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Sospendere e avviare la capacità di Power BI Embedded nel portale di Azure

Questo articolo descrive in dettaglio come sospendere e avviare capacità di Power BI Embedded in Microsoft Azure. Questa operazione presuppone che sia stata creata capacità di Power BI Embedded. Se non è stata creata alcuna capacità, vedere [Creare capacità di Power BI Embedded nel portale di Azure](azure-pbie-create-capacity.md).

Se non si ha una sottoscrizione di Azure, prima di iniziare creare un [account gratuito](https://azure.microsoft.com/free/).

## <a name="pause-your-capacity"></a>Sospendere la capacità

La sospensione della capacità evita gli addebiti legati all'uso di questa. Questa operazione è molto utile se non è necessario usare la capacità per un certo periodo di tempo. Per sospendere la capacità, eseguire i passaggi seguenti.

> [!NOTE]
> La sospensione di una capacità può impedire la disponibilità di contenuto all'interno di Power BI. Assicurarsi di annullare l'assegnazione delle aree di lavoro della capacità prima della sospensione per evitare interruzioni.

1. Accedere al [portale di Azure](https://portal.azure.com/).

2. Per visualizzare le capacità, selezionare **Tutti i servizi** > **Power BI Embedded**.

    ![Tutti i servizi all'interno del portale di Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selezionare la capacità che si vuole sospendere.

    ![Elenco di capacità di Power BI Embedded all'interno del portale di Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selezionare **Sospendi** all'interno dei dettagli della capacità.

    ![Sospendere la capacità](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Selezionare **Sì** per confermare la sospensione della capacità.

    ![Confermare la sospensione](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Avviare la capacità

Per riprendere l'utilizzo della capacità, avviarla. Con l'avvio della capacità riprende anche la fatturazione.

1. Accedere al [portale di Azure](https://portal.azure.com/).

2. Per visualizzare le capacità, selezionare **Tutti i servizi** > **Power BI Embedded**.

    ![Tutti i servizi all'interno del portale di Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selezionare la capacità da avviare.

    ![Elenco di capacità di Power BI Embedded all'interno del portale di Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selezionare **Avvia** all'interno dei dettagli della capacità.

    ![Avviare la capacità](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Selezionare **Sì** per confermare l'avvio della capacità.

    ![Conferma dell'avvio](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Dopo l'avvio della capacità, eventuale contenuto assegnato a questa è disponibile.

## <a name="next-steps"></a>Passaggi successivi

Se si vuole ridimensionare la capacità verso l'alto o verso il basso, vedere [Ridimensionare la capacità di Power BI Embedded](azure-pbie-scale-capacity.md).

Per iniziare a incorporare contenuto di Power BI all'interno dell'applicazione, vedere [Come incorporare dashboard, report e riquadri di Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)