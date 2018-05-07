---
title: Usare il drill-through in Power BI Desktop
description: Informazioni su come eseguire il drill-down nei dati, nella pagina di un nuovo report, in Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 4/10/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b5da2bf43f2d38e0828571e2b9d404feb615ac69
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Usare il drill-through in Power BI Desktop
Con il **drill-through** in **Power BI Desktop**, è possibile creare una pagina nel report incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Con la pagina del report evidenziata, è possibile fare clic con il pulsante destro del mouse su un punto dati in altre pagine di report ed eseguire il drill-through nella pagina evidenziata per ottenere dettagli che vengono filtrati in base a tale contesto.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Uso del drill-through
1. Per usare il **drill-through**, creare una pagina di report con oggetti visivi da visualizzare per il tipo di entità per cui si fornirà il drill-through. 

    Se ad esempio si è interessati a fornire il drill-through per i produttori, è possibile creare una pagina di drill-through con oggetti visivi indicanti le vendite totali, le unità spedite totali, le vendite per categoria, le vendite per area e così via. In questo modo, quando si esegue il drill-through in tale pagina, gli oggetti visivi saranno specifici del produttore selezionato.

2. In tale pagina di drill-through, nella sezione **Campi** del riquadro **Visualizzazioni**, trascinare il campo per cui si vuole eseguire il drill-through nell'area **Filtri di drill-through**.

    ![](media/desktop-drillthrough/drillthrough_02.png)

    Quando si aggiunge un campo all'area **Filtri di drill-through**, **Power BI Desktop** crea automaticamente un oggetto visivo pulsante *Indietro*. Tale oggetto visivo diventa un pulsante nei report pubblicati e consente agli utenti che utilizzano il report nel **servizio Power BI** di tornare facilmente alla pagina del report da cui sono arrivati (la pagina da cui hanno selezionato il drill-through).

    ![](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Usare un'immagine personalizzata per un pulsante Indietro    
 Poiché il pulsante Indietro è un'immagine, è possibile sostituire l'immagine di tale oggetto visivo con qualsiasi altra, che continuerà a funzionare come pulsante Indietro per far tornare gli utenti del report alla pagina originale.

1. Per usare un'immagine personalizzata per un pulsante Indietro, inserire l'oggetto visivo di un'immagine nella pagina di drill-through.
2. Selezionare l'oggetto visivo e impostare il dispositivo di scorrimento su **Pulsante Indietro**. A questo punto, l'immagine funziona come pulsante Indietro.

    ![](media/desktop-drillthrough/drillthrough_05.png)

    Quando la pagina di **drill-through** è completa, facendo clic con il pulsante destro del mouse su un punto dati del report che usa il campo inserito nell'area **Filtri di drill-through**, viene visualizzato un menu di scelta rapida che consente di eseguire il drill-through in tale pagina.

    ![](media/desktop-drillthrough/drillthrough_04.png)

    Quando gli utenti del report scelgono di eseguire il drill-through, la pagina viene filtrata per visualizzare le informazioni sul punto dati selezionato con il pulsante destro del mouse. Se ad esempio hanno selezionato con il pulsante destro del mouse un punto dati relativo a Contoso (un produttore) e hanno scelto di eseguire il drill-through, la pagina di drill-through visualizzata verrà filtrata in base a Contoso.

    > [!NOTE]
    > Solo il campo nell'area **Filtri di drill-through** viene passato alla pagina del report di drill-through. Non vengono passate altre informazioni contestuali.
    > 
    > 

Non sono necessarie altre operazioni per l'uso del **drill-through** nei report, che permette di ottenere una visualizzazione espansa delle informazioni sull'entità selezionate per il filtro di drill-through.

