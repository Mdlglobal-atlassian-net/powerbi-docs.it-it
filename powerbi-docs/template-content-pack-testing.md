---
title: Test dei pacchetti di contenuto modello per Power BI
description: Test dei pacchetti di contenuto modello
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 8a5382a5e435f916599b05310f89d9b1f0327023
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430672"
---
# <a name="testing-template-content-packs-for-power-bi"></a>Test dei pacchetti di contenuto modello per Power BI
Esistono diversi modi per testare un pacchetto di contenuto prima di inviarlo per la pubblicazione.  

> [!NOTE]
> Se il pacchetto di contenuto usa [connettore dati](https://aka.ms/DataConnectors) personalizzato sviluppato dall'utente, non riuscirà a testare l'aggiornamento dei dati o il pacchetto di contenuto del modello come descritto di seguito. In tal caso, [inviare](#submission) il pacchetto di contenuto da testare al team di Power BI.
> 
> 

## <a name="testing-scheduled-data-refresh"></a>Test dell'aggiornamento pianificato dei dati
I pacchetti di contenuto dei modelli usano l'aggiornamento in PowerBI.com per creare un'istanza di un pacchetto di contenuto modello con i dati dei clienti quando questi effettuano la connessione. Prima che il pacchetto di contenuto venga reso disponibile pubblicamente, è possibile testare questo flusso con il file Desktop che è stato creato.

Dopo aver caricato il file, selezionare "…" accanto al set di dati e selezionare Pianifica aggiornamento. Configurare le credenziali per l'origine. Assicurarsi che l'aggiornamento del set di dati avvenga correttamente. A questo scopo, provare sia "Aggiorna ora" sia "Aggiornamento pianificato". In caso di errori di aggiornamento, controllare il messaggio di errore e convalidare le query e il sistema finale.

### <a name="additional-refresh-tips"></a>Suggerimenti aggiuntivi per l'aggiornamento
* Quando si prova a pianificare l'aggiornamento deve essere rilevata una sola origine dati  
* La connessione di test deve indicare che l'utente riuscirà a caricare il pacchetto di contenuto. Diversamente, verificare che le query gestiscano i casi di errore aggiuntivi.  
* L'aggiornamento dovrebbe essere completato in un tempo ragionevole, non superiore a 5 minuti circa.  

![impostazioni](media/template-content-pack-testing/scheduledrefresh.png)

<a name="templates"></a>

## <a name="testing-templates"></a>Modelli di test
Un pacchetto di contenuto del modello è simile alle soluzioni esistenti ad eccezione del fatto che non include i dati effettivi nel set di dati. Al contrario, quando un utente utilizza o crea un'istanza di un modello, riceve la richiesta di immettere i parametri e le credenziali per connettersi. Una volta connesso, noterà i propri dati nel dashboard, nel report e nei set di dati. 

Dopo aver creato un'istanza del pacchetto di contenuto, gli utenti possono accedere alle impostazioni del set di dati, incluso l'aggiornamento pianificato. Tutte le impostazioni della sicurezza a livello di riga nel set di dati **non** sono pubblicate nel pacchetto di contenuto.  

> [!NOTE]
> I pacchetti di contenuto di modello possono includere solo 1 dashboard, 1 report e 1 set di dati. Vedere l'elenco delle restrizioni nella pagina [Template Content Pack Authoring](template-content-pack-authoring.md#restrictions) (Creazione di pacchetti di contenuto modello). 
> 
> 

Per abilitare la creazione del modello per il tenant, rivolgersi all'amministratore di Power BI per abilitare l'opzione della funzionalità riportata di seguito. 

![opzionefunzionalità](media/template-content-pack-testing/featureswitch.png)

Una volta abilitata, viene visualizzata una casella di controllo nella parte inferiore della finestra ["Crea pacchetto di contenuto"](https://app.powerbi.com/groups/me/publish-content/), che consente di pubblicare un pacchetto di contenuto del modello per l'organizzazione. 

![casellacontrollo](media/template-content-pack-testing/checkbox.png)

### <a name="naming"></a>Denominazione
Si consiglia di denominare il dashboard, il report e il set di dati in modo coerente nel pacchetto di contenuto. Tali nomi sono hardcoded e saranno uguali per tutti gli utenti, quindi l'uso del nome del prodotto/dello scenario può aiutare i clienti a trovarli.

### <a name="additional-template-tips"></a>Suggerimenti aggiuntivi sui modelli
* Verificare che i parametri specificati nelle query sono significativi per gli utenti finali
* Valutare per quanto tempo l'utente finale dovrà attendere il completamento dell'aggiornamento pianificato

![creare](media/template-content-pack-testing/createtemplate.png)

<a name="submission"></a>

## <a name="submission"></a>Invio
Il processo di invio attraverso [Microsoft AppSource](https://appsource.microsoft.com/partners/list-an-app) consente di pubblicare il pacchetto di contenuto modello nella raccolta di pacchetti di contenuto del servizio in PowerBI.com, nonché di elencare il pacchetto di contenuto in [Microsoft AppSource](http://appsource.microsoft.com).

### <a name="before-submission"></a>Prima dell'invio
* Esaminare i suggerimenti di creazione per ciascuno degli elementi all'interno del pacchetto di contenuto
* Testare e connettersi con vari account e condizioni di dati (ignorare questo passaggio se è stato sviluppato un [connettore dati](https://aka.ms/DataConnectors) personalizzato).
* Esaminare tutti gli elementi visivi, controllare con attenzione la presenza di eventuali errori di ortografia
* Verificare che il pacchetto di contenuto risponda correttamente alle domande e risposte; si consiglia di testare almeno 30 domande diverse nel modello di dati (ignorare questo passaggio se è stato sviluppato un [connettore dati](https://aka.ms/DataConnectors) personalizzato).

### <a name="submission"></a>Invio
Quando si è pronti per l'invio, visitare la [pagina di invio di app](https://appsource.microsoft.com/partners/list-an-app) su AppSource e inviare le informazioni. Assicurarsi di selezionare Power BI dall'elenco dei prodotti disponibili

Il team di Power BI esaminerà l'invio e contatterà l'utente per verificare che tutti gli elementi soddisfino i requisiti di invio. Oltre a verificarne la completezza, verrà anche convalidata la qualità del dashboard e dei report forniti, assicurandosi che soddisfino lo scenario aziendale descritto nell'applicazione.

### <a name="updates"></a>Aggiornamenti
L'aggiornamento del pacchetto di contenuto segue un flusso simile a quello dell'invio originale. 

