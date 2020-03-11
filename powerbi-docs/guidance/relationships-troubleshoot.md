---
title: Linee guida per la risoluzione dei problemi relativi alle relazioni
description: Linee guida per la risoluzione dei problemi di relazione dei modelli.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263646"
---
# <a name="relationship-troubleshooting-guidance"></a>Linee guida per la risoluzione dei problemi relativi alle relazioni

Questo articolo è destinato agli autori di modelli di dati che usano Power BI Desktop. Vengono offerte linee guida su come risolvere problemi specifici che possono verificarsi durante lo sviluppo di modelli e report.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Elenco di controllo per la risoluzione dei problemi

Quando un oggetto visivo del report è configurato per l'uso di campi da due o più tabelle e non presenta il risultato corretto, o non presenta alcun risultato, è possibile che il problema sia correlato alle relazioni del modello.

Di seguito è riportato un elenco di controllo generale per la risoluzione di questo tipo di problemi. Passare da un punto all'altro dell'elenco di controllo finché non si individua il problema.

1. Passare l'oggetto visivo a una tabella o a una matrice oppure aprire il riquadro "Visualizza dati". È più semplice risolvere i problemi quando è possibile visualizzare i risultati della query
1. Se è presente un risultato di query vuoto, passare a Vista dati: verificare che le tabelle siano state caricate con righe di dati
1. Passare a Vista modello: consente di visualizzare con facilità le relazioni e determinarne rapidamente le proprietà
1. Verificare che esistano relazioni tra le tabelle
1. Verificare che le proprietà della cardinalità siano configurate correttamente: potrebbero non essere corrette se una colonna lato "molti" contiene attualmente valori univoci ed è stata erroneamente configurata come lato "uno"
1. Verificare che le relazioni siano attive (linea continua)
1. Verificare che le direzioni del filtro supportino la propagazione (interpretare la testa delle frecce)
1. Verificare che siano correlate le colonne corrette, quindi selezionare la relazione o posizionare il cursore su di essa per visualizzare le colonne correlate
1. Verificare che i tipi di dati delle colonne correlate siano uguali o almeno compatibili: è possibile correlare una colonna di testo a una colonna di numeri interi, ma i filtri non troveranno corrispondenze da propagare
1. Passare a Vista dati e verificare che i valori corrispondenti siano presenti nelle colonne relative

## <a name="troubleshooting-guide"></a>Guida per la risoluzione dei problemi

Di seguito vengono elencati i problemi con le soluzioni possibili.

|Problema|Cause possibili|
|---------|---------|
|L'oggetto visivo non visualizza risultati|- Il modello non è ancora stato caricato con i dati<br />- Non esistono dati nel contesto del filtro<br />- Vengono applicati criteri di sicurezza a livello di riga<br />- Le relazioni tra le tabelle non vengono propagate, _seguire l'elenco di controllo riportato in precedenza_<br />- Vengono applicati criteri di sicurezza a livello di riga ma non è stata abilitata alcuna relazione bidirezionale da propagare. Vedere [Sicurezza a livello di riga con Power BI Desktop](../desktop-rls.md)|
|L'oggetto visivo visualizza lo stesso valore per tutti i raggruppamenti |- Non esistono relazioni<br />- Le relazioni tra le tabelle non vengono propagate, _seguire l'elenco di controllo riportato in precedenza_|
|L'oggetto visivo visualizza dei risultati, ma non sono corretti|- L'oggetto visivo non è configurato correttamente<br />- La logica della misura non è corretta<br />- È necessario aggiornare i dati del modello<br />- I dati di origine non sono corretti<br />- Le colonne delle relazioni sono correlate in modo errato, ad esempio la colonna **ProductID** esegue il mapping a **CustomerID**<br />- Si tratta di una relazione tra due tabelle DirectQuery e la colonna lato "uno" di una relazione contiene valori duplicati|
|Vengono visualizzati raggruppamenti o elementi del filtro dei dati o del filtro vuoti e le colonne di origine non contengono righe vuote|- Si tratta di una relazione forte e la colonna lato "molti" contiene valori non archiviati nella colonna lato "uno". Vedere [Relazioni tra modelli in Power BI Desktop - Relazioni forti](../desktop-relationships-understand.md#strong-relationships)<br />- Si tratta di una relazione forte uno-a-uno e le colonne correlate contengono righe vuote. Vedere [Relazioni tra modelli in Power BI Desktop - Relazioni forti](../desktop-relationships-understand.md#strong-relationships)<br />- Una colonna lato "molti" di una relazione inattiva contiene righe vuote oppure valori non archiviati nel lato "uno"|
|Dati mancanti nell'oggetto visivo|- Vengono applicati filtri non corretti/imprevisti<br />- Vengono applicati criteri di sicurezza a livello di riga<br />- Si tratta di una relazione debole e sono presenti righe vuole nelle colonne relative oppure si verificano problemi di integrità dei dati. Vedere [Relazioni tra modelli in Power BI Desktop - Relazioni deboli](../desktop-relationships-understand.md#weak-relationships)<br />- Si tratta di una relazione tra due tabelle DirectQuery, la relazione è configurata in modo da [presupporre l'integrità referenziale](../desktop-relationships-understand.md#assume-referential-integrity), ma si verificano problemi di integrità dei dati (valori non corrispondenti nelle colonne correlate)|
|Sicurezza a livello di riga non applicata correttamente|- Le relazioni tra le tabelle non vengono propagate, _seguire l'elenco di controllo riportato in precedenza_<br />- Vengono applicati criteri di sicurezza a livello di riga ma non è stata abilitata alcuna relazione bidirezionale da propagare. Vedere [Sicurezza a livello di riga con Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Relazioni nei modelli in Power BI Desktop](../desktop-relationships-understand.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
