---
title: Configurare il drill-through nei report di Power BI
description: Informazioni su come usare il drill-through per eseguire il drill-down nei dati, nella pagina di un nuovo report, nei report di Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 9f017a4e93e76d91949b3cc3e12ef0c652664a91
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83281439"
---
# <a name="set-up-drill-through-in-power-bi-reports"></a>Configurare il drill-through nei report di Power BI
Con il *drill-through* nei report di Power BI è possibile creare una pagina nel report incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Quando i lettori del report usano la funzione di drill-through, possono fare clic con il pulsante destro del mouse su un punto dati in altre pagine del report ed eseguire il drill-through nella pagina specifica per ottenere dettagli che vengono filtrati in base al contesto selezionato. È anche possibile [creare un pulsante che consente di eseguire il drill-through](desktop-drill-through-buttons.md) per visualizzare i dettagli quando si fa clic su di esso.

Il drill-through può essere configurato nei report in Power BI Desktop o nel servizio Power BI.

![Uso del drill-through](media/desktop-drillthrough/power-bi-drill-through-right-click.png)

## <a name="set-up-the-drill-through-destination-page"></a>Configurare la pagina di destinazione del drill-through
1. Per usare il drill-through, creare una pagina di report con gli oggetti visivi voluti per il tipo di entità per la quale si fornirà il drill-through. 

    Si supponga, ad esempio, di voler fornire il drill-through per i produttori. In questo caso è possibile creare una pagina di drill-through con oggetti visivi che visualizzano le vendite totali, le unità spedite totali, le vendite per categoria, le vendite per area e così via. In questo modo, quando si esegue il drill-through a tale pagina, gli oggetti visivi saranno specifici per il produttore selezionato.

2. Nella pagina di drill-through, nella sezione **Campi** del riquadro **Visualizzazioni**, trascinare quindi il campo per cui si vuole abilitare il drill-through nell'area **Filtri di drill-through**.

    ![Area drill-through](media/desktop-drillthrough/drillthrough_02.png)

    Quando si aggiunge un campo all'area **Filtri di drill-through**, Power BI crea automaticamente un oggetto visivo pulsante *Indietro*. Tale oggetto visivo diventa un pulsante nei report pubblicati. Gli utenti che utilizzano il report nel servizio Power BI usano questo pulsante per tornare alla pagina del report da cui sono arrivati.

    ![Immagine drill-through](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> È possibile configurare ed eseguire il drill-through a una pagina nello stesso report, ma non si può eseguire il drill-through a una pagina in un report diverso.  



## <a name="use-your-own-image-for-a-back-button"></a>Usare un'immagine personalizzata per un pulsante Indietro    
 Poiché il pulsante Indietro è un'immagine, è possibile sostituire l'immagine di tale oggetto visivo con qualsiasi altra immagine desiderata. Tale immagine continua a funzionare come pulsante Indietro per permettere agli utenti del report di tornare alla pagina originale. 

Per usare un'immagine personalizzata per un pulsante Indietro, seguire questa procedura:

1. Nella scheda **Home** selezionare **Immagine**. Individuare quindi l'immagine e inserirla nella pagina di drill-through.

2. Selezionare la nuova immagine nella pagina di drill-through. Nel riquadro **Formato immagine** impostare il dispositivo di scorrimento **Azione** su **Attivato** e quindi impostare **Tipo** su **Indietro**. A questo punto, l'immagine funziona come pulsante Indietro.

    ![Caricare l'immagine e impostare il tipo su Indietro](media/desktop-drillthrough/drillthrough_05.png)

    
     Ora gli utenti possono fare clic con il pulsante destro del mouse su un punto dati nel report e ottenere un menu di scelta rapida che supporta il drill-through a tale pagina. 

    ![Menu drill-through](media/desktop-drillthrough/drillthrough_04.png)

    Quando gli utenti del report scelgono di eseguire il drill-through, la pagina viene filtrata per visualizzare le informazioni sul punto dati su cui hanno fatto clic con il pulsante destro del mouse. Si supponga, ad esempio, che l'utente abbia fatto clic con il pulsante destro del mouse su un punto dati relativo a Contoso, un produttore, e abbia scelto di eseguire il drill-through. La pagina di drill-through visualizzata verrà filtrata in base a Contoso.

## <a name="pass-all-filters-in-drill-through"></a>Passare tutti i filtri nel drill-through

È possibile passare tutti i filtri applicati alla finestra di drill-through. Ad esempio, è possibile selezionare solo una determinata categoria di prodotti e gli oggetti visivi filtrati per tale categoria e quindi selezionare il drill-through. È interessante vedere che aspetto ha il drill-through con tutti questi filtri applicati.

Per mantenere tutti i filtri applicati, nella sezione **Drill-through** del riquadro **Visualizzazioni** impostare **Mantieni tutti i filtri** su **Attiva**. 

![Mantieni tutti i filtri](media/desktop-drillthrough/drillthrough_06.png)

Quando si esegue il drill-through su un oggetto visivo, è possibile vedere quali filtri sono stati applicati come risultato dell'applicazione di filtri temporanei all'oggetto visivo di origine. Nella sezione **Drill-through** del riquadro **Visualizzazione** tali filtri temporanei vengono visualizzati in corsivo. 

![Filtri temporanei in corsivo](media/desktop-drillthrough/drillthrough_07.png)

Anche se è possibile eseguire questa operazione con le pagine di descrizioni comandi, l'operazione risulterebbe insolita in quanto la descrizione comando non funzionerebbe correttamente. Per questo motivo, non è consigliabile eseguire l'operazione con le descrizioni comando.

## <a name="add-a-measure-to-drill-through"></a>Aggiungere una misura al drill-through

Oltre a passare tutti i filtri alla finestra di drill-through, è anche possibile aggiungere una misura o una colonna numerica di riepilogo all'area di drill-through. Trascinare il campo di drill-through nella scheda **Drill-through** per applicarlo. 

![Aggiungere una misura al drill-through](media/desktop-drillthrough/drillthrough_08.png)

Quando si aggiunge una misura o una colonna numerica di riepilogo, è possibile eseguire il drill-through alla pagina quando il campo viene usato nell'area *Valore* di un oggetto visivo.

Non sono necessarie altre operazioni per l'uso del drill-through nei report. Questo strumento è ideale per ottenere una visualizzazione espansa delle informazioni sulle entità selezionate per il filtro di drill-through.

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Usare il drill-through tra report nei report di Power BI](desktop-cross-report-drill-through.md)
* [Uso dei filtri dei dati in Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
