---
title: Usare Domande e risposte con le connessioni dinamiche in Power BI
description: Documentazione per l'uso delle query in linguaggio naturale in domande e risposte di Power BI con connessioni dinamiche su dati di Analysis Services e sul gateway dati locale.
author: maggiesMSFT
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 3544a5330a21036e0ddecb351fd67b424ca6ebc7
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348874"
---
# <a name="enable-qa-for-live-connections-in-power-bi"></a>Abilitare Domande e risposte con le connessioni dinamiche in Power BI
## <a name="what-is-the-on-premises-data-gateway--what-is-a-live-connection"></a>Che cos'è il gateway dati locale?  Che cos'è una connessione dinamica?
I set di dati in Power BI possono essere importati in Power BI oppure è possibile creare una connessione dinamica ad essi. I set di dati con connessione dinamica sono spesso definiti "locali". Le connessioni dinamiche vengono gestite con un [gateway](../connect-data/service-gateway-onprem.md) e lo scambio dei dati e delle richieste di informazioni avviene usando query dinamiche.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Domande e risposte sui set di dati del gateway dati locale
Se si intende usare Domande e risposte con i set di dati a cui si accede tramite un gateway, è prima necessario abilitarli.

Dopo l’abilitazione, Power BI crea un indice dell’origine dati e carica un subset di tali dati in Power BI per consentire la formulazione delle domande. La creazione dell’indice iniziale potrebbe richiedere alcuni minuti e Power BI gestisce e aggiorna automaticamente l'indice nel momento in cui i dati cambiano. L’uso di Domande e risposte con questi set di dati segue lo stesso comportamento di quello con i dati pubblicati in Power BI. L'intero set di funzionalità disponibili nell'esperienza di Domande e risposte è supportato in entrambi i casi.

Quando si formula una domanda in Power BI, Domande e risposte determina l’oggetto visivo migliore per il foglio di report o il costrutto da usare per rispondere alla domanda tramite un indice del set di dati. Dopo aver determinato la migliore risposta potenziale, Domande e risposte usa DirectQuery per recuperare i dati dall'origine dati tramite il gateway e popolare diagrammi e grafici. Di conseguenza, i risultati di Domande e risposte di Power BI visualizzano sempre i dati più aggiornati direttamente dall'origine dati sottostante.

Poiché Domande e risposte di Power BI usa i valori di testo e schema dell'origine dati per determinare come eseguire le query sul modello sottostante per ottenere le risposte, le ricerche di valori di testo specifici nuovi o eliminati (ad esempio quando si domanda il nome di un cliente correlato a un nuovo record di testo aggiunto) si basano sull’indice aggiornato con i valori più recenti. Power BI mantiene automaticamente aggiornato l'indice dei valori di testo e schema entro una finestra di 60 minuti dalle modifiche.

Per altre informazioni, vedere:

* Che cos'è il [gateway dati locale](../connect-data/service-gateway-onprem.md)?
* [Domande e risposte per i consumer di Power BI](../consumer/end-user-q-and-a.md)

## <a name="enable-qa"></a>Abilitare Domande e risposte
Dopo aver configurato il gateway dati, connettersi ai dati da Power BI.  Creare un dashboard usando i dati locali oppure caricare un file con estensione pbix che usa i dati locali.  È possibile che già si disponga di dati locali in dashboard, report e set di dati precedentemente condivisi con l’utente.

1. In alto a destra in Power BI selezionare l'icona della ruota dentata ![Icona a forma di ingranaggio](media/service-q-and-a-direct-query/power-bi-cog.png) e scegliere **Impostazioni**.
   
   ![Menu Impostazioni](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Selezionare **Set di dati** e scegliere il set di dati da abilitare per Domande e risposte.
   
   ![Schermata Set di dati del menu Impostazioni](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Espandere **Domande e risposte**, selezionare la casella di controllo **Attiva Domande e risposte per questo set di dati** e scegliere **Applica**.
   
    ![Area Domande e risposte espansa](media/service-q-and-a-direct-query/power-bi-qna-dataset-direct-query.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Quali dati vengono memorizzati nella cache e come viene protetta la privacy?
Quando si abilita Domande e risposte per i dati locali, nella cache del servizio viene memorizzato un subset dei dati per garantire il funzionamento di Domande e risposte con prestazioni ragionevoli. Power BI esclude dal caching i valori con più di 24 caratteri. La cache viene eliminata entro alcune ore quando si disabilita Domande e risposte deselezionando **Attiva Domande e risposte per questo set di dati** o quando si elimina il set di dati.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
La funzionalità presenta alcune limitazioni:

* La funzionalità è inizialmente disponibile solo per le origini dati tabulari di SQL Server 2016 Analysis Services. La funzionalità è ottimizzata per funzionare con i dati tabulari. L'uso di Domande e risposte non è ancora supportato per la modalità multidimensionale. Altre origini dati supportate dal gateway dati locale verranno implementate durante in futuro.
* Il supporto completo per la sicurezza a livello di riga definito in SQL Server Analysis Services non è inizialmente disponibile. Quando si formulano domande in Domande e risposte, il "completamento automatico" delle domande durante la digitazione può visualizzare valori di stringa a cui un utente non ha accesso. Tuttavia, poiché la sicurezza a livello di riga definita nel modello viene rispettata per gli oggetti visivi dei report e dei grafici, non c’è la possibilità che vengano esposti i dati numerici sottostanti. Le opzioni per controllare questo comportamento verranno rilasciate nei prossimi aggiornamenti.
* La sicurezza a livello di oggetto non è supportata. Domande e risposte non rispetta la sicurezza a livello di oggetto e può rivelare nomi di tabella o colonna ad utenti non autorizzati ad accedervi. Si consiglia pertanto di abilitare la sicurezza a livello di riga per fare in modo che anche i valori dei dati siano protetti in modo adeguato. 
* Le connessioni dinamiche sono supportate solo con il gateway dati locale. Di conseguenza, questa funzionalità non è utilizzabile con il gateway dati (modalità personale).

## <a name="next-steps"></a>Passaggi successivi

- [Gateway dati locale](../connect-data/service-gateway-onprem.md)  
- [Gestire l'origine dati - Analysis Services](../connect-data/service-gateway-enterprise-manage-ssas.md)  
- [Concetti di base sulle finestre di progettazione del servizio Power BI](../fundamentals/service-basic-concepts.md)  
- [Panoramica di Domande e risposte di Power BI](../consumer/end-user-q-and-a.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
