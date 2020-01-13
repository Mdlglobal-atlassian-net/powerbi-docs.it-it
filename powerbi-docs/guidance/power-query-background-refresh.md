---
title: Disabilitare l'aggiornamento in background di Power Query
description: Linee guida per la disabilitazione dell'aggiornamento in background di Power Query.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623062"
---
# <a name="disable-power-query-background-refresh"></a>Disabilitare l'aggiornamento in background di Power Query

Questo articolo è destinato all'importazione dei modellatori di dati usati in Power BI Desktop.

Per impostazione predefinita, quando Power Query importa i dati, memorizza anche nella cache fino a 1000 righe di dati di anteprima per ogni query. I dati di anteprima consentono di disporre di una rapida anteprima dei dati di origine e dei risultati della trasformazione per ogni passaggio delle query. Vengono archiviati separatamente su disco e non nel file di Power BI Desktop.

Tuttavia, quando il file di Power BI Desktop contiene molte query, il recupero e l'archiviazione dei dati di anteprima possono prolungare il tempo necessario per completare un aggiornamento.

## <a name="recommendation"></a>Raccomandazione

È possibile ottenere un aggiornamento più rapido impostando il file di Power BI Desktop per aggiornare la cache di anteprima _in background_. In Power BI Desktop è possibile abilitare questa operazione selezionando _File > Opzioni e impostazioni > Opzioni_ e quindi selezionando la pagina _Caricamento dati_. È quindi possibile attivare l'opzione **Consenti il download dell'anteprima dati in background**. Si noti che questa opzione può essere impostata solo per il file corrente.

![Opzioni dei dati in background di Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

L'abilitazione dell'aggiornamento in background può far sì che i dati di anteprima risultino non aggiornati. Se ciò accade, l'editor di Power Query invierà una notifica con l'avviso seguente:

![Avviso dell'editor di Power Query relativo a dati di anteprima obsoleti](media/power-query-background-refresh/power-query-preview-data-old.png)

È sempre possibile aggiornare la cache di anteprima. È possibile aggiornarla per una singola query o per tutte le query usando il comando **Aggiorna anteprima**, disponibile sulla barra multifunzione **Home** della finestra dell'editor di Power Query.

![Comandi dell'editor di Power Query per l'aggiornamento dei dati di anteprima](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Documentazione di Power Query](/power-query/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
