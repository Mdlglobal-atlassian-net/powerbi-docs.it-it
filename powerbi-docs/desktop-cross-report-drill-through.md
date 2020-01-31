---
title: Usare il drill-through tra report in Power BI Desktop
description: Informazioni su come eseguire il drill-through da un report a un altro in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e500cb29bcc4472c59e7e8215fc0a7e7e728ea0d
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538854"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Usare il drill-through tra report in Power BI

Con la funzionalità di *drill-through tra report* di Power BI, è possibile passare contestualmente da un report a un altro nella stessa app o area di lavoro del servizio Power BI. È possibile usare il drill-through tra report per connettere due o più report con contenuto correlato e per passare il contesto di filtro insieme alla connessione tra i report. 

Per avviare il drill-through tra report, si seleziona un punto dati in un *oggetto visivo di origine* di un *report di origine* e quindi si seleziona la destinazione **Drill-through** tra report dal menu di scelta rapida. 

![Opzione Drill-through tra report di Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

L'azione di drill-through apre la *pagina di destinazione* nel *report di destinazione*. 

![Destinazione del drill-through tra report di Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

Questo articolo illustra come configurare e usare il drill-through tra report per i report di Power BI.

> [!NOTE]
> Non è possibile usare il drill-through tra i report con i singoli [report condivisi con l'utente corrente](service-share-dashboards.md#share-a-dashboard-or-report) in **Area di lavoro personale**. Per usare il drill-through tra report, è necessario accedere ai report nell'area di lavoro da cui sono stati condivisi.

## <a name="enable-cross-report-drillthrough"></a>Abilitare il drill-through tra report

Il primo passaggio per abilitare il drill-through tra report consiste nel convalidare i modelli di dati per i report di origine e di destinazione. Nonostante gli schemi in ogni report non debbano essere uguali, i campi che si vogliono passare devono esistere in entrambi i modelli di dati. I nomi dei campi e i nomi delle tabelle a cui appartengono devono essere identici. Le stringhe devono corrispondere e applicano la distinzione tra maiuscole e minuscole.

Ad esempio, se si vuole passare un filtro in un campo **State** all'interno di una tabella **US States**, entrambi i modelli devono avere una tabella **US States** e un campo **State** all'interno della tabella. Al contrario, è necessario aggiornare il nome di campo o il nome di tabella nel modello sottostante. Per il drill-through tra report non è sufficiente aggiornare il nome visualizzato dei campi.

Dopo aver convalidato i modelli, consentire al report di origine di usare il drill-through tra report. 

1. In Power BI Desktop passare a **File** > **Opzioni e impostazioni** > **Opzioni**. 
1. Nel riquadro di spostamento a sinistra nella finestra **Opzioni**, nella parte inferiore della sezione **File corrente** selezionare **Impostazioni report**. 
1. In basso a destra, in **Drill-through tra report** selezionare **Consentire agli oggetti visivi in questo report di usare destinazioni di drill-through di altri report**. 
1. Selezionare **OK**. 
   
   ![Abilitare il drill-through tra report in Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

È anche possibile abilitare il drill-through tra report dal servizio Power BI.
1. Nel servizio Power BI selezionare l'area di lavoro che contiene i report di destinazione e di origine.
1. Accanto al nome del report di origine nell'elenco dell'area di lavoro selezionare il simbolo **Altre opzioni** e quindi selezionare **Impostazioni**. 
1. Nella parte inferiore del riquadro **Impostazioni**, in **Drill-through tra report** selezionare **Consentire agli oggetti visivi in questo report di usare destinazioni di drill-through di altri report** e quindi selezionare **Salva**.
   
   ![Abilitare il drill-through tra report nel servizio Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Configurare una destinazione di drill-through tra report

La configurazione di una pagina di destinazione per il drill-through tra report è simile alla configurazione del drill-through in un report. L'abilitazione del drill-through nella pagina di destinazione consente ad altri oggetti visivi di usare la pagina come destinazione del drill-through. Per creare il drill-through all'interno di un singolo report, vedere [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md).

È possibile configurare una destinazione per il drill-through tra report in Power BI Desktop o nel servizio Power BI. 
1. Modificare il file di destinazione e nella pagina destinazione del report di destinazione selezionare la sezione **Campi** del riquadro **Visualizzazioni**. 
1. In **Drill-through** impostare l'interruttore **Tra report** su **Sì**. 
1. Trascinare i campi da usare come destinazioni del drill-through in **Aggiungere qui i campi di drill-through**. Per ogni campo, indicare se si vuole consentire il drill-through quando il campo viene usato come categoria o quando viene riepilogato come una misura. 
1. Se necessario, selezionare **Mantieni tutti i filtri** per l'oggetto visivo. Se non si vogliono passare all'oggetto visivo di destinazione i filtri applicati all'oggetto visivo di origine, selezionare **No**.
   
   ![Riquadro Visualizzazioni con le opzioni di drill-through evidenziate](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Se si usa la pagina solo per il drill-through tra report, eliminare il pulsante **Indietro** aggiunto automaticamente al canvas. Il pulsante **Indietro** funziona solo per la navigazione all'interno di un report. 
1. Dopo aver configurato la pagina di destinazione, salvare il report se si usa il servizio Power BI o salvare e pubblicare il report se si usa Power BI Desktop.

È tutto. I report sono pronti per il drill-through tra i report. 

## <a name="use-cross-report-drillthrough"></a>Usare il drill-through tra report

Per usare il drill-through tra report, selezionare il report di origine nel servizio Power BI, quindi selezionare un oggetto visivo in cui il campo di drill-through viene usato nel modo specificato durante la configurazione della pagina di destinazione. Fare clic con il pulsante destro del mouse su un punto dati per aprire il menu di scelta rapida dell'oggetto visivo, scegliere **Drill-through** e quindi selezionare la destinazione del drill-through. Le destinazioni dei drill-through tra report vengono formattate come **Nome pagina [nome report]** .

![Opzione Drill-through tra report di Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

I risultati vengono visualizzati nella pagina di drill-through tra report di destinazione, in base alle impostazioni specificate al momento della creazione della destinazione. I risultati sono filtrati in base alle impostazioni di drill-through.

![Destinazione del drill-through tra report di Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI memorizza nella cache le destinazioni di drill-through tra report. Se si apportano modifiche, assicurarsi di aggiornare il browser se le destinazioni di drill-through non vengono visualizzate come previsto. 

Se si imposta **Mantieni tutti i filtri** su **Sì** quando si configura la pagina di destinazione, il contesto di filtro dell'oggetto visivo di origine può includere gli elementi seguenti: 

- Filtri a livello di report, di pagina e di oggetti visivi che hanno effetto sull'oggetto visivo di origine 
- Filtro incrociato ed evidenziazione incrociata che hanno effetto sull'oggetto visivo di origine 
- Filtri dei dati e filtri dei dati di sincronizzazione nella pagina
- Parametri URL

Quando viene visualizzato il report di destinazione per il drill-through, Power BI applica solo i filtri per i campi con corrispondenze esatte per il nome del campo e il nome della tabella. 

Power BI non applica filtri permanenti dal report di destinazione, ma applica il segnalibro personale predefinito, se presente. Se ad esempio il segnalibro personale predefinito include un filtro a livello di report per *Country = US*, Power BI applica il filtro prima di applicare il contesto di filtro dell'oggetto visivo di origine. 

Per il drill-through tra report, Power BI passa il contesto di filtro alle pagine standard del report di destinazione. Power BI non passa il contesto di filtro per le pagine di descrizione comando poiché le pagine di descrizione comando vengono filtrate in base all'oggetto visivo di origine che richiama la descrizione comando.

Se si vuole tornare al report di origine dopo l'azione di drill-through tra report, usare il pulsante **Indietro** del browser. 

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

- [Filtri dei dati in Power BI](visuals/power-bi-visualization-slicers.md)
- [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)

