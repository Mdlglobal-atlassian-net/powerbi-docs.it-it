---
title: Usare il drill-through in Power BI Desktop
description: Informazioni su come eseguire il drill-down nei dati, nella pagina di un nuovo report, in Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f4cf7b0b850445b794c092f01b7e9a837ca3f215
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Usare il drill-through in Power BI Desktop
Con il **drill-through** in **Power BI Desktop**, è possibile creare una pagina nel report incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Con la pagina del report evidenziata, gli utenti possono fare clic con il pulsante destro del mouse su un punto dati in altre pagine di report ed eseguire il drill-through nella pagina evidenziata per ottenere dettagli che vengono filtrati in base a tale contesto.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Uso del drill-through
Per usare il **drill-through**, creare una pagina di report con oggetti visivi che si vuole visualizzare sul tipo di entità per cui si fornirà il drill-through. Se ad esempio si è interessati a fornire il drill-through per i produttori, è possibile creare una pagina di drill-through con oggetti visivi indicanti le vendite totali, le unità spedite totali, le vendite per categoria, le vendite per area e così via. In questo modo, quando si esegue il drill-through in tale pagina, gli oggetti visivi saranno specifici del produttore su cui si è fatto click e che è stato selezionato per il drill-through.

In tale pagina di drill-through, nella sezione **Campi** del riquadro **Visualizzazioni** trascinare quindi il campo per cui si vuole eseguire il drill-through nell'area **Filtri di drill-through**.

![](media/desktop-drillthrough/drillthrough_02.png)

Quando si aggiunge un campo all'area **Filtri di drill-through**, **Power BI Desktop** crea automaticamente un oggetto visivo pulsante *Indietro*. Tale oggetto visivo diventa un pulsante nei report pubblicati e consente agli utenti che utilizzano il report nel **servizio Power BI** di tornare facilmente alla pagina del report da cui sono arrivati (la pagina da cui hanno selezionato il drill-through).

![](media/desktop-drillthrough/drillthrough_03.png)

Poiché il pulsante *Indietro* è un'immagine, è possibile sostituire l'immagine di tale oggetto visivo con qualsiasi altra, che funzionerà correttamente come pulsante per far tornare gli utenti del report alla pagina originale. Per usare la propria immagine per un pulsante Indietro, è sufficiente inserire l'oggetto visivo di un'immagine nella pagina di drill-through, quindi selezionare l'oggetto visivo e attivare il dispositivo di scorrimento *Pulsante Indietro*. In questo modo l'immagine funziona come un pulsante *Indietro*.

![](media/desktop-drillthrough/drillthrough_05.png)

Quando la pagina di **drill-through** è completa, se gli utenti fanno clic con il pulsante destro del mouse su un punto dati del report che usa il campo inserito nell'area **Filtri di drill-through** nella pagina di drill-through, viene visualizzato un menu di scelta rapida che consente agli utenti di eseguire il drill-through in tale pagina.

![](media/desktop-drillthrough/drillthrough_04.png)

Quando scelgono di eseguire il drill-through, la pagina viene filtrata per visualizzare le informazioni sul punto dati da cui hanno fatto clic con il pulsante destro del mouse. Se ad esempio hanno fatto clic con il pulsante destro del mouse su un punto dati relativo a Contoso (un produttore) e hanno selezionato il drill-through, la pagina di drill-through che viene visualizzata verrà filtrata in base a Contoso.

> [!NOTE]
> Solo il campo nell'area **Filtri di drill-through** viene passato alla pagina del report di drill-through. Non vengono passate altre informazioni contestuali.
> 
> 

Non sono necessarie altre operazioni per l'uso del **drill-through** nei report, che permette di ottenere una visualizzazione espansa delle informazioni sull'entità selezionate per il filtro di drill-through.

