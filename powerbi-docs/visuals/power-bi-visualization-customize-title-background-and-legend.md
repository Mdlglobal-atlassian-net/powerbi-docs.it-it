---
title: Introduzione alla formattazione delle visualizzazioni di Power BI
description: Personalizzare il riquadro, lo sfondo e la legenda della visualizzazione
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6228ed70dd78ffca6cd3c8803518b2b27674576f
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389949"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>Personalizzare i titoli, le legende e gli sfondi delle visualizzazioni

Questa esercitazione illustra alcuni modi disponibili per personalizzare le visualizzazioni. Esistono numerose opzioni per la personalizzazione delle visualizzazioni. Il modo migliore per conoscerle tutte è esplorando il riquadro **Formato** (selezionare l'icona del rullo). Per iniziare, questo articolo illustra come personalizzare il titolo, la legenda e lo sfondo di una visualizzazione.

Non è possibile personalizzare tutte le visualizzazioni. Vedere l'[elenco completo](#visualization-types-that-you-can-customize) delle visualizzazioni per altri dettagli.

Avanzare rapidamente nel video fino a 4:50 per vedere una dimostrazione di come personalizzare le visualizzazioni:

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Seguire ora le istruzioni riportate di seguito per provare in prima persona con i propri dati.

## <a name="prerequisites"></a>Prerequisiti

- Servizio Power BI o Power BI Desktop

- Report Retail Analysis Sample

## <a name="customize-visualization-titles-in-reports"></a>Personalizzazione dei titoli delle visualizzazioni nei report

Per seguire la procedura, accedere al [servizio Power BI](https://app.powerbi.com) e aprire il report [Retail Analysis Sample](../sample-datasets.md) nella visualizzazione [Modifica report](../service-interact-with-a-report-in-editing-view.md).

> [!NOTE]
> quando si aggiunge una visualizzazione a un dashboard, questa diventa un riquadro del dashboard. È possibile personalizzare anche i riquadri, [ridimensionandoli e aggiungendo nuovi titoli, sottotitoli e collegamenti ipertestuali](../service-dashboard-edit-tile.md).

1. Passare alla pagina **New Stores** del report **Retail Analysis Sample**.

1. Selezionare l'istogramma a colonne raggruppate **Open Store Count by Open Month and Chain**.

1. Nel riquadro **Visualizzazioni** selezionare l'icona del rullo per mostrare le opzioni di formattazione.

1. Selezionare **Titolo** per espandere tale sezione.

   ![Screenshot del riquadro Formato con l'icona del rullo evidenziata e una freccia che indica l'elenco a discesa Titolo.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-formatting-menu.png)

1. Spostare il dispositivo di scorrimento per **Titolo** su **Attiva**.

   ![Screenshot del dispositivo di scorrimento impostato su Attiva.](media/power-bi-visualization-customize-title-background-and-legend/onoffslider.png)

1. Per modificare il titolo, immettere *Store count by month opened* nel campo **Testo titolo**.

1. Impostare il colore arancione per **Colore carattere** e il giallo per **Colore sfondo**.

    1. Selezionare l'elenco a discesa e scegliere un colore in **Colori tema**, **Colori recenti** o **Colore personalizzato**.

        ![Screenshot delle opzioni per Colore carattere e Colore sfondo.](media/power-bi-visualization-customize-title-background-and-legend/customizecolorpicker.png)

    1. Selezionare l'elenco a discesa per chiudere la finestra del colore.

       Salvare le modifiche apportate.

       Se dovesse risultare necessario annullare tutte le modifiche, è possibile tornare ai colori predefiniti selezionando **Ripristina valori predefiniti** nella finestra del colore.

1. Aumentare le dimensioni del testo fino a **12 pt**.

1. L'ultima personalizzazione da apportare al titolo del grafico consiste nell'allinearlo al centro della visualizzazione.

    ![Screenshot dei controlli Allineamento con l'opzione Al centro selezionata.](media/power-bi-visualization-customize-title-background-and-legend/customizealign.png)

A questo punto dell'esercitazione il titolo dell'istogramma a colonne raggruppate sarà simile al seguente:

![Schermata dell'istogramma a colonne raggruppate appena configurato.](media/power-bi-visualization-customize-title-background-and-legend/tutorialprogress1.png)

Salvare le modifiche apportate e passare alla sezione successiva.

Se dovesse risultare necessario annullare tutte le modifiche, selezionare **Ripristina valori predefiniti** nella parte inferiore del riquadro di personalizzazione **Titolo**.

![Screenshot dell'opzione Ripristina valori predefiniti.](media/power-bi-visualization-customize-title-background-and-legend/revertall.png)

## <a name="customize-visualization-backgrounds"></a>Personalizzare gli sfondi delle visualizzazioni

Usare lo stesso istogramma a colonne raggruppate selezionato ed espandere le opzioni per **Sfondo**.

1. Spostare il dispositivo di scorrimento per **Sfondo** su **Attiva**.

1. Selezionare l'elenco a discesa e scegliere un colore grigio.

1. Impostare **Trasparenza** su **74%** .

A questo punto dell'esercitazione lo sfondo dell'istogramma a colonne raggruppate sarà simile al seguente:

![Screenshot dell'istogramma a colonne raggruppate con il colore di sfondo aggiornato.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-customize-background.png)

Salvare le modifiche apportate e passare alla sezione successiva.

Se dovesse risultare necessario annullare tutte le modifiche, selezionare **Ripristina valori predefiniti** nella parte inferiore del riquadro di personalizzazione **Sfondo**.

## <a name="customize-visualization-legends"></a>Personalizzare le legende delle visualizzazioni

1. Aprire la pagina del report **Overview** e selezionare il grafico **Total Sales Variance by FiscalMonth and District Manager**.

1. Nella scheda **Visualizzazioni** selezionare l'icona del rullo per aprire il riquadro Formato.

1. Espandere le opzioni per **Legenda**:

      ![Screenshot dell'opzione Legenda.](media/power-bi-visualization-customize-title-background-and-legend/legend.png)

1. Spostare il dispositivo di scorrimento per **Legenda** su **Attiva**.

1. Spostare la legenda a sinistra della visualizzazione.

1. Aggiungere un titolo alla legenda impostando **Titolo** su **Attiva**.

1. Immettere *Manager* nel campo **Nome legenda**.

A questo punto dell'esercitazione la legenda dell'istogramma a colonne raggruppate sarà simile al seguente:

![Screenshot della legenda aggiornata nell'istogramma a colonne raggruppate.](media/power-bi-visualization-customize-title-background-and-legend/legend-move.png)

Salvare le modifiche apportate e passare alla sezione successiva.

Se dovesse risultare necessario annullare tutte le modifiche, selezionare **Ripristina valori predefiniti** nella parte inferiore del riquadro di personalizzazione **Legenda**.

## <a name="visualization-types-that-you-can-customize"></a>Tipi di visualizzazione che è possibile personalizzare

Ecco un elenco delle visualizzazioni e delle opzioni di personalizzazione disponibili per ognuna:

| Visualizzazione | Titolo | Sfondo | Legenda |
|:--- |:--- |:--- |:--- |
| Area | sì | sì |sì |
| Barre | sì | sì |sì |
| Scheda | sì | sì |n/a |
| Scheda con più righe | sì | sì | n/a |
| strutturata | sì | sì | sì |
| Grafico combinato | sì | sì | sì |
| Grafico ad anello | sì | sì | sì |
| Mappa colorata | sì | sì | sì |
| Grafico a imbuto | sì | sì | n/a |
| Misuratore | sì | sì | n/a |
| Indicatore KPI | sì | sì | n/a |
| Linea | sì | sì | sì |
| Mappa | sì | sì | sì |
| Matrice | sì | sì | n/a |
| Torta | sì | sì | sì |
| Dispersione | sì | sì | sì |
| Filtro dei dati | sì | sì | n/a |
| Tabella | sì | sì | n/a |
| Casella di testo | no | sì | n/a |
| Mappa ad albero | sì | sì | sì |
| Waterfall | sì | sì | sì |

## <a name="next-steps"></a>Passaggi successivi

- [Personalizzare le proprietà degli assi X e Y](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Introduzione alla formattazione dei colori e alle proprietà degli assi](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Concetti di base del servizio Power BI per i consumer](../consumer/end-user-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
