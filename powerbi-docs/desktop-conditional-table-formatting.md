---
title: Formattazione della tabella condizionale in Power BI Desktop
description: Applicare la formattazione personalizzata alle tabelle
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
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1626c2af5906004b6b4f79f4830f003b96e241fc
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2018
---
# <a name="conditional-formatting-in-tables"></a>Formattazione condizionale nelle tabelle
Con la formattazione condizionale per le tabelle, è possibile specificare colori di sfondo personalizzati in base ai valori della cella o ad altri valori o campi e usare sfumature. Per accedere alla formattazione condizionale, nel contenitore **Campi** del riquadro **Visualizzazioni** in Power BI Desktop selezionare la freccia rivolta verso il basso accanto al valore nell'area **Valori** che si vuole formattare o fare clic con il pulsante destro del mouse sul campo. È possibile gestire la formattazione condizionale solo per i campi nell'area **Valori** dell'area **Campi**.

![Formattazione condizionale delle tabelle](media/desktop-conditional-table-formatting/table-formatting_1.png)

Nella finestra di dialogo visualizzata, è possibile configurare il colore, così come il valore *minimo* e *massimo*. Se si seleziona la casella **Divergente**, è possibile configurare anche un valore *Centro* facoltativo.

![Colori divergenti](media/desktop-conditional-table-formatting/table-formatting_2.png)

È anche possibile scegliere la sfumatura di colore di un campo in base al modello di dati. È possibile anche specificare il tipo di aggregazione per il campo selezionato. Il campo selezionato viene specificato nel campo **Applica il colore a**, in modo che sia possibile tenerne traccia.

![Applicare il colore in base a un campo](media/desktop-conditional-table-formatting/table-formatting_2b.png)

Se applicata a una tabella, la formattazione personalizzata eseguita con la procedura descritta sopra sostituisce tutti gli stili della tabella personalizzati applicati alle celle formattate in modo condizionale.

![Formattazione tabelle](media/desktop-conditional-table-formatting/table-formatting_3.png)

È anche possibile applicare la formattazione condizionale a campi di testo e data, purché si scelga un valore numerico come base per la formattazione. 

Per rimuovere la formattazione condizionale da una visualizzazione, è sufficiente fare nuovamente clic con il pulsante destro del mouse sul campo e selezionare **Rimuovi formattazione condizionale**.

![Rimozione della formattazione tabelle](media/desktop-conditional-table-formatting/table-formatting_4.png)

