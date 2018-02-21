---
title: Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop
description: Informazioni su come usare un filtro dei dati per selezionare specifici intervalli in Power BI Desktop
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
ms.date: 02/05/2018
ms.author: davidi
ms.openlocfilehash: 6d63236254906619f7244db9f57af162a19a70d6
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop
Con il **filtro dei dati per l'intervallo numerico**, è possibile applicare qualsiasi filtro a qualsiasi colonna numerica nel modello di dati. Si può decidere di usare il filtro **Tra** su più numeri oppure **Minore o uguale a** o **Maggiore o uguale a** rispetto a un numero. Anche se può sembrare semplice, è un modo molto efficace per filtrare i dati.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Uso del filtro dei dati per l'intervallo numerico
È possibile usare il filtro dei dati per l'intervallo numerico come qualsiasi altro filtro dei dati. È sufficiente creare un oggetto visivo **filtro dei dati** per il report e quindi selezionare un valore numerico per il valore **Campo**. Nell'immagine seguente è selezionato il campo *UnitPrice*.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Selezionare la freccia in giù nell'angolo in alto a destra del **filtro dei dati per l'intervallo numerico** per visualizzare un menu.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

Per l'intervallo numerico è possibile selezionare una delle tre opzioni seguenti:

* Tra
* Minore o uguale a
* Maggiore o uguale a

Quando si seleziona **Tra**, viene visualizzato un dispositivo di scorrimento che consente di applicare il filtro ai valori numerici compresi tra i numeri specificati. Oltre a usare la barra del dispositivo di scorrimento, è possibile fare clic nelle due caselle e digitare i valori. Questo risulta utile quando occorre filtrare in base a specifici numeri interi ma la granularità del dispositivo di scorrimento rende difficile selezionare il numero esatto.

Nell'immagine seguente la pagina del report è filtrata in base ai valori *UnitPrice* compresi tra 500 e 1500.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

Quando si seleziona **Minore o uguale a**, il punto di controllo a sinistra (valore più basso) della barra del dispositivo di scorrimento scompare ed è possibile modificare solo il limite superiore della barra stessa. Nell'immagine seguente la barra del dispositivo di scorrimento è impostata su 497,17.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Infine, quando si seleziona **Maggiore o uguale a**, il punto di controllo a destra (valore più alto) della barra del dispositivo di scorrimento scompare ed è possibile modificare solo il valore inferiore, come mostrato nell'immagine seguente. A questo punto, negli oggetti visivi nella pagina del report vengono visualizzati solo gli elementi il cui valore *UnitPrice* è superiore o uguale a 750,56.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer-preview"></a>Allineamento ai numeri interi con il filtro dei dati per l'intervallo numerico (anteprima)

A partire dalla versione di febbraio 2018 di **Power BI Desktop**, il filtro dei dati per l'intervallo numerico verrà allineato ai numeri interi. In questo modo il filtro dei dati sarà allineato correttamente ai numeri interi. L'allineamento ai numeri interi non si applica ai filtri decimali.


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Per il **filtro dei dati per l'intervallo numerico** è opportuno tenere presenti queste limitazioni e considerazioni.

* Il **filtro dei dati per l'intervallo numerico** attualmente filtra tutte le righe sottostanti nei dati, non i valori aggregati. Ad esempio, se si usa un filtro *Sales Amount*, viene filtrata ogni transazione basata su *Sales Amount*, non la somma di *Sales Amount* per ogni punto dati di un oggetto visivo.
* Attualmente non funziona con le misure
* Al momento il **filtro dei dati per l'intervallo numerico** è disponibile solo in **Power BI Desktop**. Se un report che usa il **filtro dei dati per l'intervallo numerico** viene pubblicato nel **servizio Power BI**, il filtro verrà comunque applicato ma verrà visualizzato come filtro dei dati elenco.

