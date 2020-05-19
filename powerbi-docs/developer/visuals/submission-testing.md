---
title: Test di presentazione di un oggetto visivo Power BI
description: In questo articolo vengono descritti i test case che l'oggetto visivo deve superare prima della pubblicazione in AppSource. Esistono anche test case opzionali.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131128"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Test di invio di un oggetto visivo Power BI

Prima che l'oggetto visivo possa essere pubblicato in [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), deve superare questi test case. Testare l'oggetto visivo prima di inviarlo. Se l'oggetto visivo non supera i test case necessari, verrà rifiutato.

Per ulteriori informazioni sul processo di pubblicazione, vedere [Pubblicare oggetti visivi di Power BI nel Centro per i partner](./office-store.md).

## <a name="general-test-cases"></a>Test case generali

| Test case | Risultati previsti
| --------- | ----------------
| Creare un **Istogramma a colonne in pila** con **Categoria** e **Valore**. Convertirlo nell'oggetto visivo e quindi tornare all'istogramma. | Dopo queste conversioni non viene visualizzato alcun errore. |
| Creare un **Misuratore** con tre misure. Convertirlo nell'oggetto visivo e quindi tornare al **Misuratore**. | Dopo queste conversioni non viene visualizzato alcun errore. |
| Eseguire le selezioni nell'oggetto visivo. | Gli altri oggetti visivi riflettono le selezioni. |
| Selezionare gli elementi in altri oggetti visivi. | L'oggetto visivo mostra i dati filtrati in base alla selezione in altri oggetti visivi. |
| Controllare le condizioni min/max di **dataViewMapping**. | I bucket di campo possono accettare più campi, un singolo campo o sono determinati da altri bucket. Le condizioni min/max di **dataViewMapping** devono essere configurate correttamente nelle funzionalità dell'oggetto visivo. |
| Rimuovere tutti i campi in ordini diversi. | L'oggetto visivo viene pulito correttamente mentre i campi vengono rimossi in ordine arbitrario. Non sono presenti errori nella console o nel browser. |
| Aprire il riquadro **Formato** con ogni possibile configurazione di bucket. | Questo test non attiva eccezioni di riferimento Null. |
| Filtrare i dati utilizzando il riquadro **Filtro** a livello di oggetto visivo, pagina e report. | Le descrizioni comando sono corrette dopo l'applicazione dei filtri. Le descrizioni comando visualizzano il valore filtrato. |
| Filtrare dati tramite un **Filtro dei dati**. | Le descrizioni comando sono corrette dopo l'applicazione dei filtri. Le descrizioni comando visualizzano il valore filtrato. |
| Filtrare i dati usando un oggetto visivo pubblicato. Selezionare, ad esempio, una sezione a torta o una colonna. | Le descrizioni comando sono corrette dopo l'applicazione dei filtri. Le descrizioni comando visualizzano il valore filtrato. |
| Se il filtro incrociato è supportato, verificare che i filtri funzionino correttamente. | La selezione applicata filtra altri oggetti visivi in questa pagina del report. |
| Applicare la selezione con i tasti CTRL, ALT e MAIUSC. | Non vengono visualizzati comportamenti imprevisti. |
| Modificare la **Modalità visualizzazione** per **Dimensioni effettive**, **Adatta alla pagina**e **Adatta in larghezza**. | Le coordinate del mouse sono accurate. |
| Ridimensionare l'oggetto visivo. | L'oggetto visivo reagisce correttamente al ridimensionamento. |
| Impostare il valore minimo per le dimensioni del report. | Nessun errore di visualizzazione. |
| Verificare che le barre di scorrimento funzionino correttamente. | Se necessario, devono essere presenti barre di scorrimento. Controllare le dimensioni della barra di scorrimento. Le barre di scorrimento non devono essere troppo larghe o alte. La posizione e le dimensioni delle barre di scorrimento devono essere adeguate ad altri elementi dell'oggetto visivo. Verificare che le barre di scorrimento siano necessarie per diverse dimensioni dell'oggetto visivo. |
| Aggiungere l'oggetto visivo a un **dashboard**. | L'oggetto visivo dovrebbe essere visualizzato correttamente. |
| Consente di aggiungere più versioni dell'oggetto visivo a una singola pagina del report. | Tutte le versioni dell'oggetto visivo vengono visualizzate e funzionano correttamente. |
| Consente di aggiungere più versioni dell'oggetto visivo a pagine del report multiple. | Tutte le versioni dell'oggetto visivo vengono visualizzate e funzionano correttamente. |
| Passa tra le pagine del report. | L'oggetto visivo viene visualizzato correttamente. |
| Testare la visualizzazione di lettura e di modifica per l'oggetto visivo. | Tutte le funzioni operano correttamente. |
| Se l'oggetto visivo usa animazioni, aggiungere, modificare ed eliminare elementi dell'oggetto visivo. | L'animazione degli elementi visivi funziona correttamente. |
| Aprire il riquadro **Proprietà**. Attivare e disattivare le proprietà, immettere testo personalizzato, evidenziare le opzioni disponibili e immettere dati non validi. | L'oggetto visivo risponde correttamente. |
| Salvare il report e riaprirlo. | Tutte le impostazioni delle proprietà vengono mantenute. |
| Cambiare le pagine del report e quindi tornare indietro. | Tutte le impostazioni delle proprietà vengono mantenute. |
| Testare tutte le funzionalità dell'oggetto visivo, incluse le diverse opzioni fornite dallo stesso. | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Testare tutti i tipi di dati numerici, di data e di carattere, come nei test seguenti. | Tutti i dati sono formattati correttamente. |
| Esaminare la formattazione dei valori della descrizione comando, delle etichette dell'asse, delle etichette dati e di altri elementi visivi con la formattazione. | Tutti gli elementi sono formattati correttamente. |
| Verificare che le etichette dati usino la stringa di formato. | Tutte le etichette dati sono formattate correttamente. |
| Attivare e disattivare la formattazione automatica per i valori numerici nelle descrizioni comandi. | Le descrizioni comandi visualizzano correttamente i valori. |
| Testare le voci di dati con tipi di dati diversi, incluse le stringhe numeriche, di testo, data/ora e di formato diverso dal modello. Testare volumi di dati diversi, ad esempio migliaia di righe, una riga e due righe. | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Fornire dati errati all'oggetto visivo, ad esempio null, Infinity, valori negativi e tipi di valore non corretti. | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |

## <a name="optional-browser-testing"></a>Test del browser facoltativo

Il team di AppSource convalida l'oggetto visivo nelle versioni più recenti di Windows dei browser Google Chrome, Microsoft Edge e Mozilla Firefox.
Facoltativamente, è possibile testare l'oggetto visivo nei seguenti browser.

| Test case | Risultati previsti
| --------- | ----------------
| **Windows** |
| Google Chrome (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Mozilla Firefox (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Microsoft Edge (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Microsoft Internet Explorer 11 (facoltativo) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| **macOS** |
| Chrome (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Firefox (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Safari (versione precedente) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| **Linux** |
| Firefox (versione più recente e versioni precedenti) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| **Dispositivi mobili (iOS)** |
| Apple Safari iPad (versione precedente di Safari) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| iPad Chrome (versione più recente di Safari) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| **Dispositivi mobili (Android)** |
| Chrome (versione più recente e versioni precedenti) | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |

## <a name="desktop-testing"></a>Test del desktop

Testare l'oggetto visivo nella versione corrente di [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Test case | Risultati previsti
| --------- | ----------------
| Testare tutte le funzionalità dell'oggetto visivo. | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Importare, salvare, aprire un file e pubblicare nel servizio Web di Power BI usando il pulsante **Pubblica** in Power BI Desktop. | Tutte le visualizzazioni e le caratteristiche funzionano correttamente. |
| Modificare la stringa di formato numerico in modo che contenga zero cifre decimali o tre cifre decimali aumentando o diminuendo la precisione. | L'oggetto visivo viene visualizzato correttamente. |

## <a name="performance-testing"></a>Test delle prestazioni

L'oggetto visivo deve essere eseguito a un livello accettabile. Usare gli strumenti per sviluppatori per convalidare le prestazioni. Non fare affidamento sui segnali visivi e sui registri temporali della console.

| Test case | Risultati previsti
| --------- | ----------------
| Creare un oggetto visivo con molti elementi visivi. | L'oggetto visivo dovrebbe funzionare correttamente e non bloccare l'applicazione. Non dovrebbero verificarsi problemi di prestazioni con elementi quali velocità di animazione, ridimensionamento, filtro e selezione.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sul processo di pubblicazione, vedere [Pubblicare oggetti visivi di Power BI nel Centro per i partner](./office-store.md).

Altre domande? [Inviare una domanda alla community di Power BI](https://community.powerbi.com/).
