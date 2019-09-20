---
title: Usare il drill-through tra report in Power BI Desktop
description: Informazioni su come eseguire il drill-through da un report a un altro in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e735d45a7a49c4a0365e35d5bb95957c6145f934
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903765"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Usare il drill-through tra report in Power BI Desktop

Con la funzionalità di drill-through tra report in Power BI Desktop, è possibile passare contestualmente da un report a un altro. Questa condizione è valida purché i report si trovino all'interno della stessa area di lavoro o dell'app nel servizio Power BI. Utilizzare il drill-through tra report per connettere due o più report con contenuto correlato e per passare il contesto di filtro insieme alla connessione tra i report. In questo articolo viene illustrato come configurare un drill-through tra report per i report Power BI e viene descritta l'esperienza degli utenti che usano il drill-through tra report.

![Screenshot dell'opzione di drill-through di Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

È importante comprendere le definizioni seguenti prima di iniziare a configurare e a usare il drill-through tra report:

* **Oggetto visivo di origine:** oggetto visivo che richiama l'azione di drill-through tramite il menu di scelta rapida visivo.
* **Report di origine:** report che contiene l'oggetto visivo di origine per il drill-through tra report.
* **Pagina di destinazione:** pagina visualizzata all'utente dopo l'avvio di un'azione di drill-through.
* **Report di destinazione:** report che contiene la pagina di destinazione per il drill-through tra report.


> [!NOTE]
> È possibile accedere ai report condivisi singolarmente in *Area di lavoro personale*, ovvero ai report visualizzati come *[Condivisi con l'utente corrente](service-share-dashboards.md#share-a-dashboard-or-report)* , solo nell'area di lavoro da cui sono stati originariamente condivisi. 


## <a name="enable-cross-report-drillthrough"></a>Abilitare il drill-through tra report

Per impostare un report come destinazione di un drill-through tra report, è necessario abilitare la funzionalità per il report nella finestra **Opzioni**. Passare a **File** > **Opzioni e impostazioni** > **Opzioni** e quindi a **Impostazioni report** nella parte inferiore della pagina a sinistra.

Selezionare la casella di controllo **Consentire agli oggetti visivi in questo report di usare destinazioni di drill-through di altri report** come illustrato nell'immagine seguente.

![Screenshot della finestra Opzioni con l'opzione Impostazioni report evidenziata](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Il drill-through tra report è ora abilitato.

## <a name="set-up-cross-report-drillthrough"></a>Configurare il drill-through tra report

La configurazione del drill-through tra report è simile alla configurazione del drill-through in un report. Il drill-through è abilitato nella pagina di destinazione, consentendo ad altri oggetti visivi di usare la pagina abilitata come destinazione del drill-through. Per le procedure per la creazione di drill-through all'interno di un singolo report, vedere [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md).

Per avviare il processo di configurazione, è necessario eseguire un paio di passaggi iniziali:

* Configurare una pagina di destinazione del drill-through a cui sarà possibile accedere da altri report nell'area di lavoro o nell'app.
* Consentire a un report di visualizzare le pagine di drill-through dall'esterno del report.

Le opzioni di drill-through sono disponibili nella sezione **Campi** del riquadro **Visualizzazioni**, come illustrato nell'immagine seguente.

![Screenshot del riquadro Visualizzazioni con le opzioni di drill-through evidenziate](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Il primo passaggio per abilitare il drill-through per una pagina consiste nel convalidare i modelli di dati per i report di origine e di destinazione. Assicurarsi che: 

* I campi che si vuole passare siano presenti in entrambi i modelli di dati.
* I nomi dei campi e i nomi delle tabelle a cui appartengono sono identici (le stringhe devono anche corrispondere e fanno distinzione tra maiuscole e minuscole).

Ad esempio, se si vuole passare un filtro nel campo *Paese* all'interno della tabella *Geografia*, entrambi i modelli devono avere una tabella *Geografia* e un campo *Paese* all'interno della tabella. Al contrario, è necessario aggiornare il nome di campo o il nome di tabella nel modello sottostante. Per il drill-through tra report non è sufficiente aggiornare il nome visualizzato dei campi. Si noti che gli schemi di ogni report non devono corrispondere esattamente.

Per iniziare la configurazione, è necessario preparare la pagina di destinazione. In Power BI Desktop passare alla pagina e verificare che l'opzione di drill-through **Tra report** sia impostata su **Attivato**. 

![Screenshot dell'opzione Tra report impostata su Attivato](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Trascinare quindi i campi che si vuole usare come destinazione di drill-through nell'area di disegno. Specificare se si vuole che il campo venga usato come categoria o riepilogato come misura. A questo punto, è possibile specificare se si vuole disabilitare l'opzione **Mantieni tutti i filtri** per l'oggetto visivo. Se non si vuole passare altri filtri applicati dall'oggetto visivo di origine all'oggetto visivo di drill-through di destinazione, selezionare **Disattivato**.

> [!NOTE]
> Se si usa la pagina solo per il drill-through tra report, è necessario eliminare il pulsante **Indietro** aggiunto automaticamente. Il pulsante **Indietro** funziona solo per la navigazione all'interno di un singolo report. 

Dopo aver configurato l'oggetto visivo, assicurarsi di salvare il report se si usa il servizio Power BI o di salvare e pubblicare il report se si usa Power BI Desktop.

Nella sezione precedente è stato descritto come abilitare il drill-through tra report per Power BI Desktop (nella finestra **Opzioni**). Se si usa il servizio Power BI per creare una destinazione di drill-through tra report, per abilitare il drill-through tra report è necessario: 

1. Selezionare l'area di lavoro in cui si trovano il report di destinazione e il report di origine.
2. Selezionare **Report**.
3. Selezionare l'icona **Impostazioni** per il report di origine.
4. Verificare che l'opzione di drill-through tra report sia impostata su **Attivato**.
5. Salvare il report.

Questo è tutto. Il report è pronto per l'esperienza di drill-through tra report. 

Nella sezione successiva l'esperienza verrà esaminata dal punto di vista dell'utente.

## <a name="cross-report-drillthrough-experience"></a>Esperienza di drill-through tra report

Quando si configura l'esperienza di drill-through tra report per un report, è possibile specificare la funzionalità da usare.

Selezionare il report di origine nel servizio Power BI, quindi selezionare un oggetto visivo in cui il campo o i campi vengono usati nel modo specificato durante la configurazione della pagina di destinazione. Quindi fare clic con il pulsante destro del mouse su un punto dati per aprire il menu di scelta rapida visivo e selezionare **Drill-through**.

![Screenshot del report di origine nel servizio Power BI con l'opzione Drill-through evidenziata](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

I risultati verranno quindi visualizzati nella pagina di drill-through tra report di destinazione, in base alle impostazioni specificate al momento della creazione della destinazione. I risultati sono filtrati in base alle impostazioni di drill-through.

> [!IMPORTANT]
> Power BI memorizza nella cache le destinazioni di drill-through tra report. Se si apportano modifiche, assicurarsi di aggiornare il browser se le destinazioni di drill-through non vengono visualizzate come previsto. 

Le destinazioni tra report sono formattate nel modo seguente: 

`Target Page Name [Target Report Name]`

Dopo aver selezionato la pagina di destinazione del drill-through, Power BI passa alla pagina. Power BI passa anche il contesto di filtro in base alle impostazioni della pagina di destinazione. 

Il contesto di filtro dell'oggetto visivo di origine può includere gli elementi seguenti: 

* Filtri a livello di report, di pagina e di oggetti visivi che hanno effetto sull'oggetto visivo di origine. 
* Filtro incrociato ed evidenziazione incrociata che hanno effetto sull'oggetto visivo di origine. 
* Filtri dei dati nella pagina e filtri dei dati di sincronizzazione.
* Parametri URL.

Quando viene visualizzato il report di destinazione per il drill-through, Power BI applica solo i filtri per i campi per i quali trova corrispondenze esatte per il nome del campo e il nome della tabella. Power BI non applica i filtri permanenti del report di destinazione. Viene tuttavia applicato il segnalibro personale predefinito, se disponibile. Ad esempio, se il segnalibro personale predefinito include un filtro a livello di report per *Paese = US*, Power BI applica il filtro prima di applicare il contesto di filtro dell'oggetto visivo di origine. 

Per il drill-through tra report, Power BI passa il contesto di filtro a tutte le pagine standard del report di destinazione. Power BI non passa il contesto di filtro per le pagine di descrizione comando poiché le pagine di descrizione comando vengono filtrate in base all'oggetto visivo di origine che richiama la descrizione comando.

Se si vuole tornare al report di origine dopo l'azione di drill-through tra report, usare il pulsante **Indietro** del browser. 

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Uso dei filtri dei dati in Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)

