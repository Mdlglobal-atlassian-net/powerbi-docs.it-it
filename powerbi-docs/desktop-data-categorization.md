---
title: Categorizzazione dei dati in Power BI Desktop
description: Categorizzazione dei dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 218a05c41c3befed8f8600f6a584560f5be92a1f
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709557"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Specificare le categorie di dati in Power BI Desktop
In *Power BI Desktop* è possibile specificare la categoria di dati per una colonna in modo tale che Power BI Desktop sappia come trattare i valori in una visualizzazione.

Quando Power BI Desktop importa i dati, ottiene altre informazioni oltre ai dati in sé, ad esempio i nomi delle tabelle e delle colonne, e determina se i dati sono una chiave primaria. Con tali informazioni Power BI Desktop fa alcune supposizioni su come offrire una valida esperienza predefinita per la creazione di una visualizzazione.
Ad esempio, quando una colonna include valori numerici, è probabile che si voglia aggregarli in qualche modo, quindi Power BI Desktop li inserisce nell'area **Valori** del riquadro **Visualizzazioni**. Oppure, nel caso di una colonna con valori di data e ora in un grafico a linee, Power BI Desktop suppone che la si voglia usare come asse della gerarchia temporale.

Esistono però alcuni casi che sono un po' più impegnativi come la geografia. Considerare la tabella seguente da un foglio di lavoro di Excel:

![](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop deve trattare i codici della colonna **GeoCode** come abbreviazione di un paese o come stato degli Stati Uniti?  Non è chiaro, perché tali codici possono significare entrambe le cose. Ad esempio, AL può significare Alabama o Albania, AR può significare Arkansas o Argentina oppure CA può significare California o Canada. Ciò fa la differenza quando si va a creare un grafico in base al campo GeoCode su una mappa. 

Power BI Desktop deve mostrare un'immagine del mondo con i paesi evidenziati? Oppure un'immagine degli Stati Uniti con gli stati evidenziati?  È possibile specificare una categoria di dati per tale tipo di dati. La categorizzazione dei dati ottimizza ulteriormente le informazioni usate da Power BI Desktop per fornire le visualizzazioni migliori.  

**Per specificare una categoria di dati**

1. Nell'elenco **Campi** nella visualizzazione **Report** o nella visualizzazione **Dati** selezionare il campo da archiviare con una categorizzazione diversa.
2. Sulla barra multifunzione, nell'area **Proprietà** della scheda **Creazione di modelli** selezionare la freccia a discesa accanto a **Categoria di dati**.  Questo elenco visualizza le categorie di dati che è possibile scegliere per la colonna. Alcune selezioni potrebbero essere disabilitate se non vengono usate con il tipo di dati corrente della colonna.  Se ad esempio una colonna è un tipo di dati binario, Power BI Desktop non consentirà di scegliere le categorie di dati geografici. 
3. Selezionare la categoria desiderata.

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

Potrebbe anche essere interessante ottenere informazioni sul [filtro geografico per le app Power BI per dispositivi mobili](desktop-mobile-geofiltering.md).

