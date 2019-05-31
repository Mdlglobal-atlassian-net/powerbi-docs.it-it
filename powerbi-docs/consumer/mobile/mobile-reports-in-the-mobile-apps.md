---
title: Esplorare i report nelle app Power BI per dispositivi mobili
description: Informazioni sulla visualizzazione e sull'interazione con i report nelle app Power BI nel telefono o nel tablet. Creare report nel servizio Power BI o Power BI Desktop, quindi interagire con essi nelle app per dispositivi mobili.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/21/2019
ms.author: mshenhav
ms.openlocfilehash: bee60dd6f3254b049f2445e6e985c625933caf5b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565530"
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

In elenchi e i menu, si noterà un'icona accanto a un nome di report, consentendo di comprendere che questo elemento è un report. 

![report nell'area di lavoro](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png) 

Sono presenti due icone per i report nelle App Power BI per dispositivi mobili:

* ![Icona del report](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) indica un report che verrà visualizzato con orientamento orizzontale nell'app e avranno lo stesso aspetto come si presenta nel browser.

* ![Icona di rapporto telefono](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) indica un report che include almeno una pagina di report ottimizzato phone, che verrà visualizzata in verticale. 

Nota: Mantenendo il telefono in orizzontale, si otterranno sempre il layout verticale, anche se la pagina del report dispone di layout del telefono. 

Per visualizzare un report da un dashboard, toccare i puntini di sospensione (...) nell'angolo superiore destro di un riquadro > **aprire report**.
  
  ![Apri report](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Non tutti i riquadri offrono l'opzione di apertura in un report. Ad esempio, i riquadri creati ponendo una domanda nella casella Domande e risposte non aprono i report quando vengono toccati. 
  
## <a name="interacting-with-reports"></a>Interagire con i report
Dopo aver creato un report aperto nell'app, è possibile iniziare a utilizzarlo. Esistono molti aspetti che è possibile eseguire con i report e i relativi dati. Nel piè di pagina report sono disponibili azioni che è possibile eseguire il report e toccando e se si tocca lungo i dati visualizzati nel report è possibile anche suddividere e ripartire i dati.

### <a name="using-tap-and-long-tap"></a>Usando toccare e durata
Fare clic su TAP uguale a quando il mouse. Pertanto, se si desidera eseguire l'evidenziazione incrociata il report in base a un punto dati, toccare su tale punto dati.
Toccare un valore di filtro dei dati, rende tale valore selezionato e il resto del report di sezionamento per tale valore. Se si tocca un collegamento, pulsante o un segnalibro verrà attivarlo in base all'azione definito dall'autore.

Si sarà probabilmente notato che quando toccano in un oggetto visivo, viene visualizzato un bordo. Nell'angolo superiore destro del bordo, sono i puntini di sospensione (...). Se tocchi su di esso verranno visualizzato un menu con operazioni che possono essere eseguite su tale oggetto visivo.

![oggetto visivo del report e menu](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Azioni di Drill e della descrizione comando

Quando si prolungata tocca (toccare e tenere premuto) un punto dati, una descrizione comando verrà visualizzata la presentazione di punto dati rappresenta i valori. 

![descrizione comando del report](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Gli autori di report è possono definire le gerarchie nei dati e le relazioni tra le pagine del report. Gerarchia consente il drill-down, drill backup e il drill-through da un oggetto visivo e un valore di un'altra pagina del report. Pertanto, quando si tocca prolungata su un valore, oltre alla descrizione comandi, le opzioni di drill rilevante verranno visualizzato nel piè di pagina. 

![segnalare azioni di drill](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)

Con il *drill-through*, quando si tocca una parte specifica di un oggetto visivo, Power BI consente di passare a un'altra pagina nel report, filtrata in base al valore scelto.  L'autore del report può definire una o più opzioni di drill-through che portano a pagine diverse. In tal caso, è possibile scegliere la pagina di cui eseguire il drill-through. Il pulsante Indietro consente di tornare alla pagina del report precedente.

Leggere le informazioni su come [aggiungere il drill-through in Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > Nell'app Power BI per dispositivi mobili, drill negli oggetti visivi tabella e matrice è abilitato tramite un solo valore di cella e non da intestazioni di riga e colonna.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Usare le azioni nel piè di pagina report
Il piè di pagina del report sono disponibili azioni che è possibile eseguire nella pagina del report corrente o per l'intero report. Il piè di pagina ha un accesso rapido alle azioni più utili e tutte le azioni sono accessibili i puntini di sospensione (...).

![piè di pagina report](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Le azioni che eseguibili nel piè di pagina sono:
1) Tra le selezioni di evidenziazione allo stato originale e reimpostare il filtro di report.
2) Aprire il riquadro di conversazione per visualizzare o aggiungere commenti su questo report.
3) Aprire il riquadro filtro per visualizzare e modificare il filtro correntemente applicato nel report.
4) Elencare tutte le pagine di questo report. Se si tocca il nome di pagina verrà caricato e presentare tale pagina.
Lo spostamento tra pagine del report è possibile scorrendo rapidamente dal bordo dello schermo al centro.
5) Consente di visualizzare tutte le azioni report.

#### <a name="all-report-actions"></a>Tutte le azioni report
Toccando il... Seleziona l'opzione nel piè di pagina report, consentiranno di elaborare tutte le azioni che eseguibili in un report. 

![tutte le azioni report](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Alcune delle azioni potrebbe disabilitare, poiché dipendono le funzionalità di report specifico.
ad esempio:
1) **Filtra per località corrente** è abilitato se i dati nel report è stati categorizzati dall'autore con i dati geografici. [Informazioni su come identificare i dati geografici nel report](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).
2) **Analisi per filtrare il report dal codice a barre** è abilitata solo se il set di dati nel report è stato contrassegnato come codice a barre. [Come si contrassegnare codici a barre in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes). 
3) **Invitare** è abilitata solo se si è autorizzati a condividere questo report con altri utenti. Hai l'autorizzazione solo se si è proprietari del report o se assegnato dal proprietario delle autorizzazioni di ricondivisione.
4) **Aggiungere annotazioni e condividere** potrebbe essere disable se è presente un' [criteri di protezione Intune](https://docs.microsoft.com/intune/app-protection-policies) nell'organizzazione che vietata la condivisione dall'app Power BI per dispositivi mobili. 

## <a name="next-steps"></a>Passaggi successivi
* [Visualizzare e interagire con i report di Power BI ottimizzati per il proprio telefono](mobile-apps-view-phone-report.md)
* [Creare una versione di un report ottimizzata per i telefoni](../../desktop-create-phone-report.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

