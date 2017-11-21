---
title: Riquadro Analisi nel servizio Power BI
description: Creare linee di riferimento dinamiche per gli oggetti visivi nel servizio Power BI
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 05/02/2017
ms.author: mihart
ms.openlocfilehash: 30fc0731f819f063aa04e856e8acc75a69f64a59
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="analytics-pane-in-power-bi-service"></a>Riquadro Analisi nel servizio Power BI
Il riquadro **Analisi** nel **servizio Power BI** consente di aggiungere *linee di riferimento* dinamiche alle visualizzazioni e di concentrare l'attenzione su tendenze o informazioni importanti.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> Il riquadro **Analisi** viene visualizzato solo quando si seleziona un oggetto visivo nell'area di disegno report.
> 
> 

## <a name="using-the-analytics-pane"></a>Uso del riquadro Analisi
Con il riquadro **Analisi** è possibile creare i seguenti tipi di linee di riferimento dinamiche, anche se non tutte le linee sono disponibili per tutti i tipi di oggetti visivi:

* Linea costante asse X
* Linea costante asse Y
* Linea minima
* Linea massima
* Linea media
* Linea mediana
* Linea percentile

Le sezioni seguenti mostrano come usare il riquadro **Analisi** e le linee di riferimento dinamiche nelle visualizzazioni.

Per visualizzare le linee di riferimento dinamiche disponibili per un oggetto visivo, seguire questa procedura:

1. Selezionare o creare un oggetto visivo, quindi selezionare l'icona **Analisi** ![](media/service-analytics-pane/power-bi-analytics-icon.png) dal riquadro **Visualizzazioni**.
2. Selezionare la freccia rivolta verso il basso per il tipo di linea che si desidera creare per espandere le opzioni. In questo caso, si selezionerà **Linea media**.
   
   ![](media/service-analytics-pane/power-bi-add.png)
3. Per creare una nuova linea, selezionare **+ Aggiungi**. È quindi possibile specificare un nome per la linea facendo doppio clic sulla casella di testo, quindi digitando il nome.
   
   Sono disponibili moltissime opzioni per la linea, ad esempio per impostare *colore*, *trasparenza*, *stile* e *posizione* relativamente a elementi dati dell'oggetto visivo, oltre alla possibilità di scegliere se includere l'etichetta. Soprattutto, è possibile selezionare su quale **Misura** nell'oggetto visivo si desidera basare la linea selezionando il menu a discesa **Misura**, che viene automaticamente popolato con gli elementi dati dell'oggetto visivo. In questo caso, si selezionerà *Open store count* come misura, si etichetterà l'opzione come *Avg # Open Stores* e si personalizzeranno altre opzioni come illustrato di seguito.
   
   ![](media/service-analytics-pane/power-bi-average-line.png)
4. Se si desidera visualizzare un'etichetta dati, spostare il dispositivo di scorrimento **Etichetta dati** su On. In questo caso, si ottiene una serie completa di opzioni aggiuntive per l'etichetta dati.
5. Notare il numero visualizzato accanto all'elemento **Linea media** nel riquadro **Analisi**. Questo numero indica quante linee dinamiche sono attualmente presenti nell'oggetto visivo e di che tipo sono. Se si aggiunge un elemento **Linea costante** come obiettivo 9 per Store Count, è possibile notare che nel riquadro **Analisi** è ora presente anche una linea di riferimento **Linea costante** applicata a questo oggetto visivo.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   
   Se l'oggetto visivo selezionato non può contenere linee di riferimento dinamiche applicate, in questo caso un oggetto visivo **Mappa**, verrà visualizzato quanto segue nel momento in cui si seleziona il riquadro **Analisi**.
   
   ![](media/service-analytics-pane/power-bi-no-lines.png)

Sono moltissime le informazioni interessanti da poter evidenziare creando linee di riferimento dinamiche con il riquadro **Analisi**.

Sono previste altre funzionalità, ad esempio l'espansione degli oggetti visivi che possono avere linee di riferimento dinamiche applicate, pertanto è consigliabile tenersi aggiornati sulle novità.

## <a name="limitations"></a>Limitazioni
La possibilità di usare linee di riferimento dinamiche dipende dal tipo di oggetto visivo in uso. L'elenco seguente mostra le linee dinamiche attualmente disponibili per i vari oggetti visivi:

Gli oggetti visivi seguenti possono usufruire pienamente delle linee dinamiche:

* Grafico ad aree
* Grafico a linee
* Grafico a dispersione
* Istogramma a colonne raggruppate
* Grafico a barre raggruppate

Gli oggetti visivi seguenti possono usare solo una *linea costante* dal riquadro **Analisi**:

* Area in pila
* Barre in pila
* Istogramma in pila
* Barre in pila 100%
* Istogramma in pila 100%

Per gli oggetti visivi seguenti è attualmente disponibile solo la *linea di tendenza*:

* Linee non in pila
* Istogramma a colonne raggruppate

Infine, gli oggetti visivi non cartesiani attualmente non possono applicare linee dinamiche dal riquadro **Analisi**, ad esempio:

* Matrice
* Grafico a torta
* Grafico ad anello
* Tabella

## <a name="next-steps"></a>Passaggi successivi
[Riquadro Analisi in Power BI Desktop](desktop-analytics-pane.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

