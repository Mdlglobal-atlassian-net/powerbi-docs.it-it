---
ms.openlocfilehash: b05b5b0b5212f39b9b47cb63e2fc8522fff2f8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194081"
---
## <a name="faq"></a>DOMANDE FREQUENTI
**Domanda**: Cosa accade se sono stati precedentemente creati ruoli e le regole per un set di dati nel servizio Power BI? Continueranno a funzionare anche se non si esegue alcuna operazione?  
**Risposta**: No. Il rendering degli oggetti visivi non verrà eseguito correttamente. Sarà necessario creare di nuovo i ruoli e le regole all'interno di Power BI Desktop e quindi pubblicarli nel servizio Power BI.

**Domanda**: È possibile creare questi ruoli per le origini dati di Analysis Services?  
**Risposta**: È possibile se i dati sono stati importati in Power BI Desktop. Se si usa una connessione dinamica, non sarà possibile configurare la sicurezza a livello di riga all'interno del servizio Power BI. Ciò viene definito all'interno del modello di Analysis Services in locale.

**Domanda**: È possibile usare la sicurezza a livello di riga per limitare le colonne o le misure accessibili agli utenti?  
**Risposta**: No. Se un utente può accedere a una riga specifica di dati, può visualizzare tutte le colonne di dati per tale riga.

**Domanda**: La sicurezza a livello di riga consente di nascondere i dati dettagliati ma di concedere l'accesso al riepilogo dati negli oggetti visivi?  
**Risposta**: No. È possibile proteggere singole righe di dati, ma gli utenti possono visualizzare sempre sia i dettagli sia il riepilogo dati.

