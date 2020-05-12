---
title: Limitazioni di Domande e risposte di Power BI
description: Limitazioni attuali di Domande e risposte di Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866772"
---
# <a name="limitations-of-power-bi-qa"></a>Limitazioni di Domande e risposte di Power BI

Domande e risposte di Power BI presenta attualmente alcune limitazioni.

## <a name="data-sources"></a>Origini dati

### <a name="supported-data-sources"></a>Origini dati supportate

Domande e risposte di Power BI supporta le configurazioni seguenti di origini dati nel servizio Power BI:

- Modalità importazione
- Connessione dinamica ad Azure Analysis Services
- Connessione dinamica a SQL Server Analysis Services (con un gateway)
- Set di dati Power BI.

In ognuna di queste configurazioni è supportata anche la sicurezza a livello di riga.

### <a name="data-sources-not-supported"></a>Origini dati non supportate

Domande e risposte di Power BI attualmente non supporta le configurazioni seguenti:

- Sicurezza a livello di oggetto con qualsiasi tipo di origine dati
- DirectQuery su qualsiasi origine. Una soluzione alternativa è quella di usare la connessione dinamica con Azure Analysis Services, che usa DirectQuery.
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

- Country which is USA
- Country which is not USA
- Products > 100
- Products greater than 100
- Products = 100
- Products is 100
- Products < 100
- Products smaller than 100

> [!NOTE]
> Gli strumenti di Domande e risposte supportano solo la modalità di importazione. Non è ancora supportata la connessione a un'origine dati locale o di Azure Analysis Services. Questa limitazione verrà rimossa nelle versioni successive di Power BI.

### <a name="statements-not-supported"></a>Formulazioni non supportate

- L'uso di misure nelle condizioni non è attualmente supportato. Per risolvere il problema, è possibile convertire le misure in colonne calcolate.
- La definizione di più condizioni non è supportata. Per risolvere il problema, creare una colonna calcolata DAX che valuti un valore booleano di formulazione con più condizioni e usare in alternativa questo campo.
- Se non si specifica una condizione di filtro quando Domande e risposte richiede un subset di dati, non è possibile salvare la definizione, anche se l'intera formulazione non ha sottolineature rosse.

## <a name="next-steps"></a>Passaggi successivi

Per migliorare il motore del linguaggio naturale è disponibile una serie di procedure consigliate. Per altre informazioni, vedere [Procedure consigliate per Domande e risposte](q-and-a-best-practices.md).