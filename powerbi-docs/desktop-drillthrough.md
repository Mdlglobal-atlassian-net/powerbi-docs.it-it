---
title: Usare il drill-through in Power BI Desktop
description: Informazioni su come eseguire il drill-down nei dati, nella pagina di un nuovo report, in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4989e981c3f39a637b3bb4927c427be0005c7776
ms.sourcegitcommit: b343e44dbafc0b718c564402593d4b6e3a8ce97c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51027438"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Usare il drill-through in Power BI Desktop
Con il **drill-through** in **Power BI Desktop**, è possibile creare una pagina nel report incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Gli utenti possono fare clic con il pulsante destro del mouse su un punto dati in altre pagine del report. Possono quindi eseguire il drill-through fino alla pagina di interesse per ottenere informazioni dettagliate filtrate in base al contesto.

![Uso del drill-through](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Uso del drill-through
1. Per usare il **drill-through**, creare una pagina di report con gli oggetti visivi desiderati per il tipo di entità per la quale si fornirà il drill-through. 

    Si supponga, ad esempio, di voler fornire il drill-through per i produttori. È quindi possibile creare una pagina di drill-through con oggetti visivi che mostrano le vendite totali, le unità spedite totali, le vendite per categoria, le vendite per area e così via. In questo modo, quando si esegue il drill-through a tale pagina, gli oggetti visivi saranno specifici per il produttore selezionato.

2. Nella pagina di drill-through, nella sezione **Campi** del riquadro **Visualizzazioni**, trascinare quindi il campo per cui si vuole abilitare il drill-through nell'area **Filtri di drill-through**.

    ![Area drill-through](media/desktop-drillthrough/drillthrough_02.png)

    Quando si aggiunge un campo all'area **Filtri di drill-through**, **Power BI Desktop** crea automaticamente un oggetto visivo pulsante *Indietro*. Tale oggetto visivo diventa un pulsante nei report pubblicati. Gli utenti che utilizzano il report nel **servizio Power BI** possono usare questo pulsante per tornare alla pagina del report da cui sono arrivati.

    ![Immagine del drill-through](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Usare un'immagine personalizzata per un pulsante Indietro    
 Poiché il pulsante Indietro è un'immagine, è possibile sostituire l'immagine di tale oggetto visivo con qualsiasi altra immagine desiderata. Tale immagine continuerà a funzionare come pulsante Indietro per permettere agli utenti del report di tornare alla pagina originale. Per usare un'immagine personalizzata per un pulsante Indietro, eseguire questa procedura:

1. Nella scheda **Home** selezionare **Immagine**. Individuare quindi l'immagine e inserirla nella pagina di drill-through.

2. Selezionare la nuova immagine nella pagina di drill-through. Nella sezione **Formato immagine** impostare il dispositivo di scorrimento **Collegamento** su **Attivato** e quindi impostare **Tipo** su **Indietro**. A questo punto, l'immagine funziona come pulsante Indietro.

    ![Usare l'immagine per il pulsante Indietro](media/desktop-drillthrough/drillthrough_05.png)

    
     Ora gli utenti possono fare clic con il pulsante destro del mouse su un punto dati nel report e ottenere un menu di scelta rapida che supporta il drill-through a tale pagina. 

    ![Menu di drill-through](media/desktop-drillthrough/drillthrough_04.png)

    Quando gli utenti del report scelgono di eseguire il drill-through, la pagina viene filtrata per visualizzare le informazioni sul punto dati su cui hanno fatto clic con il pulsante destro del mouse. Si immagini, ad esempio, che l'utente abbia fatto clic con il pulsante destro del mouse su un punto dati relativo a Contoso (un produttore) e abbia scelto di eseguire il drill-through. La pagina di drill-through visualizzata verrà filtrata in base a Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Filtri in drill-through

A partire dalla versione di maggio 2018 di **Power BI Desktop**, è possibile eseguire tutti i filtri applicati alla finestra di drill-through. Ad esempio, è possibile selezionare solo una determinata categoria di prodotti e gli oggetti visivi filtrati per tale categoria e quindi selezionare il drill-through. È interessante vedere che aspetto ha il drill-through con tutti questi filtri applicati.

Per mantenere tutti i filtri applicati, nella sezione **Drill-through** del riquadro **Visualizzazioni** impostare l'interruttore **Mantieni tutti i filtri** su **Attiva**. 

![Mantieni tutti i filtri](media/desktop-drillthrough/drillthrough_06.png)

Nelle versioni di **Power BI Desktop** precedenti a quella di maggio 2018, il comportamento equivale a impostare l'interruttore su **Disattiva**.

Quando si esegue il drill-through su un oggetto visivo, è possibile vedere quali filtri sono stati applicati come risultato dell'applicazione di filtri temporanei all'oggetto visivo di origine. Nella finestra di drill-through tali filtri temporanei vengono visualizzati in corsivo. 

![Filtri temporanei in corsivo](media/desktop-drillthrough/drillthrough_07.png)

Sarebbe possibile eseguire questa operazione con le pagine di descrizioni comando, ma tale operazione risulterebbe insolita in quanto la descrizione comando non funzionerebbe correttamente. Per questo motivo, non è consigliabile eseguire l'operazione con le descrizioni comando.

## <a name="add-a-measure-to-drillthrough"></a>Aggiungere una misura al drill-through

Oltre a passare tutti i filtri alla finestra di drill-through, è anche possibile aggiungere una misura o una colonna numerica di riepilogo all'area di drill-through. Trascinare il campo di drill-through nella scheda Drill-through per applicarlo. 

![Aggiungere una misura al drill-through](media/desktop-drillthrough/drillthrough_08.png)

Quando si aggiunge una misura o una colonna numerica di riepilogo, è possibile eseguire il drill-through alla pagina quando il campo viene usato nell'area *Valore* di un oggetto visivo.

Non sono necessarie altre operazioni per l'uso del **drill-through** nei report. Questo strumento è ideale per ottenere una visualizzazione espansa delle informazioni sulle entità selezionate per il filtro di drill-through.

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Uso dei filtri dei dati in Power BI Desktop](visuals/desktop-slicers.md)

