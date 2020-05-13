---
title: Usare il motore di calcolo avanzato con i flussi di dati
description: Informazioni su come usare il motore di calcolo avanzato in Power BI Premium con i flussi di dati
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e126451bf016bf4e9dcce7b7a4df51db9ed20386
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320516"
---
# <a name="the-enhanced-compute-engine"></a>Motore di calcolo avanzato

Il motore di calcolo avanzato in Power BI consente ai sottoscrittori di Power BI Premium di usare la propria capacità per ottimizzare l'uso dei flussi di dati. L'uso del motore di calcolo avanzato offre i vantaggi seguenti:

* Riduzione drastica del tempo di aggiornamento necessario per i passaggi ETL (estrazione, trasformazione e caricamento ) con esecuzione prolungata sulle entità calcolate, ad esempio l'esecuzione di operazioni *join*, *distinct*, *filter* e *group by*
* Esecuzione di query DirectQuery sulle entità (a febbraio 2020)

Le sezioni seguenti descrivono come abilitare il motore di calcolo avanzato e rispondono alle domande più comuni.


## <a name="using-the-enhanced-compute-engine"></a>Uso del motore di calcolo avanzato

È possibile abilitare il motore di calcolo avanzato nella pagina **Impostazioni di capacità** del servizio Power BI, nella sezione **Flussi di dati**. L'impostazione predefinita per il motore di calcolo avanzato è **No**. Per attivarlo, impostare l'opzione su **Sì** come illustrato nell'immagine seguente e salvare le impostazioni. 

![Attivare il motore di calcolo avanzato](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

Una volta attivato il motore di calcolo avanzato, tornare ai flussi di dati e si riscontrerà un miglioramento delle prestazioni in qualsiasi entità calcolata che esegue operazioni complesse, ad esempio operazioni *join* o *group by*, per i flussi di dati creati da entità collegate esistenti nella stessa capacità. 

Per sfruttare al meglio il motore di calcolo, è necessario suddividere la fase ETL in due flussi di dati separati nel modo seguente:

* **Flusso di dati 1**: questo flusso di dati deve solo inserire tutti i dati richiesti da un'origine dati e posizionarli nel flusso di dati 2.
* **Flusso di dati 2**: eseguire tutte le operazioni ETL in questo secondo flusso di dati, ma assicurarsi di fare riferimento al flusso di dati 1, che si deve trovare nella stessa capacità. Assicurarsi inoltre di eseguire le operazioni di tipo fold (filter, group by, distinct, join) prima di qualsiasi altra operazione, per garantire che il motore di calcolo venga utilizzato.

## <a name="common-questions-and-answers"></a>Domande frequenti e risposte

**Domanda:** Dopo aver abilitato il motore di calcolo avanzato, gli aggiornamenti sono più lenti. Perché?

**Risposta:** Se si abilita il motore di calcolo avanzato, ci sono due possibili spiegazioni per il rallentamento dei tempi di aggiornamento:

 - Quando il motore di calcolo avanzato è abilitato, richiede una certa quantità di memoria per funzionare correttamente. Di conseguenza, la memoria disponibile per l'esecuzione di un aggiornamento è ridotta e quindi aumenta la probabilità che gli aggiornamenti vengano accodati, riducendo di conseguenza il numero di flussi di dati che possono essere aggiornati contemporaneamente. Per risolvere questo problema, quando si abilita il calcolo avanzato, aumentare la memoria assegnata ai flussi di dati per garantire che la memoria disponibile per gli aggiornamenti contemporanei dei flussi di dati rimanga invariata.

 - Un'altra possibile causa del rallentamento degli aggiornamenti è che il motore di calcolo funziona solo sulle entità esistenti e se il flusso di dati fa riferimento a un'origine dati che non è un flusso di dati, non si riscontrerà alcun miglioramento. Non ci sarà un aumento delle prestazioni, poiché in alcuni scenari di Big Data la lettura iniziale da un'origine dati risulta più lenta, in quanto i dati devono essere passati al motore di calcolo avanzato.  

**Domanda:** L'opzione di attivazione/disattivazione del motore di calcolo avanzato non è visibile. Perché?

**Risposta:** Il rilascio del motore di calcolo avanzato sta avvenendo per fasi nelle diverse aree di tutto il mondo. Si prevede che il supporto sarà disponibile in tutte le aree entro la fine del 2020.

**Domanda:** Quali sono i tipi di dati supportati per il motore di calcolo?

**Risposta:** Il motore di calcolo avanzato e i flussi di dati attualmente supportano i tipi di dati seguenti. Se il flusso di dati non usa uno dei tipi di dati seguenti, si verifica un errore durante l'aggiornamento:

* Data/ora
* Numero decimale
* Text
* Numero intero
* Data/ora/fuso orario
* True/False
* Data
* Tempo

## <a name="next-steps"></a>Passaggi successivi

In questo articolo sono state fornite informazioni sull'uso del motore di calcolo avanzato per i flussi di dati. Anche gli articoli seguenti possono risultare utili:

* [Preparazione dei dati self-service con flussi di dati](service-dataflows-overview.md)
* [Creare e usare flussi di dati in Power BI](service-dataflows-create-use.md)
* [Uso delle entità calcolate in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Risorse per sviluppatori per i flussi di dati Power BI](service-dataflows-developer-resources.md)

Per altre informazioni su Power Query e sull'aggiornamento pianificato, è possibile leggere questi articoli:
* [Panoramica delle query in Power BI Desktop](desktop-query-overview.md)
* [Configurazione dell'aggiornamento pianificato](../connect-data/refresh-scheduled-refresh.md)

Per altre informazioni sul modello CDM (Common Data Model), è possibile leggere l'articolo di panoramica:
* [Panoramica del modello CDM (Common Data Model)](https://docs.microsoft.com/powerapps/common-data-model/overview)
