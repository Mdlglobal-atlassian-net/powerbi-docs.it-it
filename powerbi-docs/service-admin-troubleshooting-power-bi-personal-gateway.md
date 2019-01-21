---
title: Risoluzione dei problemi relativi a Power BI Gateway - Personal
description: Risoluzione dei problemi relativi a Power BI Gateway - Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 642bd39cb9348bae2a1f30dbc9ee026e11ff7401
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284519"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Risoluzione dei problemi relativi a Power BI Gateway - Personal
Di seguito sono illustrati alcuni problemi comuni che possono verificarsi quando si usa Power BI Gateway - Personal.

> [!NOTE]
> La versione corrente del gateway per uso personale è **Gateway dati locale (personale)**. Aggiornare l'installazione in modo da usare tale versione.
> 
> 

## <a name="update-to-the-latest-version"></a>Aggiornare alla versione più recente
Quando la versione del gateway non è aggiornata, possono verificarsi molti problemi.  In generale, è consigliabile assicurarsi di usare sempre la versione più recente.  Se il gateway non è stato aggiornato da un mese o più, potrebbe essere utile provare a installare la versione più recente del gateway e provare a riprodurre il problema.

## <a name="installation"></a>Installazione
**Il gateway personale è a 64 bit:** se la versione del computer è a 32 bit, non sarà possibile installare il gateway personale. Il sistema operativo deve essere a 64 bit. È necessario installare una versione a 64 bit di Windows o installare il gateway personale in un computer a 64 bit.

**Personal Gateway non viene installato come servizio anche se l'accesso al computer è stato effettuato come amministratore locale**: l'installazione può non riuscire se l'utente appartiene al gruppo Administrators locale del computer, ma i criteri di gruppo non permettono al nome utente di accedere come servizio.  Assicurarsi che il criterio di gruppo consenta a un utente di accedere come servizio. Microsoft sta lavorando a una soluzione del problema. [Altre informazioni](https://technet.microsoft.com/library/cc739424.aspx)

**Timeout dell'operazione**: è frequente se il computer (computer fisico o macchina virtuale) in cui si sta installando il gateway personale ha un processore a core singolo. Chiudere tutte le applicazioni e disattivare tutti i processi non essenziali, quindi ripetere l'installazione.

**Gateway di gestione dati o Analysis Services Connector non può essere installato nello stesso computer del gateway personale**: se è già installato Analysis Services Connector o Gateway di gestione dati, è necessario disinstallarlo prima di installare il gateway personale.

> [!NOTE]
> Se si verifica un problema durante l'installazione, i log del programma di installazione possono fornire informazioni per la risoluzione. Per altre informazioni, vedere [Log del programma di installazione](#SetupLogs).
> 
> 

 **Configurazione proxy** È possibile riscontrare problemi durante la configurazione del gateway personale se l'ambiente richiede l'uso di un proxy. Per altre informazioni su come configurare le informazioni sul proxy, vedere [Configurazione delle impostazioni proxy per Power BI Gateway](service-gateway-proxy.md)

## <a name="schedule-refresh"></a>Pianifica aggiornamenti
**Errore: Le credenziali archiviate nel cloud mancano.**

Questo errore viene visualizzato in Impostazioni per \<set di dati\> se è stato impostato un aggiornamento pianificato ed è stato disinstallato e poi reinstallato il gateway personale. Quando si disinstalla un gateway personale, le credenziali dell'origine dati per un set di dati configurato per l'aggiornamento vengono rimosse dal servizio Power BI.

**Soluzione:** In Power BI, passare alle impostazioni di aggiornamento per un set di dati. In Gestisci origini dati fare clic su Modifica credenziali per ogni origine dati con errori e accedere di nuovo all'origine dati.

**Errore: Le credenziali fornite per il set di dati non sono valide. Aggiornare le credenziali tramite un aggiornamento o nella finestra di dialogo Impostazioni origine dati per continuare.**

**Soluzione**: se viene visualizzato un messaggio relativo alle credenziali:

* Verificare che i nomi utente e le password usati per l'accesso alle origini dati siano aggiornati. In Power BI andare nelle impostazioni di aggiornamento del set di dati. In Gestisci origini dati fare clic su Modifica credenziali per aggiornare la credenziali per l'origine dati.
* I mashup tra un'origine cloud e un'origine locale, in una singola query, non renderanno possibile l'aggiornamento di Personal Gateway se una delle origini utilizza OAuth per l'autenticazione, ad esempio un mashup tra CRM Online e un Server SQL locale. Questo mashup avrà esito negativo poiché CRM Online richiede OAuth.
  
  Si tratta di un problema noto e analizzato. Per risolvere il problema, eseguire una query separata per l'origine cloud e l'origine locale e utilizzare una query di unione o di accodamento per combinarle.

**Errore: Origine dati non supportata.**

**Soluzione:** Un messaggio relativo a un'origine dati non supportata nelle impostazioni Pianifica aggiornamento può indicare: 

* L'origine dati non è attualmente supportata per l'aggiornamento in Power BI. 
* La cartella di lavoro di Excel non contiene un modello di dati, ma solo dati del foglio di lavoro. Power BI attualmente supporta l'aggiornamento solo se la cartella di lavoro di Excel caricata contiene un modello di dati. Quando si importano i dati con Power Query in Excel, verificare che sia selezionata l'opzione di caricamento dati nel modello di dati. In questo modo, i dati vengono importati in un modello di dati. 

**Errore: [Non è possibile combinare i dati] &lt;parte della query&gt;/&lt;…&gt;/&lt;…&gt; accede a origini dati i cui livelli di privacy non possono essere usati contemporaneamente. Ricompilare la combinazione di dati.**

**Soluzione**: questo errore è dovuto a restrizioni a livello di privacy e ai tipi di origini dati in uso.

**Errore: Errore dell'origine dati: Non è possibile convertire il valore "\[Table\]" nel tipo Table.**

**Soluzione**: questo errore è dovuto a restrizioni a livello di privacy e ai tipi di origini dati in uso.

**Errore: Non è disponibile spazio sufficiente per questa riga.**

Questo accade in presenza di una riga singola le cui dimensioni superano 4 MB. È necessario determinare quale sia la riga dall'origine dati e tentare di filtrarla o di ridurne le dimensioni.

## <a name="data-sources"></a>Origini dati
**Provider di dati mancante**: il gateway personale è solo a 64 bit. Richiede una versione a 64 bit dei provider di dati installata nello stesso computer del gateway personale. Ad esempio, se l'origine dati nel set di dati è Microsoft Access, è necessario installare un provider ACE a 64 bit nello stesso computer in cui è stato installato il gateway personale.  

>[!NOTE]
>Se è in uso la versione di Excel a 32 bit, non è possibile installare un provider ACE a 64 bit nello stesso computer.

**L'autenticazione di Windows non è supportata per il database Access**: attualmente Power BI supporta solo l'autenticazione anonima per il database di Access. Microsoft sta lavorando per consentire l'autenticazione di Windows per il database di Access.

**Errore di accesso quando si immettono le credenziali per un'origine dati**: se viene visualizzato un errore simile a questo quando si immettono le credenziali di Windows per un'origine dati, è possibile che sia in uso una versione precedente del gateway personale. [Installare la versione più recente di Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Errore: Errore di accesso quando si seleziona l'autenticazione di Windows per un'origine dati usando ACE OLEDB** : se viene visualizzato l'errore seguente quando si immettono le credenziali per un'origine dati usando un provider ACE OLEDB:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Attualmente, Power BI non supporta l'autenticazione di Windows per un'origine dati tramite un provider ACE OLEDB.

**Soluzione:** per risolvere questo errore, è possibile selezionare l'autenticazione anonima. Per il provider ACE OLEDB legacy, le credenziali anonime sono equivalenti alle credenziali di Windows.

## <a name="tile-refresh"></a>Aggiornamento del riquadro
Se si riceve un errore con l’aggiornamento dei riquadri del dashboard, consultare l'articolo seguente.

[Risoluzione degli errori del riquadro](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Strumenti per la risoluzione dei problemi
### <a name="refresh-history"></a>Cronologia aggiornamenti
**Cronologia aggiornamenti** consente di visualizzare gli errori che si sono verificati, nonché di fornire dati utili nel caso in cui sia necessario creare una richiesta di supporto. È possibile visualizzare sia gli aggiornamenti pianificati che quelli su richiesta. Per accedere alla **Cronologia aggiornamenti**, eseguire le operazioni seguenti.

1. In **Set di dati** nel riquadro di spostamento di Power BI selezionare un set di dati &gt; Apri menu &gt;**Pianifica aggiornamento**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
2. In **Impostazioni per...** &gt; **Pianifica aggiornamento** selezionare **Cronologia aggiornamenti**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registri eventi
Sono disponibili molti registri eventi che posso fornire informazioni. I primi due, **Gateway di gestione dati** e **PowerBIGateway**, sono presenti se si è un amministratore del computer.  Se non si è un amministratore e si sta usando il Gateway personale, le voci verranno visualizzate all'interno del registro **Applicazione** .

I registri **Gateway di gestione dati** e **PowerBIGateway** sono presenti in **Registri applicazioni e servizi**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Traccia di Fiddler
[Fiddler](http://www.telerik.com/fiddler) è uno strumento gratuito di Telerik che monitora il traffico HTTP.  È possibile visualizzare il traffico dal servizio Power BI al computer client e viceversa. Potrebbero essere illustrati errori e altre informazioni correlate.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Log del programma di installazione
Se l'installazione di **Personal Gateway** non riesce, viene visualizzato un collegamento al log del programma di installazione che potrebbe contenere i dettagli dell'errore. Si tratta di log di Windows Installer, detti anche log di MSI. Possono essere piuttosto complessi e difficili da leggere. In genere l'errore risultante si trova nella parte inferiore, ma stabilire la causa dell'errore non è immediato. Potrebbe essere il risultato di errori in un altro log o di un errore in un punto precedente del log.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

In alternativa è possibile accedere alla **cartella temporanea** (%temp%) e cercare i file che iniziano con **Power\_BI\_**.

> [!NOTE]
> quando si passa a %temp%, si potrebbe accedere a una sottocartella della cartella temporanea.  I file **Power\_BI\_** si trovano nella radice della directory temporanea.  Potrebbe essere necessario andare su di uno o due livelli.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Passaggi successivi
[Configurazione delle impostazioni del proxy per Power BI Gateway](service-gateway-proxy.md)  
[Aggiornamento dei dati](refresh-data.md)  
[Power BI Gateway - Personale](service-gateway-personal-mode.md)  
[Risoluzione degli errori del riquadro](refresh-troubleshooting-tile-errors.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

