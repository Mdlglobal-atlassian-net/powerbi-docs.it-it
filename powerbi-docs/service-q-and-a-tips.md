---
title: Suggerimenti e idee per porre domande con Domande e risposte in Power BI
description: Suggerimenti e idee per porre domande con Domande e risposte in Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/24/2017
ms.author: jastru
ms.openlocfilehash: 4b861927bad961837f40f34636f0570106aaabc6
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Suggerimenti per porre domande in Domande e risposte di Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Parole e terminologia riconosciute da Domande e risposte
L'elenco di parole chiave non è completo.  Il modo migliore per verificare se Power BI riconosce una parola chiave consiste nel provare a usarla digitandola nella casella della domanda.  Se la parola o il termine viene visualizzato in grigio, Power BI non lo riconosce o non lo riconosce nel contesto corrente.

L'elenco seguente usa i tempi verbali presenti, ma tutti i tempi verbali vengono riconosciuti nella maggior parte dei casi. Ad esempio "è" include sono, era, erano, saranno, hanno, ha, aveva, avrà, avranno, faccio, fa, fanno.  E "ordina" include ordinato e ordinamento.  PowerBI riconosce e include anche le versioni singolari e plurali di una parola. Power BI riconosce ad esempio "anno" e "anni".

> [!NOTE]
> Domande e risposte è disponibile anche nell'[app Microsoft Power BI per iOS sui dispositivi iPad, iPhone e iPod Touch](mobile-apps-ios-qna.md).
> 
> 

Se si ha un set di dati, aggiungere formulazioni e i sinonimi per migliorare i risultati di Domande e risposte per i clienti.

**Aggregazioni**: totale, somma, importo, numero, quantità, conteggio, media, la maggior parte, almeno, più piccolo, più grande, minore, più elevato, grandissimo, massimo, max, più grande, più basso, il più piccolo, minimo, min

**Articoli**: un, una, il

**Vuoto e booleano**: vuoto, vuoti, null, con prefisso "non" o "no", stringa vuota, testo vuoto, true, t, false, f

**Confronti**: confronto, confronti, rispetto a, a confronto con

**Congiunzioni**: e, o, ogni, con, confronto, &, ed, ma, né, insieme a, oltre a

**Contrazioni**: Domande e risposte riconosce quasi tutte le contrazioni.  Ecco alcuni esempi: un'ora, l'eroe, l'amicizia, d'essere, senz'altro.

**Date**: Power BI riconosce la maggior parte dei termini di data (giorno, settimana, mese, anno, trimestre, decennio e così via) e le date scritte in molti formati diversi (vedere più avanti). Power BI riconosce anche le parole chiave seguenti: MonthName, Days 1-31, decade.

Esempi: 3 gennaio 1995, 03 gen 1995, 03/01/1995, 03-01-1995, nomi dei mesi.

**Date relative**: oggi, adesso, ora corrente, ieri, domani, attuale, prossimo, in arrivo, ultimo, precedente, fa, prima d'ora, prima di, dopo, più tardi di, da, alle, in data, da adesso, dopo ora, nel futuro, in passato, recente, precedentemente, entro, tra, su, n. giorni fa, n. giorni da adesso, successivamente, una volta, due volte.

Esempio: conteggio degli ordini negli ultimi 6 giorni.

**Uguaglianza (intervallo)**: compreso tra, uguale a, =, dopo, maggiore di, tra, entro, precedente

Esempi: l'anno dell'ordine è precedente al 2012? Il prezzo è compreso tra 10 e 20? L'età di John è maggiore di 40? Totale vendite compreso tra 200-300?

**Uguaglianza (valore)**: è, uguale, uguale a, tra, per, entro, è compreso, si trova in

Esempi: Quali prodotti sono verdi? La data dell'ordine è uguale a 2012. L'età di John è 40? Totale vendite non uguali a 200? La data dell'ordine è 01/01/2016. 10 nel prezzo? Verde per colore? 10 nel prezzo?

**Nomi**: se una colonna nel set di dati contiene la frase "nome" (ad esempio EmployeeName), Domande e risposte riconosce che i valori nella colonna sono nomi ed è possibile porre domande quali "quali dipendenti si chiamano robert".

**Pronomi**: io, noi, tu, voi, egli, ella, esso, essa, lui, lei, essi, esse, loro, mio tuo, suo, nostro, vostro, loro, questo, codesto, quello, stesso, medesimo, tale

**Comandi di query**: ordinato, ordina per, direzione, gruppo, raggruppa per, per, mostra, elenco, visualizza, fornisci, nome, solo, soltanto, disponi, classificazione, confronto,a, con, rispetto a, alfabeticamente, in ordine crescente, in ordine decrescente, ordine

**Intervallo**: maggiore, più, più grande, superiore, oltre, >, meno, più piccolo, minore, sotto, inferiore a, <, almeno, non meno di, >=, al massimo, non più di, <=, in, tra, nell'intervallo di, da, successivo, precedente, prima, dopo, il giorno, alle, più tardi di, successivamente, da, inizia con, a partire da, finisce con

**Orari**: in punto, mezzogiorno, mezzanotte, ora, minuto, secondo, secondo, hh:mm:ss

Esempi: 22.00, 22:35, 22:35:15, 22 in punto, mezzogiorno, mezzanotte, ora, minuto, secondo.

**Numeri principali** (ordine, classificazione): principale, inferiore, più alto, più basso, primo, ultimo, successivo, meno recente, più recente, più vecchio, più nuovo, recentissimo, successivo

**Tipo di oggetti visivi**: tutti i tipi di oggetti visivi nativi di Power BI.  Se è un'opzione disponibile nel riquadro Visualizzazioni, è possibile includere il valore nella domanda.  L'eccezione è costituita dagli [oggetti visivi personalizzati](power-bi-custom-visuals.md), aggiunti manualmente al riquadro Visualizzazioni.

Esempio: mostra aree in base al mese e al totale vendite sotto forma di grafico a barre

**Relazione (qualificata)**: quando, dove, quale, chi, a chi, quanti, quale quantità, quante volte, quanto spesso, con che frequenza, importo, numero, quantità, durata, cosa

## <a name="qa-helps-you-phrase-the-question"></a>Domande e risposte aiuta a formulare la domanda
Domande e risposte fa del suo meglio per garantire che la risposta rifletta accuratamente la domanda che viene posta. Questa operazione viene eseguita in diversi modi. Per tutti questi, è possibile accettare l'azione in modo completo, in parte o non accettarla. Quando si digita la domanda, Domande e risposte:

* completa automaticamente parole e domande. Usa diverse strategie, tra cui il completamento automatico di parole riconoscibili, domande comuni per le cartelle di lavoro sottostanti e domande utilizzate in precedenza che hanno restituito risposte valide. Se è disponibile più di un'opzione di completamento automatico, vengono presentate in un elenco a discesa.
* corregge l'ortografia.
* fornisce un'anteprima della risposta sotto forma di visualizzazione. La visualizzazione si aggiorna quando si digita e modifica la domanda, senza attendere che l'utente prema INVIO.
* auto-suggerisce termini sostitutivi dai set di dati sottostanti quando si sposta il cursore nella casella della domanda.
* riformula la domanda in base ai dati nei set di dati sottostanti. Questo contribuisce a garantire che Domande e risposte comprenda la domanda quando Domande e risposte sostituisce le parole utilizzate con sinonimi dai set di dati sottostanti.
* offusca parole che non riconosce.

## <a name="combine-results-from-more-than-one-dataset"></a>Combinare i risultati da più set di dati
Una delle funzionalità più potenti di Power BI è la possibilità di combinare i dati da set di dati diversi.  Non occorre quindi limitare le domande a un singolo set di dati, ma si possono porre domande che recuperano dati da più set di dati. Ad esempio, se il dashboard contiene riquadri dall'esempio di analisi delle vendite al dettaglio e un set di dati della popolazione degli stati, è possibile domandare *mostra il numero di negozi per popolazione degli stati come grafico a barre in ordine decrescente*.

## <a name="dont-stop-now"></a>Non interrompere ora
Dopo che Domande e risposte ha mostrato i risultati, continuare la conversazione! Utilizzare le funzionalità interattive della visualizzazione e di Domande e risposte per scoprire ulteriori approfondimenti.

## <a name="next-steps"></a>Passaggi successivi
Tornare a [Domande e risposte in Power BI](service-q-and-a.md)  

[Power BI - Concetti di base](service-basic-concepts.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

