---
title: Usare cross-report drill-through in Power BI Desktop
description: Informazioni su come il drill-through da un report a un altro in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375201"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Usare cross-report drill-through in Power BI Desktop

Con la funzionalità di drill-through cross-report in Power BI Desktop, è possibile contestualmente passare da un report a un altro report. Ciò è vero, purché i report sono all'interno della stessa area di lavoro o app nel servizio di Microsoft Power BI. Usare cross-report drill-through per collegare due o più report che dispone di contenuto correlato e passare il contesto di filtro insieme alla connessione cross-report. In questo articolo descrive come configurare un cross-report di drill-through per i report di Power BI e cosa verificarsi quando gli utenti usano il cross-report drill-through per se stessi.

![Opzione di drill-through screenshot di Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Prima di iniziare l'installazione e utilizzo cross-report drill-through, sono importanti per comprendere le definizioni seguenti:

* **Visualizzazione di origine:** L'oggetto visivo che richiama l'azione di drill-through usando il menu di scelta rapida visual.
* **Report di origine:** Il report che contiene l'oggetto visivo di origine tra report drill-through.
* **Pagina di destinazione:** La pagina di un utente apre dopo l'avvio di un'azione drill-through.
* **Report di destinazione:** Il report che contiene la pagina di destinazione tra report drill-through.

## <a name="enable-cross-report-drillthrough"></a>Consenti drill-through cross-report

Per abilitare un report per essere la destinazione del drill-through tra report, è necessario abilitare la funzionalità per il report nel **opzioni** finestra. Passare a **File** > **opzioni e impostazioni** > **opzioni**, quindi passare a **impostazioni Report** quasi il nella parte inferiore della pagina a sinistra.

Selezionare il **consentire gli oggetti visivi in questo report per utilizzare destinazioni drill-through da altri report** casella di controllo, come illustrato nell'immagine seguente.

![Finestra di screenshot delle opzioni, con evidenziate le impostazioni di Report](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Cross-report drill-through è abilitato.

## <a name="set-up-cross-report-drillthrough"></a>Impostare il drill-through cross-report

Configurazione di cross-report drill-through è simile alla configurazione di drill-through in un report. Drill-through è abilitato nella pagina di destinazione, consentendo di altri oggetti visivi per la pagina abilitata per il drill-through di destinazione. Per i passaggi per creare drill-through all'interno di un singolo report, vedere [utilizzare il drill-through in Power BI Desktop](desktop-drillthrough.md).

Per avviare il processo di installazione, è necessario eseguire due passaggi iniziali:

* Consente di impostare una pagina di destinazione di drill-through, che è accessibile da altri report nell'area di lavoro o app.
* Consenti un report visualizzare le pagine di drill-through da all'esterno di un proprio report.

Cercare opzioni di drill-through nel **campi** sezione il **visualizzazioni** riquadro, come illustrato nell'immagine seguente.

![Riquadro schermata di visualizzazioni, con evidenziate le opzioni di drill-through](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Il primo passo per abilitare il drill-through per una pagina è per convalidare i modelli di dati per i report di origine e destinazione. Verificare quanto segue: 

* I campi che si desidera passare presenti nei modelli di dati.
* I nomi dei campi e i nomi delle tabelle a cui appartengono, sono identici (le stringhe deve inoltre corrispondere e tra maiuscole e minuscole).

Ad esempio, se si desidera passare un filtro nel campo *paese* all'interno di tabella *Geography*, entrambi modelli devono avere un *Geography* tabella e un *paese* campo all'interno di tale tabella. In caso contrario, è necessario aggiornare il nome del campo o il nome della tabella nel modello sottostante. È sufficiente aggiornare il nome visualizzato dei campi non funzionerà correttamente tra report drill-through. Si noti che non devono essere esattamente gli stessi schemi in ogni report.

Per iniziare a usare il programma di installazione, è necessario preparare la pagina di destinazione. In Power BI Desktop, passare alla pagina e assicurarsi che il **Cross-segnalazione** toggle di drill-through è impostata su **su**. 

![Schermata di attivazione/disattivazione Cross-report impostata su On](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Successivamente, trascinare i campi da usare come destinazione del drill-through nell'area di disegno. Selezionare se si desidera che il campo da usare come una categoria o riepilogati come una misura. A questo punto, è possibile selezionare se si desidera disabilitare la **mantenere tutti i filtri** attiva/disattiva per l'oggetto visivo. Se non si desidera passare altri filtri applicati dall'origine visual il drill-through di destinazione visual, selezionare **disattivata**.

> [!NOTE]
> Se si usa la pagina tra report drill-through solo, è necessario eliminare il **nuovamente** pulsante che viene aggiunto automaticamente. Il **nuovamente** pulsante funziona solo per nagivation all'interno di un singolo report. 

Dopo aver configurato l'oggetto visivo, verificare che si salva il report, se non ha nel servizio Power BI, oppure salvare e pubblicare il report se si usa Power BI Desktop.

La sezione precedente descrive come abilitare il drill-through cross-report per Power BI Desktop (nelle **opzioni** finestra). Se si usa il servizio Power BI per creare una destinazione tra report drill-through, per abilitare tra report drill-through è necessario: 

1. Selezionare l'area di lavoro in cui si trovano i report di destinazione e i report di origine.
2. Selezionare **report**.
3. Selezionare il **impostazioni** icona per il report di origine.
4. Assicurarsi che sia l'alternanza tra report drill-through **su**.
5. Salvare il report.

Questo è tutto. Il report è pronto per l'esperienza tra report drill-through. 

Nella sezione successiva, è esaminiamo l'esperienza dal punto di vista dell'utente.

## <a name="cross-report-drillthrough-experience"></a>Esperienza tra report drill-through

Quando si configura l'esperienza tra report drill-through per un report, è possibile inserire le funzionalità da usare.

Selezionare il report di origine nel servizio Power BI e quindi selezionare un oggetto visivo che usa il campo o campi nel modo specificato quando si configura la pagina di destinazione. Successivamente, fare doppio clic su un punto dati per aprire il menu di scelta rapida visual e selezionare **drill-through**.

![Screenshot del report di origine nel servizio Power BI, con evidenziati il drill-through](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Si noterà quindi i risultati nella pagina di drill-through cross-report di destinazione, come devono essere impostati durante la creazione di destinazione. I risultati vengono filtrati in base alle impostazioni di drill-through.

> [!IMPORTANT]
> Power BI memorizza nella cache di destinazioni tra report drill-through. Se si apportano modifiche, assicurarsi che aggiornare il browser se non viene visualizzato le destinazioni di drill-through come previsto. 

Destinazioni tra report vengono formattate nel modo seguente: 

`Target Page Name [Target Report Name]`

Dopo aver selezionato la pagina di destinazione a cui si desidera il drill-through, Power BI può essere a tale pagina. Passa il contesto di filtro basato sulle impostazioni della pagina di destinazione. 

Contesto di filtro dall'oggetto visivo di origine può includere quanto segue: 

* Report, pagina e filtri a livello di oggetto visivo che interessano l'oggetto visivo di origine. 
* Il filtro incrociato ed evidenziazione incrociata che interessano l'oggetto visivo di origine. 
* Filtri dei dati nella pagina e Sincronizza filtri dei dati.
* Parametri dell'URL.

Quando verrà visualizzato il report di destinazione per il drill-through, Power BI si applica solo per i campi per cui trova corrisponde alla stringa esatta per nome del campo e il nome di tabella. Power BI non applica filtri permanenti dal report di destinazione. È, tuttavia, applicabile il segnalibro personale predefinito se presente. Ad esempio, se il segnalibro personale predefinito include un filtro a livello di report per *Country = US*, Power BI applica prima di tutto che il filtro prima di applicare il contesto di filtro dall'oggetto visivo di origine. 

Drill-through tra report, Power BI passa il contesto di filtro a tutte le pagine standard nel report di destinazione. Power BI non soddisfa il contesto di filtro per le pagine di descrizione comando, perché le pagine di descrizione comando vengono filtrate in base alle oggetto visivo di origine che richiama la descrizione comando.

Se si vuole tornare al report di origine dopo l'azione di drill-through tra report, utilizzare il visualizzatore **nuovamente** pulsante. 

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Uso dei filtri dei dati in Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)

