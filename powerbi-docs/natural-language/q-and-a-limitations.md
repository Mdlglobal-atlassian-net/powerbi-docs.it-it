---
title: Limitazioni di Domande e risposte di Power BI
description: Limitazioni attuali di Domande e risposte di Power BI
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9f1beed3408d53a58a0fb725f9d98a4a95bb1b7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874893"
---
# <a name="limitations-of-power-bi-qa"></a>Limitazioni di Domande e risposte di Power BI

Domande e risposte di Power BI presenta attualmente alcune limitazioni.

## <a name="data-sources"></a>Origini dati

### <a name="supported-data-sources"></a>Origini dati supportate

Domande e risposte di Power BI supporta le configurazioni seguenti di origini dati nel servizio Power BI:

- Modalità importazione
- Connessione dinamica ad Azure Analysis Services
- Connessione dinamica a SQL Server Analysis Services (con un gateway)
- Set di dati Power BI. Quando si usa un set di dati di Power BI, Power BI Desktop segnala un errore relativo a Domande e risposte. Tuttavia, quando si pubblica il report nel servizio Power BI, l'errore scompare.

In ognuna di queste configurazioni è supportata anche la sicurezza a livello di riga.

### <a name="data-sources-not-supported"></a>Origini dati non supportate

Domande e risposte di Power BI attualmente non supporta le configurazioni seguenti:

- Sicurezza a livello di oggetto con qualsiasi tipo di origine dati
- DirectQuery su qualsiasi origine. Una soluzione alternativa a questo problema è quella di usare Live Connect con Azure Analysis Services, che usa DirectQuery.
- Modelli compositi
- Reporting Services 

## <a name="tooling-limitations"></a>Limitazioni degli strumenti

La nuova finestra di dialogo degli strumenti consente agli utenti di personalizzare e migliorare il linguaggio naturale in Domande e risposte. Per altre informazioni sugli strumenti, vedere [Introduzione agli strumenti di Domande e risposte](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitazioni di Rivedi le domande

La funzionalità Rivedi le domande archivia le domande poste al modello di dati per un massimo di 28 giorni. Quando si usa questa nuova funzionalità, si noterà che alcune domande non vengono registrate. Questo avviene per progettazione, poiché il motore del linguaggio naturale esegue una serie di passaggi di pulizia dei dati per garantire che ogni pressione di tasto da parte di un utente non venga registrata o visualizzata.

Gli amministratori di tenant possono usare le impostazioni di amministrazione del tenant per gestire la capacità di archiviare domande. Le autorizzazioni sono basate sui gruppi di sicurezza. 

Gli utenti possono anche evitare di registrare le proprie domande selezionando **Impostazioni** > **Generale** e deselezionando **Allow Q&A to record my utterance** (Consenti a Domande e risposte di registrare l'espressione). 

## <a name="teach-qa-limitations"></a>Limitazioni di Insegna a Domande e risposte

Insegna a Domande e risposte consente di correggere due tipi di errori:

- Assegnare una parola a un campo.
- Assegnare una parola a una condizione di filtro.

Attualmente non è supportata la ridefinizione di un termine riconosciuto o la definizione di altri tipi di condizioni o frasi. Inoltre, quando si definiscono condizioni di filtro, è possibile usare solo un subset limitato del linguaggio, ad esempio:

- "Paese" uguale a "Stati Uniti"
- "Paese" diverso da "Stati Uniti"
- "Peso" > 2000
- "Peso" = 2000
- "Peso" < 2000

> [!NOTE]
> Gli strumenti di Domande e risposte supportano solo la modalità di importazione. Non è ancora supportata la connessione a un'origine dati locale o di Azure Analysis Services. Questa limitazione verrà rimossa nelle versioni successive di Power BI.

### <a name="statements-not-supported"></a>Formulazioni non supportate

- L'uso di misure nelle condizioni non è attualmente supportato. Per risolvere il problema, è possibile convertire le misure in colonne calcolate.
- La definizione di più condizioni non è supportata. Per risolvere il problema, creare una colonna calcolata DAX che valuti un valore booleano di formulazione con più condizioni e usare in alternativa questo campo.
- Se non si specifica una condizione di filtro quando Domande e risposte richiede un subset di dati, non è possibile salvare la definizione, anche se l'intera formulazione non ha sottolineature rosse.
