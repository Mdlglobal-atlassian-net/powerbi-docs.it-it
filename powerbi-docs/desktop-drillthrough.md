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
ms.openlocfilehash: 8bbfafcecb6876ea063bb6751ca31c25697dc185
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44725858"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Usare il drill-through in Power BI Desktop
Con il **drill-through** in **Power BI Desktop**, è possibile creare una pagina nel report incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Con la pagina del report evidenziata, è possibile fare clic con il pulsante destro del mouse su un punto dati in altre pagine di report ed eseguire il drill-through nella pagina evidenziata per ottenere dettagli che vengono filtrati in base a tale contesto.

![Uso del drill-through](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Uso del drill-through
1. Per usare il **drill-through**, creare una pagina di report con oggetti visivi da visualizzare per il tipo di entità per cui si fornirà il drill-through. 

    Se ad esempio si è interessati a fornire il drill-through per i produttori, è possibile creare una pagina di drill-through con oggetti visivi indicanti le vendite totali, le unità spedite totali, le vendite per categoria, le vendite per area e così via. In questo modo, quando si esegue il drill-through in tale pagina, gli oggetti visivi saranno specifici del produttore selezionato.

2. In tale pagina di drill-through, nella sezione **Campi** del riquadro **Visualizzazioni**, trascinare il campo per cui si vuole eseguire il drill-through nell'area **Filtri di drill-through**.

    ![Area drill-through](media/desktop-drillthrough/drillthrough_02.png)

    Quando si aggiunge un campo all'area **Filtri di drill-through**, **Power BI Desktop** crea automaticamente un oggetto visivo pulsante *Indietro*. Tale oggetto visivo diventa un pulsante nei report pubblicati e consente agli utenti che utilizzano il report nel **servizio Power BI** di tornare facilmente alla pagina del report da cui sono arrivati (la pagina da cui hanno selezionato il drill-through).

    ![Immagine drill-through](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Usare un'immagine personalizzata per un pulsante Indietro    
 Poiché il pulsante Indietro è un'immagine, è possibile sostituire l'immagine di tale oggetto visivo con qualsiasi altra, che continuerà a funzionare come pulsante Indietro per far tornare gli utenti del report alla pagina originale.

1. Nella scheda **Home** fare clic su **Immagine** e quindi individuare l'immagine e inserirla nella pagina di drill-through.
2. Selezionare la nuova immagine nella pagina di drill-through e nella sezione Formato immagine impostare il dispositivo di scorrimento **Collegamento** su attivato e impostare il **Tipo** su **Pulsante Indietro**. A questo punto, l'immagine funziona come pulsante Indietro.

    ![Uso immagine per tornare indietro](media/desktop-drillthrough/drillthrough_05.png)

    Quando la pagina di **drill-through** è completa, facendo clic con il pulsante destro del mouse su un punto dati del report che usa il campo inserito nell'area **Filtri di drill-through**, viene visualizzato un menu di scelta rapida che consente di eseguire il drill-through in tale pagina.

    ![Menu drill-through](media/desktop-drillthrough/drillthrough_04.png)

    Quando gli utenti del report scelgono di eseguire il drill-through, la pagina viene filtrata per visualizzare le informazioni sul punto dati selezionato con il pulsante destro del mouse. Se ad esempio hanno selezionato con il pulsante destro del mouse un punto dati relativo a Contoso (un produttore) e hanno scelto di eseguire il drill-through, la pagina di drill-through visualizzata verrà filtrata in base a Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Filtri in drill-through

A partire dalla versione di maggio 2018 di **Power BI Desktop**, è possibile eseguire tutti i filtri applicati alla finestra di drill-through. Ad esempio, è possibile selezionare solo una determinata categoria di prodotti e gli oggetti visivi filtrati per tale categoria, e quindi selezionare il drill-through. È interessante vedere che aspetto ha il drill-through con tutti questi filtri applicati.

Per mantenere tutti i filtri applicati, nella sezione **Drill-through** del riquadro **Visualizzazioni** è sufficiente impostare l'alternanza **Mantieni tutti i filtri** su **On**. 

![Mantieni tutti i filtri](media/desktop-drillthrough/drillthrough_06.png)

Nelle versioni di **Power BI Desktop** precedenti a quella di maggio 2018, il comportamento equivale a impostare l'alternanza su **Off**.

Quando si esegue il drill-through su un oggetto visivo, è possibile visualizzare i filtri applicati come risultato dell'applicazione di filtri temporanei all'oggetto visivo di origine. Nella finestra di drill-through tali filtri temporanei vengono visualizzati in corsivo. 

![Filtri temporanei in corsivo](media/desktop-drillthrough/drillthrough_07.png)

Si noti che è possibile eseguire questa operazione con le pagine di descrizioni comandi, ma tale operazione non è consigliata in quanto la descrizione comando non viene visualizzata correttamente.

## <a name="add-a-measure-to-drillthrough"></a>Aggiungere una misura al drill-through

Oltre a passare tutti i filtri alla finestra di drill-through, è anche possibile aggiungere una misura (o una colonna numerica di riepilogo) all'area di drill-through. Trascinare il campo di drill-through nella scheda Drill-through per applicarlo. 

![Aggiungere una misura al drill-through](media/desktop-drillthrough/drillthrough_08.png)

Quando si aggiunge una misura (o una colonna numerica di riepilogo), è possibile accedere alla pagina quando il campo viene usato nell'area *Valore* di un oggetto visivo.

Non sono necessarie altre operazioni per l'uso del **drill-through** nei report, che permette di ottenere una visualizzazione espansa delle informazioni sull'entità selezionate per il filtro di drill-through.

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Uso dei filtri dei dati in Power BI Desktop](visuals/desktop-slicers.md)

