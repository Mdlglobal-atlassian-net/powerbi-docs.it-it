---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409369"
---
## <a name="faq"></a>DOMANDE FREQUENTI
**Domanda**: Cosa accade se sono stati precedentemente creati ruoli e regole per un set di dati nel servizio Power BI? Continueranno a funzionare anche se non si esegue alcuna operazione?  
**Risposta**: No, il rendering degli oggetti visivi non verrà eseguito correttamente. Sarà necessario creare di nuovo i ruoli e le regole all'interno di Power BI Desktop e quindi pubblicarli nel servizio Power BI.

**Domanda**: È possibile creare questi ruoli per le origini dati di Analysis Services?  
**Risposta**: È possibile se i dati sono stati importati in Power BI Desktop. Se si usa una connessione dinamica, non sarà possibile configurare la sicurezza a livello di riga all'interno del servizio Power BI. Ciò viene definito all'interno del modello di Analysis Services in locale.

**Domanda**: È possibile usare la sicurezza a livello di riga per limitare le colonne o le misure accessibili agli utenti?  
**Risposta**: No, se un utente può accedere a una riga specifica di dati, può visualizzare tutte le colonne di dati per tale riga.

**Domanda**: La sicurezza a livello di riga consente di nascondere i dati dettagliati ma di concedere l'accesso al riepilogo dati negli oggetti visivi?  
**Risposta**: No. È possibile proteggere singole righe di dati, ma gli utenti possono visualizzare sempre sia i dettagli sia il riepilogo dati.

**Domanda**: Per l'origine dati sono già stati definiti ruoli di sicurezza, ad esempio ruoli di SQL Server o ruoli di SAP BW. Qual è la relazione tra questi ruoli e la sicurezza a livello di riga?  
**Risposta**: La risposta varia a seconda che i dati vengano importati o si usi DirectQuery. Se si importano i dati nel set di dati Power BI, i ruoli di sicurezza nell'origine dati non vengono usati. In questo caso, è necessario definire la sicurezza a livello di riga per applicare regole di sicurezza per gli utenti che si connettono in Power BI. Se si usa DirectQuery, i ruoli di sicurezza nell'origine dati vengono usati. Quando un utente apre un report di Power BI invia una query all'origine dati sottostante, che applica le regole di sicurezza ai dati in base alle credenziali dell'utente.
