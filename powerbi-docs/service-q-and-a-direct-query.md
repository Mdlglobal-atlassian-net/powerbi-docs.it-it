---
title: Usare Domande e risposte con le connessioni dinamiche in Power BI
description: Documentazione per l'uso delle query in linguaggio naturale in domande e risposte di Power BI con connessioni dinamiche su dati di Analysis Services e sul gateway dati locale.
author: maggiesMSFT
manager: kfile
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 9836cd88bef5066f61a8ae44eabe7685196e2bed
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65624932"
---
# <a name="enable-qa-for-live-connections-in-power-bi"></a>Abilitare Domande e risposte con le connessioni dinamiche in Power BI
## <a name="what-is-the-on-premises-data-gateway--what-is-a-live-connection"></a>Che cos'è il gateway dati locale?  Che cos'è una connessione dinamica?
I set di dati in Power BI possono essere importati in Power BI oppure è possibile creare una connessione dinamica ad essi. Live connessione i set di dati vengono spesso definite come "locale". Le connessioni dinamiche vengono gestite con un [gateway](service-gateway-onprem.md) e lo scambio dei dati e delle richieste di informazioni avviene usando query dinamiche.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Domande e risposte sui set di dati del gateway dati locale
Se si intende usare Domande e risposte con i set di dati a cui si accede tramite un gateway, è prima necessario abilitarli.

Dopo l’abilitazione, Power BI crea un indice dell’origine dati e carica un subset di tali dati in Power BI per consentire la formulazione delle domande. La creazione dell’indice iniziale potrebbe richiedere alcuni minuti e Power BI gestisce e aggiorna automaticamente l'indice nel momento in cui i dati cambiano. L’uso di Domande e risposte con questi set di dati segue lo stesso comportamento di quello con i dati pubblicati in Power BI. L’intero set di funzionalità disponibili nell’esperienza di Domande e risposte è supportato in entrambi i casi, incluso l'uso dell'origine dati con Cortana.

Quando si formula una domanda in Power BI, Domande e risposte determina l’oggetto visivo migliore per il foglio di report o il costrutto da usare per rispondere alla domanda tramite un indice del set di dati. Dopo aver determinato la migliore risposta potenziale, Domande e risposte usa DirectQuery per recuperare i dati dall'origine dati tramite il gateway e popolare diagrammi e grafici. In questo modo, i risultati di Domande e risposte di Power BI mostrano sempre i dati più aggiornati direttamente dall'origine dati sottostante.

Poiché Domande e risposte di Power BI usa i valori di testo e schema dell'origine dati per determinare come eseguire le query sul modello sottostante per ottenere le risposte, le ricerche di valori di testo specifici nuovi o eliminati (ad esempio quando si domanda il nome di un cliente correlato a un nuovo record di testo aggiunto) si basano sull’indice aggiornato con i valori più recenti. Power BI mantiene automaticamente aggiornato l'indice dei valori di testo e schema entro una finestra di 60 minuti dalle modifiche

Per altre informazioni, vedere:

* Che cos'è il [gateway dati locale](service-gateway-onprem.md)?
* [Per gli utenti di Power BI Q & a](consumer/end-user-q-and-a.md)

## <a name="enable-qa"></a>Abilitare Domande e risposte
Dopo aver configurato il gateway dati, connettersi ai dati da Power BI.  Creare un dashboard usando i dati locali oppure caricare un file con estensione pbix che usa i dati locali.  È possibile che già si disponga di dati locali in dashboard, report e set di dati precedentemente condivisi con l’utente.

1. In alto a destra in Power BI selezionare l'icona della ruota dentata ![Icona a forma di ingranaggio](media/service-q-and-a-direct-query/power-bi-cog.png) e scegliere **Impostazioni**.
   
   ![Menu Impostazioni](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Selezionare **Set di dati** e scegliere il set di dati da abilitare per Domande e risposte.
   
   ![Schermata Set di dati del menu Impostazioni](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Espandere **Domande e risposte e Cortana**, selezionare la casella di controllo **Attiva Domande e risposte per questo set di dati** e scegliere **Applica**.
   
    ![Area Domande e risposte espansa](media/service-q-and-a-direct-query/power-bi-q-and-a-directquery.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Quali dati vengono memorizzati nella cache e come viene protetta la privacy?
Quando si abilita Domande e risposte per i dati locali, nella cache del servizio viene memorizzato un subset dei dati per garantire il funzionamento di Domande e risposte con prestazioni ragionevoli, Power BI esclude dal caching i valori con più di 24 caratteri. La cache viene eliminata entro alcune ore quando si disabilita Domande e risposte deselezionando **Attiva Domande e risposte per questo set di dati** o quando si elimina il set di dati.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
La funzionalità presenta alcune limitazioni:

* La funzionalità è inizialmente disponibile solo per le origini dati tabulari di SQL Server 2016 Analysis Services. La funzionalità è ottimizzata per funzionare con i dati tabulari. Esperienza di domande e risposte non è ancora supportata per la modalità multidimensionale. Altre origini dati supportate dal gateway dati locale verranno implementate durante in futuro.
* Il supporto completo per la sicurezza a livello di riga definito in SQL Server Analysis Services non è disponibile inizialmente. Quando si formulano domande in domande e risposte, il "completamento automatico" delle domande durante la digitazione può mostrare valori di stringa un utente non ha accesso a. Tuttavia, poiché la sicurezza a livello di riga definita nel modello viene rispettata per gli oggetti visivi dei report e dei grafici, non c’è la possibilità che vengano esposti i dati numerici sottostanti. Le opzioni per controllare questo comportamento verranno rilasciate nei prossimi aggiornamenti.
* Sicurezza a livello di oggetto (amministrazione) non è supportata. Domande e risposte non rispettino la sicurezza a livello di oggetto e consente di rilevare nomi di tabella o colonna per gli utenti autorizzati ad accedere a essi. Si consiglia pertanto di abilitare la sicurezza a livello di riga per fare in modo che anche i valori dei dati siano protetti in modo adeguato. 
* Le connessioni dinamiche sono supportate solo con il gateway dati locale. Di conseguenza, questo non è utilizzabile con il gateway personale.

## <a name="next-steps"></a>Passaggi successivi

- [Gateway dati locale](service-gateway-onprem.md)  
- [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
- [Power BI: Concetti di base](consumer/end-user-basic-concepts.md)  
- [Panoramica di Domande e risposte di Power BI](consumer/end-user-q-and-a.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

