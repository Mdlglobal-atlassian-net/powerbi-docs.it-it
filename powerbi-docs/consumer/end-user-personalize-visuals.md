---
title: Personalizzare oggetti visivi in un report
description: Creare una propria visualizzazione di un report senza modificarlo.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 83f040fd021a3d3e1cd6ce344c84051c7ff58bb0
ms.sourcegitcommit: faa8cfb66e79ea16ba46605f752cc9ca57924d0e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83383158"
---
# <a name="personalize-visuals-in-a-report"></a>Personalizzare oggetti visivi in un report

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

È difficile creare un unico oggetto visivo in grado di soddisfare i requisiti di tutti. Quando tuttavia un report viene condiviso da un collega, potrebbe essere necessario modificare gli oggetti visivi senza dover chiedere al collega di apportare le modifiche. 

È possibile che si vogliano sostituire le informazioni sull'asse, modificare il tipo di oggetto visivo o aggiungere informazioni alla descrizione comando. Con la funzionalità **Personalizza questo oggetto visivo**, apportare le modifiche in autonomia e, dopo aver ottenuto l'oggetto visivo desiderato, salvarlo come segnalibro a cui poter tornare in seguito. Non è neppure necessaria l'autorizzazione di modifica per il report.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="Personalizzare un oggetto visivo":::
 
## <a name="what-you-can-change"></a>Modifiche possibili

Questa funzionalità consente di ottenere altre informazioni approfondite tramite l'esplorazione ad hoc degli oggetti visivi in un report di Power BI. Di seguito sono elencate alcune modifiche che è possibile apportare. Le opzioni disponibili variano in base al tipo di oggetto visivo. 

- Modificare il tipo di visualizzazione
- Sostituire una misura o una dimensione
- Aggiungere o rimuovere una legenda
- Confrontare due o più misure
- Modificare le aggregazioni e così via.

Questa funzionalità non solo offre nuove opportunità di esplorazione, ma consente anche di acquisire e condividere le modifiche in vari modi:

- Acquisire le modifiche
- Condividere le modifiche
- Reimpostare tutte le modifiche di un report
- Reimpostare tutte le modifiche di un oggetto visivo
- Cancellare le modifiche recenti


## <a name="personalize-visuals-in-the-power-bi-service"></a>Personalizzare gli oggetti visivi nel servizio Power BI

Grazie alla personalizzazione di un oggetto visivo, è possibile esplorare i dati in molti modi senza uscire dalla visualizzazione di lettura del report. Gli esempi seguenti illustrano i diversi modi in cui è possibile modificare una visualizzazione per soddisfare le proprie esigenze. 

1. Aprire un report nella visualizzazione di lettura nel servizio Power BI.

2. Nella barra dei menu dell'oggetto visivo selezionare l'icona **Personalizza questo oggetto visivo** Icona ![Personalizza questo oggetto visivo](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png). 

3. Per cancellare i campi **Personalizza**, selezionare **Altre opzioni (...)** e scegliere **Rimuovi campo**.

### <a name="change-the-visualization-type"></a>Modificare il tipo di visualizzazione

Si ritiene che i dati vengano visualizzati meglio come istogramma a colonne in pila? Modificare il **tipo di visualizzazione**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Modificare il tipo di visualizzazione":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Sostituire una misura o una dimensione
Sostituire il campo usato per l'asse X selezionando il campo che si vuole sostituire e selezionare un campo diverso.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Modificare l'asse":::
 
### <a name="add-or-remove-a-legend"></a>Aggiungere o rimuovere una legenda
L'aggiunta di una legenda consente di applicare una codifica a colori a un oggetto visivo in base a una categoria. In questo esempio viene usata la codifica a colori in base al nome della società. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Aggiungere o rimuovere la legenda":::

### <a name="compare-two-or-more-different-measures"></a>Confrontare due o più misure diverse
Confrontare e contrapporre i valori per diverse misure usando l'icona + per aggiungere più misure per un oggetto visivo. Per rimuovere una misura, selezionare **Altre opzioni (...)** e scegliere **Rimuovi campo**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Confrontare misure":::

### <a name="change-aggregations"></a>Modificare le aggregazioni
Cambiare il modo in cui una misura viene calcolata modificando l'aggregazione nel riquadro **Personalizza**. Selezionare **Altre opzioni (...)** e scegliere l'aggregazione da usare.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Modificare le aggregazioni":::

### <a name="capture-changes"></a>Acquisire le modifiche 
Con i segnalibri personali è possibile acquisire le modifiche in modo da tornare alla visualizzazione personalizzata. Selezionare **Segnalibri** > **Segnalibri personali** e assegnare un nome al segnalibro. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Creare un segnalibro":::
 
È anche possibile impostare il segnalibro come visualizzazione predefinita.

### <a name="share-changes"></a>Condividere le modifiche 
Se sono disponibili le autorizzazioni di lettura e ricondivisione, quando si condivide il report è possibile scegliere di includere le modifiche.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Condividire le modifiche":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Reimpostare tutte le modifiche apportate a un report

Nell'angolo in alto a destra dell'area di disegno del report selezionare **Ripristina impostazioni predefinite**. Questa operazione consente di rimuovere tutte le modifiche apportate al report e impostarle nuovamente sull'ultima visualizzazione salvata dell'autore del report.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Reimpostare tutte le modifiche":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Reimpostare tutte le modifiche apportate a un oggetto visivo

Nella barra dei menu dell'oggetto visivo selezionare **Reimposta questo oggetto visivo** per rimuovere tutte le modifiche apportate a un oggetto visivo specifico e impostarlo di nuovo sull'ultima visualizzazione salvata dell'autore di tale oggetto visivo.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Reimpostare tutte le modifiche di un oggetto visivo":::
 
### <a name="clear-recent-changes"></a>Cancellare le modifiche recenti

Selezionare l'icona a forma di gomma per cancellare tutte le modifiche recenti apportate dall'apertura del riquadro **Personalizza**.  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Cancellare le modifiche recenti":::

## <a name="limitations-and-known-issues"></a>Limitazioni e problemi noti

Attualmente la funzionalità presenta alcune limitazioni di cui tenere conto.

- È possibile disattivare **Personalizza questo oggetto visivo** per un intero report o per un determinato oggetto visivo. Se non è presente un'opzione per personalizzare un oggetto visivo, rivolgersi all'amministratore tenant o al proprietario del report. Per visualizzare le informazioni di contatto del proprietario del report, selezionare il nome del report nella barra dei menu di Power BI.
- Le esplorazioni dell'utente non vengono mantenute automaticamente. È necessario salvare la visualizzazione come segnalibro personale per acquisire le modifiche.
- Non è possibile modificare gli oggetti visivi nelle app Power BI per dispositivi mobili. Tuttavia, qualsiasi modifica di un oggetto visivo salvata in un segnalibro personale nel servizio Power BI viene rispettata nelle app per dispositivi mobili.

Sono presenti anche alcuni problemi in corso di risoluzione:

- L'aggiunta di una gerarchia non è supportata. È necessario aggiungere i singoli elementi figlio.
- Con i segnalibri personali si potrebbero ottenere risultati leggermente diversi in base alla sequenza selezionata. Le discrepanze sono possibili perché l'acquisizione non include lo stato completo del report, ma solo le modifiche apportate. La soluzione alternativa consiste nel selezionare **Ripristina impostazioni predefinite** e quindi selezionare il segnalibro che si vuole visualizzare. 

## <a name="next-steps"></a>Passaggi successivi
[Copiare un oggetto visivo del report come immagine statica](../visuals/power-bi-visualization-copy-paste.md)    
Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

