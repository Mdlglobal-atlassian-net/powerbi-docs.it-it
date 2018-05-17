---
title: Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop
description: Informazioni su come usare un filtro dei dati per selezionare specifici intervalli in Power BI Desktop
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
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 460221ed9cf35b4c5db9509085a819519202d4a3
ms.sourcegitcommit: 50016425005d2e929c8c606c2d0d393342e05d39
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop
Con il **filtro dei dati per l'intervallo numerico**, è possibile applicare qualsiasi filtro a qualsiasi colonna numerica nel modello di dati. Si può decidere di usare il filtro **Tra** su più numeri oppure **Minore o uguale a** o **Maggiore o uguale a** rispetto a un numero. Anche se può sembrare semplice, è un modo molto efficace per filtrare i dati.

![Oggetto visivo con filtro dei dati per l'intervallo numerico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="using-the-numeric-range-slicer"></a>Uso del filtro dei dati per l'intervallo numerico
È possibile usare il filtro dei dati per l'intervallo numerico come qualsiasi altro filtro dei dati. È sufficiente creare un oggetto visivo **filtro dei dati** per il report e quindi selezionare un valore numerico per il valore **Campo**. Nell'immagine seguente è selezionato il campo *LineTotal*.

![Creare un filtro dei dati per l'intervallo numerico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Selezionare il collegamento freccia giù nell'angolo in alto a destra del **filtro dei dati per l'intervallo numerico** per visualizzare un menu.

![Menu del filtro dei dati per l'intervallo numerico](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Per l'intervallo numerico è possibile selezionare una delle tre opzioni seguenti:

* Tra
* Minore o uguale a
* Maggiore o uguale a

Quando si seleziona **Tra**, viene visualizzato un dispositivo di scorrimento che consente di applicare il filtro ai valori numerici compresi tra i numeri specificati. Oltre a usare la barra del dispositivo di scorrimento, è possibile fare clic nelle due caselle e digitare i valori. Questo risulta utile quando occorre filtrare in base a specifici numeri ma la granularità del dispositivo di scorrimento rende difficile selezionare il numero esatto.

Nell'immagine seguente la pagina del report è filtrata in base ai valori *LineTotal* compresi tra 2500,00 e 6000,00.

![Filtro dei dati per l'intervallo numerico con Tra](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Quando si seleziona **Minore o uguale a**, il punto di controllo a sinistra (valore più basso) della barra del dispositivo di scorrimento scompare ed è possibile modificare solo il limite superiore della barra stessa. Nell'immagine seguente il valore massimo della barra del dispositivo di scorrimento è impostato su 5928,19.

![Filtro dei dati per l'intervallo numerico con Minore di](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Infine, quando si seleziona **Maggiore o uguale a**, il punto di controllo a destra (valore più alto) della barra del dispositivo di scorrimento scompare ed è possibile modificare solo il valore inferiore, come mostrato nell'immagine seguente. A questo punto, negli oggetti visivi nella pagina del report vengono visualizzati solo gli elementi il cui valore *LineTotal* è superiore o uguale a 4902,99.

![Filtro dei dati per l'intervallo numerico con Maggiore di](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Allineamento ai numeri interi con il filtro dei dati per l'intervallo numerico

Un filtro dei dati per l'intervallo numerico viene allineato ai numeri interi, a meno che non si tratti di un intervallo decimale. In questo modo il filtro dei dati sarà allineato correttamente ai numeri interi. 


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Per il **filtro dei dati per l'intervallo numerico** è opportuno tenere presenti queste limitazioni e considerazioni:

* Il **filtro dei dati per l'intervallo numerico** attualmente filtra tutte le righe sottostanti nei dati, non i valori aggregati. Ad esempio, se si usa un filtro *Sales Amount*, viene filtrata ogni transazione basata su *Sales Amount*, non la somma di *Sales Amount* per ogni punto dati di un oggetto visivo.
* Attualmente non funziona con le misure.
