---
title: Utilizzare Performance Analyzer per esaminare le prestazioni di elemento di report in Power BI Desktop
description: Scoprire la modalità di esecuzione di oggetti visivi ed elementi del report in termini di velocità di risposta e dell'utilizzo delle risorse
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854414"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Utilizzare Performance Analyzer per esaminare le prestazioni di elemento di report

Nelle **Power BI Desktop** è possibile trovare ognuno degli elementi del report, ad esempio gli oggetti visivi e le formule DAX, prestazioni delle istanze. Usando il **Performance Analyzer**, è possibile visualizzare e record di log che misura come ognuno degli elementi del report esegue quando gli utenti interagiscono con essi, e gli aspetti delle loro prestazioni utilizzano molte risorse la maggior parte delle (o meno).

![Analizzatore prestazioni](media/desktop-performance-analyzer/performance-analyzer-01.png)

Performance Analyzer analizza e visualizza l'intervallo di tempo necessario per l'aggiornamento o l'aggiornamento di tutti gli oggetti visivi che avviare le interazioni dell'utente e presenta le informazioni in modo che è possibile visualizzare, eseguire il drill-o esportare i risultati. Analizzatore prestazioni consente di identificare gli oggetti visivi che incidono sulle prestazioni dei report e identificare il motivo per l'impatto.

## <a name="displaying-the-performance-analyzer-pane"></a>Visualizzazione del riquadro Performance Analyzer

Nelle **Power BI Desktop** selezionare la **visualizzazione** della barra multifunzione. Nel **mostrare** area della **vista** della barra multifunzione è possibile selezionare la casella di controllo accanto a **Performance Analyzer** per visualizzare il riquadro Performance Analyzer.

![Selezionare Performance analyzer nella barra multifunzione Visualizza](media/desktop-performance-analyzer/performance-analyzer-02.png)

Una volta selezionata, l'analizzatore delle prestazioni viene visualizzato in un proprio riquadro a destra dell'area di disegno report.

## <a name="using-performance-analyzer"></a>Tramite Performance Analyzer

Le misurazioni di Analizzatore prestazioni il tempo di elaborazione (incluso il tempo necessario per creare o aggiornare un oggetto visivo) necessario per aggiornare gli elementi di report avviati in seguito a alcuna interazione dell'utente che risulta in esecuzione una query. La regolazione di un filtro dei dati, ad esempio, richiede l'oggetto visivo di filtro dei dati da modificare, una query da inviare al modello di dati e oggetti visivi interessati che devono essere aggiornati in seguito le nuove impostazioni. 

Per iniziare a registrare Performance Analyzer, selezionare semplicemente **avviare la registrazione**

![Avvia registrazione](media/desktop-performance-analyzer/performance-analyzer-03.png)

Qualsiasi azione eseguita nel report vengono visualizzati e registrati nel riquadro Performance Analyzer, nell'ordine che l'oggetto visivo venga caricato da Power BI. Ad esempio, forse disponibile un report che gli utenti hanno detto richiede molto tempo per aggiornare. O alcuni oggetti visivi in un report richiedono molto tempo da visualizzare quando viene modificato un dispositivo di scorrimento. Analizzatore prestazioni può indicare che è l'oggetto visivo è la causa del problema e identifica quali aspetti dell'oggetto visivo sta richiedendo la durata più lunga per l'elaborazione. 

Dopo aver avviato la registrazione, il **avviare la registrazione** diventa inattivo out (inattivo, poiché si è già avviata la registrazione) e il **arrestare** pulsante è attivo. 

Analizzatore prestazioni raccoglie e visualizza le informazioni di misurazione delle prestazioni in tempo reale. Pertanto ogni volta che si fa clic su un oggetto visivo, spostare un filtro dei dati o interagire in altro modo, Performance Analyzer visualizza immediatamente i risultati delle prestazioni nel relativo riquadro.

Se il riquadro ha altre informazioni che possono essere visualizzate, viene visualizzata una barra di scorrimento per passare a informazioni aggiuntive.

Ogni interazione ha un identificatore di sezione nel riquadro, che descrive l'azione che ha avviato le voci di log. Nell'immagine seguente, l'interazione è che gli utenti di modifichino un filtro dei dati.

![Sezioni in base al tipo di interazione](media/desktop-performance-analyzer/performance-analyzer-04.png)

Le informazioni sul log di ogni dell'oggetto visivo include il tempo impiegato (durata) per completare le seguenti categorie di attività:

* **Query DAX** -se una query DAX è obbligatoria, questo è il tempo tra l'oggetto visivo inviando la query e per Analysis Services restituire i risultati.
* **Rappresentazione visiva** -tempo necessario per l'oggetto visivo disegnare sullo schermo, inclusi tempo richiesto per recuperare le immagini di web o la geocodifica. 
* **Altri** -tempo richiesto dall'oggetto visivo per la preparazione di query, in attesa di altri oggetti visivi completare o eseguire altre elaborazioni in background.

![elementi di informazioni di log](media/desktop-performance-analyzer/performance-analyzer-06.png)

Dopo che è stata ha interagito con elementi del report che si desidera misurare con Performance Analyzer, è possibile selezionare i **arrestare** pulsante. Le informazioni sulle prestazioni rimangono nel riquadro dopo aver selezionato **arrestare** analisi.

Per cancellare le informazioni contenute nel riquadro di Performance Analyzer, selezionare **cancellare**. Tutte le informazioni vengono cancellate e non viene salvate quando si seleziona **chiaro**. Vedere la sezione successiva per informazioni su come salvare le informazioni nei log. 

## <a name="refreshing-visuals"></a>L'aggiornamento di oggetti visivi

È possibile selezionare **Aggiorna gli oggetti visivi** nel riquadro Performance Analyzer per aggiornare tutti gli oggetti visivi nella pagina corrente del report e in tal modo sono Performance Analyzer raccogliere informazioni su tutti questi oggetti visivi.

È anche possibile aggiornare i singoli oggetti visivi. Quando si sta registrando Performance Analyzer, è possibile selezionare **aggiornare questo oggetto visivo** nell'angolo superiore destro di ogni oggetto visivo, tale oggetto visivo, aggiornare e acquisire le informazioni sulle prestazioni.

![aggiornare un singolo oggetto visivo](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Salvataggio delle informazioni sulle prestazioni

È possibile salvare le informazioni che Performance Analyzer consente di creare un report selezionando il **esportare** pulsante. Selezionando **esportare** crea un file con estensione JSON con informazioni dal riquadro Performance Analyzer. 

![Salvare il file di log per l'analizzatore delle prestazioni](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su **Power BI Desktop** e su come iniziare, vedere gli articoli seguenti.

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)   

