---
title: Esplorare i report nelle app Power BI per dispositivi mobili
description: Informazioni sulla visualizzazione e sull'interazione con i report nelle app Power BI nel telefono o nel tablet. Creare report nel servizio Power BI o Power BI Desktop, quindi interagire con essi nelle app per dispositivi mobili.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 08/17/2018
ms.author: maggies
ms.openlocfilehash: 5fe4212be55a42a6892a94e2a07da8af5c035b6d
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44742956"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Esplorare i report nelle app Power BI per dispositivi mobili
Si applica a:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telefono Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivi Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Telefoni Android |Tablet Android |Dispositivi Windows 10 |

Un report di Power BI è una vista interattiva dei dati con elementi visivi che rappresentano conclusioni e approfondimenti diversi ottenuti da tali dati. La visualizzazione dei report nella app Power BI per dispositivi mobili è il terzo passaggio in un processo in tre fasi.

1. [Creare report in Power BI Desktop](../../desktop-report-view.md). In Power BI Desktop è persino possibile [ottimizzare un report per i telefoni](mobile-apps-view-phone-report.md). 
2. Pubblicare i report nel servizio Power BI [(https://powerbi.com)](https://powerbi.com) o in [Server di report di Power BI](../../report-server/get-started.md).  
3. È quindi possibile interagire con questi report nelle app Power BI per dispositivi mobili.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Aprire un report di Power BI nell'app per dispositivi mobili
A seconda della provenienza, i report di Power BI sono archiviati in posizioni diverse nell'app per dispositivi mobili. Possono trovarsi in App, Condivisi con l'utente corrente, Aree di lavoro (inclusa l'Area di lavoro personale) oppure in un server di report. In alcuni casi si accede attraverso un dashboard correlato per ottenere un report, e talvolta sono elencati.

* In un dashboard, toccare i puntini di sospensione (...) nell'angolo superiore destro di un riquadro > **Apri report**.
  
  ![Aprire un report](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Non tutti i riquadri offrono l'opzione di apertura in un report. Ad esempio, i riquadri creati ponendo una domanda nella casella Domande e risposte non aprono i report quando vengono toccati. 
  
  In un telefono, il report verrà aperto in modalità orizzontale, a meno che non sia [ottimizzato per la visualizzazione in un telefono](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Report per il telefono in modalità orizzontale](./media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Visualizzare i report ottimizzati per i telefoni
Gli autori di report di Power BI possono creare un layout di report ottimizzato in modo specifico per telefoni. Le pagine dei report ottimizzate per i telefoni includono funzionalità aggiuntive. È ad esempio possibile eseguire il drill-down e ordinare gli oggetti visivi ed è possibile accedere ai [filtri aggiunti dall'autore del report alla pagina del report](mobile-apps-view-phone-report.md#filter-the-report-page-on-a-phone). Il report viene aperto in un telefono filtrato in base ai valori usati per filtrare il report sul Web con un messaggio che segnala che ci sono filtri attivi nella pagina. È possibile modificare i filtri nel telefono.

In un elenco di report un report ottimizzato è contrassegnato da un'icona speciale ![Icona del report per il telefono](./media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Aprire il report per il telefono](./media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

Quando si visualizza tale report in un telefono, viene aperto in visualizzazione verticale.

![Report in visualizzazione verticale](./media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

 Un report può includere una combinazione di pagine che non sono ottimizzate per i telefoni. In tal caso, quando si scorrono i report la visualizzazione passerà da verticale a orizzontale per ogni pagina.

Altre informazioni sui [report ottimizzati per la visualizzazione telefono](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report"></a>Usare i filtri dei dati per filtrare un report
Quando si progetta un report in Power BI Desktop o nel servizio Power BI, prendere in considerazione l'[aggiunta di filtri dei dati a una pagina del report](../../visuals/power-bi-visualization-slicers.md). Sia l'autore che i colleghi potranno così usare i filtri dei dati per filtrare la pagina in un browser e nelle app per dispositivi mobili. Quando si visualizza il report in un telefono, è possibile visualizzare e interagire con i filtri dei dati in modalità orizzontale e in una pagina ottimizzata per la modalità verticale del telefono. Se si seleziona un valore in un filtro dei dati o in un filtro nel browser, il valore verrà selezionato anche quando si visualizza la pagina nell'app per dispositivi mobili. Viene visualizzato un messaggio che indica che sono presenti filtri attivi nella pagina.  

* Quando si seleziona un valore in un filtro dei dati nella pagina del report, vengono filtrati gli altri oggetti visivi nella pagina.
  
  ![Filtro dei dati del report](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  In questa illustrazione, il filtro dei dati filtra l'istogramma in modo da mostrare solo i valori di luglio.

## <a name="cross-filter-and-highlight-a-report"></a>Applicare un filtro incrociato ed evidenziare un report
Quando si seleziona un valore in un oggetto visivo, gli altri oggetti visivi non vengono filtrati, ma vengono evidenziati i valori correlati in altri oggetti visivi.

* Toccare un valore in un oggetto visivo.
  
  ![Filtro incrociato di una pagina](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Se si tocca la colonna Large in un grafico, vengono evidenziati i valori correlati negli altri oggetti visivi. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Ordinare un oggetto visivo in un iPad o un tablet
* Toccare il grafico, toccare i puntini di sospensione (**...**) e toccare il nome del campo.
  
   ![Ordinare un oggetto visivo](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* Per invertire l'ordinamento, toccare di nuovo i puntini di sospensione (**...**), quindi toccare di nuovo il nome dello stesso campo.

## <a name="drill-down-and-up-in-a-visual"></a>Eseguire il drill-down e il drill-up in un oggetto visivo
Se l'autore di un report ha aggiunto funzionalità di drill-down a un oggetto visivo, è possibile eseguire il drill-down nell'oggetto visivo per visualizzare i valori che ne fanno parte. È possibile [aggiungere il drill-down a un oggetto visivo](../../power-bi-visualization-drill-down.md) in Power BI Desktop o nel servizio Power BI. 

* Toccare e tenere premuto su una barra o un punto specifico in un oggetto visivo per visualizzare la descrizione comando. In caso di drill-down, la parte inferiore della descrizione comando contiene delle frecce che è possibile toccare. 
  
  ![Eseguire il drill-down in un oggetto visivo](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-tooltip.png)

* Per rieseguire il drill-up, toccare la freccia rivolta verso l'alto nella descrizione comando.
  
  ![Drill-up](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-tooltip.png)

* È anche possibile eseguire il drill-down in tutti i punti dati di un oggetto visivo. Aprire l'oggetto in modalità messa a fuoco, toccare l'icona Esplora, quindi scegliere Mostra tutto al livello successivo oppure espandere per visualizzare il livello corrente e successivo.

   ![Drill-down di tutti gli elementi di Power BI](./media/mobile-reports-in-the-mobile-apps/power-bi-drill-down-all.png)

## <a name="drill-through-from-one-page-to-another"></a>Eseguire il drill-through da una pagina all'altra

Con il *drill-through*, quando si tocca una parte specifica di un oggetto visivo, Power BI consente di passare a un'altra pagina nel report, filtrata in base al valore scelto. L'autore del report può definire una o più opzioni di drill-through che portano a pagine diverse. In tal caso, è possibile scegliere la pagina di cui eseguire il drill-through. Nell'esempio seguente quando si tocca il valore nel misuratore, è possibile scegliere di eseguire il drill-through in **spent by business area** o **planning by business area**.

![Report di drill-through di Power BI per dispositivi mobili](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-through-it-spent-report.png)

Quando si esegue il drill-through, il pulsante Indietro consente di tornare alla pagina del report precedente.

Leggere le informazioni su come [aggiungere il drill-through in Power BI Desktop](../../desktop-drillthrough.md).

## <a name="next-steps"></a>Passaggi successivi
* [Visualizzare e interagire con i report di Power BI ottimizzati per il proprio telefono](mobile-apps-view-phone-report.md)
* [Creare una versione di un report ottimizzata per i telefoni](../../desktop-create-phone-report.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

