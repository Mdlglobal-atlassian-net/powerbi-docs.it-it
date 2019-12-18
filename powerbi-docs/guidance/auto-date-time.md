---
title: Linee guida per Data/ora automatica in Power BI Desktop
description: Linee guida per l'uso della funzionalità di data/ora automatica in Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 30bfacc1024035f0849440eec8b1c7051ff4d82a
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002444"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Linee guida per Data/ora automatica in Power BI Desktop

Questo articolo è destinato a esperti di modellazione di dati che sviluppano modelli di importazione o compositi in Power BI Desktop. Include linee guida, raccomandazioni e considerazioni per l'uso di _Data/ora automatica_ di Power BI Desktop in situazioni specifiche. Per una panoramica e un'introduzione generale a _Data/ora automatica_ vedere [Data/ora automatica in Power BI Desktop](../desktop-auto-date-time.md).

L'opzione _Data/ora automatica_ offre funzionalità di Business Intelligence per le gerarchie temporali pratiche, veloci e facili da usare. Gli autori di report possono usare le funzionalità di Business Intelligence per le gerarchie temporali per l'applicazione di filtri, il raggruppamento e il drill-down in periodi di tempo del calendario.

## <a name="considerations"></a>Considerazioni

L'elenco puntato seguente descrive le considerazioni e le possibili limitazioni associate all'opzione _Data/ora automatica_.

- **È valida per tutte le colonne o per nessuna di esse:** Quando è abilitata, l'opzione _Data/ora automatica_ viene applicata a tutte le colonne data nelle tabelle di importazione che non sono il lato &quot;molti&quot; di una relazione. Non può essere abilitata o disabilitata selettivamente colonna per colonna.
- **Solo periodi di calendario:** Le colonne anno e trimestre fanno riferimento a periodi di calendario. Questo significa che l'anno inizia il 1 gennaio e termina il 31 dicembre. Non è possibile personalizzare la data di inizio o di fine dell'anno.
- **Personalizzazione:** Non è possibile personalizzare i valori usati per descrivere i periodi di tempo. Inoltre non è possibile aggiungere altre colonne per descrivere altri periodi di tempo, ad esempio le settimane.
- **Filtro dell'anno:** I valori delle colonne **Trimestre**, **Mese** e **Giorno** non includono il valore dell'anno. Ad esempio la colonna **Mese** contiene solo i nomi dei mesi, ovvero Gennaio, Febbraio e così via. I valori non sono completamente autodescrittivi e in alcune strutture di report potrebbero non comunicare il contesto di filtro anno.

    Per questo motivo è importante che l'implementazione di filtri o il raggruppamento avvengano in base alla colonna **Anno**. Quando si esegue il drill-down usando la gerarchia l'anno verrà filtrato, salvo se il livello **Anno** viene rimosso intenzionalmente. Se non è presente alcun filtro o raggruppamento in base all'anno, un raggruppamento in base al mese, ad esempio, riepiloga i valori di tutti gli anni per quel mese.
- **Applicazione di filtro data a una sola tabella:** Poiché ogni colonna della data produce una propria tabella di data/ora automatica (nascosta), non è possibile applicare un filtro ora a una tabella e propagarlo a più tabelle modello. L'applicazione di filtri con questa modalità è un requisito di modellazione comune durante la creazione di report su più soggetti (tabelle di tipo fact), come vendite e budget di vendite. Quando si usa la data/ora automatica, l'autore del report deve applicare filtri a ogni singola colonna data.
- **Dimensioni del modello:** Ogni colonna data che genera una tabella data/ora automatica nascosta produce un incremento delle dimensioni del modello e prolunga il tempo necessario per l'aggiornamento dei dati.

## <a name="recommendations"></a>Raccomandazioni

È consigliabile mantenere attivata l'opzione _Data/ora automatica_ solo quando si lavora con periodi di tempo del calendario e si hanno requisiti di modellazione semplici in termini di tempo. L'uso di questa opzione può risultare pratico anche quando si creano modelli ad hoc o si esegue l'esplorazione dei dati o la profilatura.

Quando l'origine dati definisce già una tabella delle dimensioni data, questa tabella deve essere usata per definire in modo coerente il tempo all'interno dell'organizzazione. Un caso tipico si verifica quando l'origine dati è un data warehouse. In alternativa è possibile generare tabelle data nel modello usando le funzioni DAX [CALENDAR](/dax/calendar-function-dax) o [CALENDARAUTO](/dax/calendarauto-function-dax). Quindi è possibile aggiungere colonne calcolate per supportare i requisiti noti di applicazione filtri e raggruppamento del tempo. Questo approccio può consentire la creazione di un'unica tabella che esegue la propagazione a tutte le tabelle di tipo fact, ed eventualmente risultare in un'unica tabella per l'applicazione di filtri temporali. Per altre informazioni sulla creazione di tabelle data vedere l'articolo [Impostare e usare tabelle data in Power BI Desktop](../desktop-date-tables.md).

Se l'opzione _Data/ora automatica_ non è importante nei progetti sui quali si lavora, è consigliabile disattivare l'opzione _Data/ora automatica_ a livello globale. In questo modo l'opzione _Data/ora automatica_ non sarà abilitata in tutti i nuovi file di Power BI Desktop creati.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Data/ora automatica in Power BI Desktop](../desktop-auto-date-time.md)
- [Impostare e usare tabelle data in Power BI Desktop](../desktop-date-tables.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
