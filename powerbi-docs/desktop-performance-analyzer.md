---
title: Usare l'analizzatore prestazioni per esaminare le prestazioni degli elementi del report in Power BI Desktop
description: Informazioni su come esaminare le prestazioni di oggetti visivi ed elementi del report in termini di utilizzo delle risorse e velocità di risposta
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8bbf391135442d6490033c0fc65b7372154820d2
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73866438"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Usare l'analizzatore prestazioni per esaminare le prestazioni degli elementi del report

In **Power BI Desktop** è possibile esaminare le prestazioni di tutti gli elementi del report, ad esempio oggetti visivi e formule DAX. L'**analizzatore prestazioni** consente di visualizzare e registrare log che misurano le prestazioni di ogni elemento del report durante l'interazione con gli utenti e di conoscere gli aspetti che usano più o meno risorse dal punto di vista delle prestazioni.

![Analizzatore prestazioni](media/desktop-performance-analyzer/performance-analyzer-01.png)

L'analizzatore prestazioni esamina e visualizza la durata necessaria per aggiornare tutti gli oggetti visivi avviati dalle interazioni utente e presenta le informazioni in modo che sia possibile visualizzare, eseguire il drill-down o esportare i risultati. L'analizzatore prestazioni consente di identificare gli oggetti visivi che incidono sulle prestazioni dei report e di identificarne il motivo.

## <a name="displaying-the-performance-analyzer-pane"></a>Visualizzazione del riquadro dell'analizzatore prestazioni

In **Power BI Desktop** selezionare la barra multifunzione **Visualizza**. Nell'area **Mostra** della barra multifunzione di **Visualizza** è possibile selezionare la casella di controllo accanto a **Analizzatore prestazioni** per visualizzare il riquadro dell'analizzatore prestazioni.

![Selezionare Analizzatore prestazioni nella barra multifunzione di Visualizza](media/desktop-performance-analyzer/performance-analyzer-02.png)

Quando selezionato, l'analizzatore prestazioni viene visualizzato nel relativo riquadro a destra dell'area di disegno report.

## <a name="using-performance-analyzer"></a>Uso dell'analizzatore prestazioni

Performance Analyzer misura il tempo di elaborazione (incluso il tempo necessario per creare o aggiornare un oggetto visivo) necessario per aggiornare gli elementi del report avviati in seguito a qualsiasi interazione dell'utente che comporta l'esecuzione di una query. La modifica di un filtro dei dati richiede, ad esempio, la modifica dell'oggetto visivo del filtro dei dati, l'invio di una query al modello di dati e la restituzione degli oggetti visivi interessati come risultato delle nuove impostazioni. 

Per avviare la registrazione nell'analizzatore prestazioni, è sufficiente selezionare **Avvia registrazione**.

![Avvia registrazione](media/desktop-performance-analyzer/performance-analyzer-03.png)

Tutte le azioni eseguite nel report vengono visualizzate e registrate nel riquadro dell'analizzatore prestazioni, nell'ordine in cui l'oggetto visivo viene caricato da Power BI. È, ad esempio, possibile avere un report il cui caricamento richiede molto tempo secondo quanto segnalato dagli utenti, oppure che la visualizzazione di determinati oggetti visivi in un report richieda molto tempo durante la regolazione di un dispositivo di scorrimento. L'analizzatore prestazioni può indicare l'oggetto visivo responsabile del rallentamento e identificare gli aspetti dell'oggetto visivo che richiedono più tempo per l'elaborazione. 

Dopo aver avviato la registrazione, il pulsante **Avvia registrazione** risulta inattivo perché la registrazione è già stata avviata, mentre il pulsante **Arresta** è attivo. 

L'analizzatore prestazioni raccoglie e visualizza le informazioni sulla misurazione delle prestazioni in tempo reale. Di conseguenza, ogni volta che si fa clic su un oggetto visivo, si sposta un filtro dei dati o si interagisce in altro modo, l'analizzatore prestazioni visualizza immediatamente i risultati delle prestazioni nel relativo riquadro.

Se il riquadro contiene una quantità di informazioni maggiore rispetto a quella visualizzabile, viene visualizzata una barra di scorrimento che consente di passare alle altre informazioni.

A ogni interazione è assegnato un identificatore di sezione nel riquadro, che descrive l'azione che ha avviato le registrazioni nel log. Nell'immagine seguente l'interazione si riferisce alla modifica di un filtro dei dati da parte degli utenti.

![Sezioni basate sul tipo di interazione](media/desktop-performance-analyzer/performance-analyzer-04.png)

Le informazioni del log di ogni oggetto visivo includono il tempo trascorso (durata) per completare le categorie di attività seguenti:

* **Query DAX**: se è stata richiesta una query DAX, indica il tempo che intercorre tra l'invio della query da parte dell'oggetto visivo e la restituzione dei risultati da parte di Analysis Services.
* **Visualizzazione oggetti visivi**: indica il tempo necessario per il disegno dell'oggetto visivo sullo schermo, incluso il tempo necessario per recuperare eventuali immagini Web o informazioni di geocodifica. 
* **Altro**: indica il tempo richiesto dall'oggetto visivo per la preparazione delle query, l'attesa del completamento di altri oggetti visivi o l'esecuzione di altre operazioni di elaborazione in background.

![Elementi delle informazioni del log](media/desktop-performance-analyzer/performance-analyzer-06.png)

Dopo avere interagito con gli elementi del report che si intende misurare con l'analizzatore prestazioni, è possibile selezionare il pulsante **Arresta**. Dopo aver selezionato **Arresta**, le informazioni sulle prestazioni continuano a essere visibili nel riquadro in modo che sia possibile analizzarle.

Per cancellare le informazioni nel riquadro dell'analizzatore prestazioni, selezionare **Cancella**. Quando si seleziona **Cancella**, tutte le informazioni vengono cancellate e non vengono salvate. Per informazioni su come salvare le informazioni nei log, vedere la sezione successiva. 

## <a name="refreshing-visuals"></a>Aggiornamento degli oggetti visivi

È possibile selezionare **Aggiorna gli oggetti visivi** nel riquadro dell'analizzatore prestazioni per aggiornare tutti gli oggetti visivi nella pagina corrente del report e quindi fare in modo che l'analizzatore prestazioni raccolga informazioni su tutti gli oggetti visivi.

È anche possibile aggiornare singoli oggetti visivi. Quando l'analizzatore prestazioni esegue la registrazione, è possibile selezionare l'opzione **Aggiorna questo oggetto visivo** presente nell'angolo in alto a destra destro di ogni oggetto visivo, per aggiornare l'oggetto visivo e acquisire le informazioni sulle prestazioni.

![Aggiornare un singolo oggetto visivo](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Salvataggio delle informazioni sulle prestazioni

Per salvare le informazioni relative a un report create dall'analizzatore prestazioni, selezionare il pulsante **Esporta**. Quando si seleziona **Esporta**, viene creato un file con estensione JSON contenente le informazioni del riquadro dell'analizzatore prestazioni. 

![Salvare il file di log per l'analizzatore prestazioni](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su **Power BI Desktop** e su come iniziare, vedere gli articoli seguenti.

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)   

