---
title: Visualizzazione report in Power BI Desktop
description: Visualizzazione report in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 153a77cdc7d4749ac450378723d04c82ef938de6
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514618"
---
# <a name="report-view-in-power-bi-desktop"></a>Visualizzazione report in Power BI Desktop
Se si usa già Power BI, si saprà già quanto sia facile creare report che offrono prospettive dinamiche e informazioni dettagliate sui dati. Power BI include però funzionalità più avanzate in Power BI Desktop. Grazie a Power BI Desktop è infatti possibile creare query avanzate, combinare dati di più origini, creare relazioni tra tabelle e altro ancora.

Power BI Desktop include **Visualizzazione report**, in cui è possibile creare un numero qualsiasi di pagine di report con visualizzazioni. e che offre un'esperienza di progettazione analoga a quella della Visualizzazione di modifica di un report nel servizio Power BI, consentendo di spostare le visualizzazioni, nonché di copiare e incollare, unire e così via.

La differenza tra le due visualizzazioni è che quando si usa Power BI Desktop è possibile lavorare con le query e modellare i dati, per ottenere, con i dati, informazioni dettagliate di migliore qualità nei report. Il file di Power BI Desktop può quindi essere salvato in qualsiasi posizione dell'unità locale o del cloud.

## <a name="lets-take-a-look"></a>Operazioni di base
Quando si caricano i dati in Power BI Desktop per la prima volta, **Visualizzazione report** contiene un'area di disegno vuota.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Per spostarsi tra **Visualizzazione report**, **Visualizzazione dati** e **Visualizzazione relazioni** selezionare le icone nella barra di spostamento a sinistra:

![Icona Visualizzazione report](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Dopo avere aggiunto alcuni dati, è possibile aggiungere campi a una nuova visualizzazione nell'area di disegno.

![Aggiungere un oggetto visivo trascinandolo dal riquadro Campi](media/desktop-report-view/pbid_reportview_addvis.gif)

Per cambiare il tipo di visualizzazione, selezionarlo nel gruppo **Visualizzazioni** della barra multifunzione oppure fare clic con il pulsante destro del mouse e scegliere un tipo diverso tramite l'icona **Cambia tipo di visualizzazione**.

![Cambiare un oggetto visivo selezionandone uno nuovo](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Esaminare i vari tipi di visualizzazione disponibili. È infatti importante che la visualizzazione scelta consenta di trasmettere chiaramente le informazioni presenti nei dati.

Un report includerà almeno una pagina vuota per iniziare. Le pagine vengono visualizzate nel pannello di navigazione a sinistra dell'area di disegno. È possibile aggiungere a una pagina tutti i tipi di visualizzazione: l'importante è non esagerare. Un numero eccessivo di visualizzazioni in un'unica pagina può infatti rendere quest'ultima poco chiara e impedire l'individuazione delle informazioni corrette. È possibile aggiungere nuove pagine al report. Fare clic su **Nuova pagina** nella barra multifunzione.

![Icona Nuova pagina](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Per eliminare una pagina, fare clic sulla **X** nella scheda della pagina nella parte inferiore della Visualizzazione report.

![Aggiungere una nuova pagina a un report](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Non è possibile aggiungere report e visualizzazioni in un dashboard da Power BI Desktop. A tale scopo, è necessario [pubblicare da Power BI Desktop](desktop-upload-desktop-files.md) nel sito di Power BI.

## <a name="copy-and-paste-between-reports"></a>Copiare e incollare tra i report

È facilmente possibile prendere un oggetto visivo da un report di Power BI Desktop e incollarlo in un altro report. È sufficiente usare la scelta rapida da tastiera **CTRL+C** per copiare l'oggetto visivo del report, quindi usare **CTRL+V** nell'altro report di Power BI Desktop per incollarvi l'oggetto visivo. È possibile selezionare un singolo oggetto visivo alla volta oppure è possibile selezionare tutti gli oggetti visivi in una pagina per copiarli, quindi incollarli nel report di Power BI Desktop di destinazione. 

La possibilità di copiare e incollare gli oggetti visivi è utile per chi compila e aggiorna frequentemente più report. Quando si esegue la copia tra file, le impostazioni e la formattazione impostate in modo esplicito nel riquadro di formattazione verranno riportate, mentre gli oggetti visivi basati su un tema o sulle impostazioni predefinite vengono aggiornati automaticamente in modo che corrispondano al tema del report di destinazione. Pertanto, quando si crea un oggetto visivo con la formattazione e l'aspetto desiderati, è possibile copiarlo e incollarlo in nuovi report e conservare la formattazione valida.

![Errore durante l'operazione di copia/incolla dell'oggetto visivo: nessun campo dati](media/desktop-report-view/report-view_05.png)

Se i campi nel modello sono diversi, verranno visualizzati un errore relativo all'oggetto visivo e un avviso sui campi inesistenti. L'errore è simile all'esperienza visualizzata quando si elimina un campo nel modello usato da un oggetto visivo. Per correggere l'errore, è sufficiente sostituire i campi interrotti con i campi che si vuole usare dal modello nel report in cui è stato incollato l'oggetto visivo. Se si usa un oggetto visivo personalizzato, è anche necessario importare tale oggetto visivo personalizzato nel report di destinazione.




## <a name="hide-report-pages"></a>Nascondere pagine dei report

Quando si crea un report, è anche possibile nascondere pagine. Ciò può essere utile se è necessario creare i dati o gli oggetti visivi sottostanti per un report, ma non si vuole che queste pagine siano visibili per altri utenti, ad esempio quando si creano tabelle oppure oggetti visivi di supporto che vengono usati in altre pagine del report. Esistono molti altri motivi creativi per cui può essere necessario creare una pagina di report per poi nasconderla nel report da pubblicare. 

È facile nascondere una pagina di un report. È sufficiente fare clic con il pulsante destro del mouse sulla scheda della pagina del report e scegliere **Nascondi** dal menu visualizzato.

![Opzione Nascondi pagina](media/desktop-report-view/report-view_05.png)

Esistono alcune considerazioni da tenere presenti quando si nasconde una pagina di un report:

* È comunque possibile visualizzare un pagina di report nascosta in **Power BI Desktop**, anche se il titolo della pagina è in grigio. Nella figura seguente, la pagina 4 è nascosta.

    ![Pagina inattiva nascosta](media/desktop-report-view/report-view_06.png)

* *Non* è possibile visualizzare una pagina del report nascosta, quando il report viene aperto nel **servizio Power BI**.

* Nascondere una pagina di un report *non* è una misura di sicurezza. La pagina rimane comunque accessibile per gli utenti e il relativo contenuto è ancora accessibile tramite drill-through e altri metodi.

* Quando una pagina è nascosta, in modalità di visualizzazione non viene visualizzata alcuna freccia di navigazione.

