---
title: Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop
description: Informazioni su come usare un filtro dei dati per selezionare specifici intervalli in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f997ee7574c5dd9dc6b4d28767d599a97bf297ed
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669843"
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

Se i dati del campo sottostante sono di tipo **numero intero**, un filtro dei dati di intervallo numerico verrà allineato ai numeri interi. In questo modo il filtro dei dati sarà allineato correttamente ai numeri interi. I campi di tipo **numero decimale** consentono di immettere o selezionare le frazioni di un numero. La formattazione applicata nella casella di testo corrisponde alla formattazione impostata nel campo, anche se è possibile digitare o selezionare numeri più precisi.


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Per il **filtro dei dati per l'intervallo numerico** è opportuno tenere presenti queste limitazioni e considerazioni:

* Il **filtro dei dati per l'intervallo numerico** attualmente filtra tutte le righe sottostanti nei dati, non i valori aggregati. Ad esempio, se si usa un filtro *Sales Amount*, viene filtrata ogni transazione basata su *Sales Amount*, non la somma di *Sales Amount* per ogni punto dati di un oggetto visivo.
* Attualmente non funziona con le misure.
* È possibile digitare un qualsiasi numero nelle caselle di testo in un filtro dei dati numerico, anche se non è compreso nell'intervallo di valori nella colonna sottostante. Ciò consente di impostare filtri per dati che possono cambiare in futuro.
