---
title: Usare il riquadro Analisi in Power BI Desktop
description: Creare linee di riferimento dinamiche per gli oggetti visivi in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4ad843078e452502a94aa7d60b3304528fd25496
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76038641"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Usare il riquadro Analisi in Power BI Desktop

Il riquadro **Analisi** in Power BI Desktop consente di aggiungere *linee di riferimento* dinamiche agli oggetti visivi e incentrare l'attenzione su tendenze o informazioni importanti. L'icona e il riquadro **Analisi** sono disponibili nell'area **Visualizzazioni** di Power BI Desktop.

![Riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Il riquadro **Analisi** viene visualizzato solo quando si seleziona un oggetto visivo nell'area di disegno di Power BI Desktop.

## <a name="search-within-the-analytics-pane"></a>Eseguire ricerche all'interno del riquadro Analisi

A partire dalla versione di febbraio 2018 di Power BI Desktop (versione 2.55.5010.201 o successive) è possibile eseguire ricerche all'interno del riquadro **Analisi** che è una sottosezione del riquadro **Visualizzazioni**. La casella di ricerca viene visualizzata quando si seleziona l'icona **Analisi**.

![Casella di ricerca, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Usare il riquadro Analisi

Con il riquadro **Analisi** è possibile creare i seguenti tipi di linee di riferimento dinamiche:

* Linea costante asse X
* Linea costante asse Y
* Linea minima
* Linea massima
* Linea media
* Linea mediana
* Linea percentile
* Ombreggiatura simmetrica

> [!NOTE]
> Non tutte le linee sono disponibili per tutti i tipi di oggetti visivi.

Le sezioni seguenti mostrano come usare il riquadro **Analisi** e le linee di riferimento dinamiche nelle visualizzazioni.

Per visualizzare le linee di riferimento dinamiche disponibili per un oggetto visivo, seguire questa procedura:

1. Selezionare o creare un oggetto visivo, quindi selezionare l'icona **Analisi** dalla sezione **Visualizzazioni**.

    ![Visualizzare analisi per un oggetto visivo, riquadro Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Selezionare il tipo di linea che si vuole creare per espandere le opzioni corrispondenti. In questo caso si selezionerà **Linea media**.

    ![Linea media, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Per creare una nuova linea selezionare **+&nbsp;Aggiungi**. Quindi è possibile assegnare un nome alla linea. Fare doppio clic sulla casella di testo e immettere il nome.

    Ora sono disponibili molte opzioni per la linea. È possibile specificare le opzioni **Colore**, percentuale di **Trasparenza**, **Stile linea** e **Posizione** (rispetto agli elementi dati dell'oggetto visivo). È anche possibile scegliere se includere l'**Etichetta dati**. Per specificare la misura visiva su cui basare la linea, selezionare l'elenco a discesa **Misura**, che viene popolato automaticamente con elementi dati dell'oggetto visivo. In questo caso si selezionerà **Culture** come misura, si etichetterà l'opzione come *Average of Culture* e si personalizzeranno altre opzioni.

    ![Linea media di Culture, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Se si vuole visualizzare un'etichetta dati, spostare il dispositivo di scorrimento **Etichetta dati** da **Disattivato** ad **Attivato**. In questo caso, si ottiene una serie completa di opzioni aggiuntive per l'etichetta dati.

    ![Impostazioni Etichetta dati, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Notare il numero visualizzato accanto all'elemento **Linea media** nel riquadro **Analisi**. Questo numero indica quante linee dinamiche sono attualmente presenti nell'oggetto visivo e di che tipo sono. Se si aggiunge una **Linea massima** per **Affordability**, il riquadro **Analisi** ora visualizza anche una linea di riferimento dinamica **Linea massima** applicata a questo oggetto visivo.

    ![Totali Linea massima e Linea media, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Se non è possibile applicare linee di riferimento dinamiche all'oggetto visivo selezionato (in questo caso un oggetto visivo **Mappa**), quando si seleziona il riquadro **Analisi** viene visualizzato il messaggio seguente.

![Analisi non disponibile per oggetto visivo Mappa, Riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

È possibile evidenziare molte informazioni interessanti creando linee di riferimento dinamiche con il riquadro **Analisi**.

In futuro è prevista l'aggiunta di altre funzionalità, ad esempio l'espansione degli oggetti visivi ai quali è possibile applicare linee di riferimento dinamiche. Tornare spesso a questo argomento per visualizzare le novità.

## <a name="apply-forecasting"></a>Applicare la previsione

Se sono presenti dati temporali nell'origine dati, è possibile usare la funzionalità di *previsione*. Selezionare un oggetto visivo, quindi espandere la sezione **Previsione** del riquadro **Analisi**. È possibile specificare molti input per modificare la previsione, ad esempio **Lunghezza previsione** o **Intervallo di confidenza**. L'immagine seguente illustra un oggetto visivo a linee di base con la previsione applicata. È possibile sperimentare per applicare la funzionalità di previsione ai modelli in molti modi.

![Funzionalità Previsione, riquadro Analisi, Visualizzazioni, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> La funzionalità di previsione è disponibile solo per gli oggetti visivi grafico a linee.

## <a name="limitations"></a>Limitazioni

La possibilità di usare linee di riferimento dinamiche dipende dal tipo di oggetto visivo in uso. Gli elenchi seguenti descrivono in maggior dettaglio queste limitazioni.

È possibile usare *Linea costante asse X*, *Linea costante asse Y* e *Ombreggiatura simmetrica* nel seguente oggetto visivo:

* Grafico a dispersione

L'uso di *Linea costante*, *Linea minima*, *Linea massima*, *Linea media*, *Linea mediana* e *Linea percentile* è disponibile negli oggetti visivi seguenti:

* Grafico ad aree
* Grafico a barre raggruppate
* Istogramma a colonne raggruppate
* Grafico a linee
* Grafico a dispersione

Gli oggetti visivi seguenti possono usare solo una *linea costante* dal riquadro **Analisi**:

* Grafico ad area in pila
* Grafico a barre in pila
* Istogramma a colonne in pila
* Grafico a cascata
* Grafico a barre in pila 100%
* Istogramma a colonne in pila 100%

Gli oggetti visivi seguenti possono usare una *linea di tendenza* se sono presenti dati temporali:

* Grafico ad aree
* Istogramma a colonne raggruppate
* Grafico a linee
* Linea e Istogramma a colonne raggruppate

Infine non è attualmente possibile applicare linee dinamiche a molti oggetti visivi, tra cui (a titolo di esempio):

* Grafico a imbuto
* Linea e Istogramma a colonne raggruppate
* Grafico a linee e istogramma a colonne in pila
* Grafico a nastri
* Oggetti visivi non cartesiani come ad esempio Grafico ad anello, Misuratore, Matrice, Grafico a torta e Tabella

La *linea del percentile* è disponibile solo quando si usano dati importati in Power BI Desktop o con una connessione dinamica a un modello in un server che esegue **Analysis Services 2016** o versione successiva, **Azure Analysis Services** o un set di dati nel servizio Power BI.

## <a name="next-steps"></a>Passaggi successivi

Power BI Desktop offre infinite possibilità. Per altre informazioni sulle capacità disponibili, vedere le risorse seguenti:

* [Novità di Power BI Desktop](desktop-latest-update.md)
* [Ottenere Power BI Desktop](desktop-get-the-desktop.md)
* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Tipi di dati in Power BI Desktop](desktop-data-types.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Eseguire attività comuni in Power BI Desktop](desktop-common-query-tasks.md)
