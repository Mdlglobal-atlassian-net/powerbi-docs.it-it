---
title: Risoluzione dei problemi relativi a Power BI Gateway (modalità personale)
description: Risoluzione dei problemi relativi a Power BI Gateway (modalità personale)
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8916d92eef86be601ceb21112209ab7daa736c11
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543530"
---
# <a name="troubleshooting-power-bi-gateway-personal-mode"></a>Risoluzione dei problemi relativi a Power BI Gateway (modalità personale)

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Le sezioni seguenti descrivono alcuni problemi comuni che possono verificarsi quando si usa il gateway dati locale (modalità personale) di Power BI.

## <a name="update-to-the-latest-version"></a>Aggiornare alla versione più recente

La versione corrente del gateway per uso personale è il gateway dati locale (modalità personale). Aggiornare l'installazione per usare tale versione.

Quando la versione del gateway non è aggiornata, possono verificarsi diversi problemi. In generale, è consigliabile assicurarsi di usare sempre la versione più recente. Se il gateway non è stato aggiornato da un mese o più, può essere utile installare la versione più recente. Verificare quindi se è possibile riprodurre il problema.

## <a name="installation"></a>Installazione
**Il gateway (modalità personale) funziona con le versioni a 64 bit:** se il computer in uso è a 32 bit, non è possibile installare il gateway (modalità personale). Il sistema operativo deve essere una versione a 64 bit. Installare una versione a 64 bit di Windows o installare il gateway (modalità personale) in un computer a 64 bit.

**L'installazione del gateway (modalità personale) come servizio non riesce anche se si è un amministratore locale del computer:** l'installazione può non riuscire se l'utente appartiene al gruppo Administrators locale del computer ma i criteri di gruppo non consentono al nome utente l'accesso come servizio. Assicurarsi che i criteri di gruppo consentano a un utente di accedere come servizio. Microsoft sta lavorando a una soluzione del problema. Per altre informazioni, vedere [Aggiungere il diritto di accesso come servizio a un account](https://technet.microsoft.com/library/cc739424.aspx).

**Timeout dell'operazione:** questo messaggio è frequente se il computer (computer fisico o macchina virtuale) in cui si sta installando il gateway (modalità personale) ha un processore a core singolo. Chiudere tutte le applicazioni e disattivare tutti i processi non essenziali, quindi ripetere l'installazione.

**Non è possibile installare il gateway di gestione dati o Analysis Services Connector nello stesso computer del gateway (modalità personale):** se il gateway di gestione dati o Analysis Services Connector è già installato, è prima necessario disinstallarlo. Provare quindi a installare il gateway (modalità personale).

> [!NOTE]
> Se si verifica un problema durante l'installazione, i log del programma di installazione possono fornire informazioni per la risoluzione. Per altre informazioni, vedere [Log di installazione](#SetupLogs).
> 
> 

 **Configurazione del proxy:** potrebbero verificarsi problemi nella configurazione del gateway (modalità personale) se l'ambiente richiede l'uso di un proxy. Per altre informazioni su come configurare le informazioni sul proxy, vedere [Configurare le impostazioni proxy per il gateway dati locale](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Pianifica aggiornamenti
**Errore: Le credenziali archiviate nel cloud mancano.**

Questo errore viene visualizzato nelle impostazioni del \<set di dati\> se è stato impostato un aggiornamento pianificato e quindi il gateway (modalità personale) è stato disinstallato e reinstallato. Quando si disinstalla un gateway (modalità personale), le credenziali dell'origine dati per un set di dati configurato per l'aggiornamento vengono rimosse dal servizio Power BI.

**Soluzione:** In Power BI, passare alle impostazioni di aggiornamento per un set di dati. In **Gestisci origini dati** selezionare **Modifica credenziali** per ogni origine dati con errori. Accedere quindi di nuovo all'origine dati.

**Errore: Le credenziali fornite per il set di dati non sono valide. Aggiornare le credenziali tramite un aggiornamento o nella finestra di dialogo Impostazioni origine dati per continuare.**

**Soluzione:** se viene visualizzato un messaggio relativo alle credenziali:

* I nomi utente e le password usati per l'accesso alle origini dati non sono aggiornati. In Power BI andare nelle impostazioni di aggiornamento del set di dati. In **Gestisci origini dati** selezionare **Modifica credenziali** per aggiornare le credenziali per l'origine dati.
* I mashup tra un'origine cloud e un'origine locale, in una singola query, non vengono aggiornati nel gateway (modalità personale) se una delle origini usa OAuth per l'autenticazione. Un esempio di questo problema è rappresentato da un mashup tra CRM Online e un'istanza di SQL Server locale. Il mashup ha esito negativo poiché CRM Online richiede OAuth.
  
  Si tratta di un problema noto e in fase di analisi. Per risolvere il problema, eseguire una query separata per l'origine cloud e l'origine locale. Quindi usare una query di unione o di accodamento per combinarle.

**Errore: Origine dati non supportata.**

**Soluzione:** Se viene visualizzato un messaggio relativo a un'origine dati non supportata nelle impostazioni in **Pianifica aggiornamenti** può indicare: 

* L'origine dati non è attualmente supportata per l'aggiornamento in Power BI. 
* La cartella di lavoro di Excel non contiene un modello di dati, ma solo dati del foglio di lavoro. Power BI attualmente supporta l'aggiornamento solo se la cartella di lavoro di Excel caricata contiene un modello di dati. Quando si importano i dati usando Power Query in Excel, scegliere l'opzione **Carica** per caricare i dati in un modello di dati. Questa opzione garantisce che i dati vengano importati in un modello di dati. 

**Errore: [Non è possibile combinare i dati] &lt;parte della query&gt;/&lt;…&gt;/&lt;…&gt; accede a origini dati i cui livelli di privacy non possono essere usati contemporaneamente. Ricompilare la combinazione di dati.**

**Soluzione:** questo errore è dovuto a restrizioni a livello di privacy e ai tipi di origini dati in uso.

**Errore: Errore dell'origine dati: Non è possibile convertire il valore "\[Table\]" nel tipo Table.**

**Soluzione:** questo errore è dovuto a restrizioni a livello di privacy e ai tipi di origini dati in uso.

**Errore: Non è disponibile spazio sufficiente per questa riga.**

**Soluzione:** Questo errore si verifica in presenza di una riga singola le cui dimensioni superano 4 MB. Individuare la riga dell'origine dati e cercare di filtrarla o di ridurne le dimensioni.

## <a name="data-sources"></a>Origini dati
**Provider di dati mancante:** il gateway (modalità personale) funziona solo con le versioni a 64 bit. Richiede una versione a 64 bit dei provider di dati installata nello stesso computer del gateway (modalità personale). Se, ad esempio, l'origine dati nel set di dati è Microsoft Access, è necessario installare il provider ACE a 64 bit nello stesso computer in cui è stato installato il gateway (modalità personale). 

>[!NOTE]
>Se si usa una versione di Excel a 32 bit, non è possibile installare un provider ACE a 64 bit nello stesso computer.

**L'autenticazione di Windows non è supportata per il database di Access:** attualmente Power BI supporta solo l'autenticazione anonima per il database di Access.

**Errore: Errore di accesso quando si immettono le credenziali per un'origine dati:** se viene visualizzato un errore simile al seguente quando si immettono le credenziali di Windows per un'origine dati: 

  ![Messaggio di errore relativo alle credenziali di Windows](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

Potrebbe essere ancora in uso una versione precedente del gateway (modalità personale). 

**Soluzione:** per altre informazioni, vedere [Installare la versione più recente di Power BI Gateway (modalità personale)](https://powerbi.microsoft.com/gateway/).

**Errore: Errore di accesso quando si seleziona l'autenticazione di Windows per un'origine dati con un provider ACE OLEDB:** se si verifica l'errore seguente quando si immettono le credenziali per un'origine dati con un provider ACE OLEDB:

![Messaggio di errore relativo alle credenziali dell'origine dati](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI attualmente non supporta l'autenticazione di Windows per un'origine dati con un provider ACE OLEDB.

**Soluzione:** per risolvere questo errore, selezionare **Autenticazione anonima**. Per un provider ACE OLEDB legacy, le credenziali anonime equivalgono alle credenziali di Windows.

## <a name="tile-refresh"></a>Aggiornamento del riquadro
Se viene visualizzato un errore quando vengono aggiornati i riquadri del dashboard, vedere [Risoluzione dei problemi dei riquadri](refresh-troubleshooting-tile-errors.md).

## <a name="tools-for-troubleshooting"></a>Strumenti per la risoluzione dei problemi
### <a name="refresh-history"></a>Cronologia aggiornamenti
**Cronologia aggiornamenti** consente di visualizzare gli errori che si sono verificati e offre dati utili nel caso sia necessario creare una richiesta di supporto. È possibile visualizzare sia gli aggiornamenti pianificati che quelli su richiesta. Ecco come accedere a **Cronologia aggiornamenti**.

1. In **Set di dati** nel riquadro di spostamento di Power BI selezionare un set di dati. Aprire il menu e selezionare **Pianifica aggiornamenti**.

   ![Selezionare Pianifica aggiornamenti](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. In **Impostazioni per** selezionare **Cronologia aggiornamenti**. 

   ![Selezionare Cronologia aggiornamenti](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![Informazioni della cronologia aggiornamenti](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registri eventi
Diversi registri eventi possono offrire informazioni. I primi due, **Gateway di gestione dati** e **PowerBIGateway**, sono disponibili se si è un amministratore del computer. Se non si è un amministratore e si sta usando il gateway dati (modalità personale), è possibile visualizzare le voci di log nel log **Applicazione**.

I registri **Gateway di gestione dati** e **PowerBIGateway** sono presenti in **Registri applicazioni e servizi**.

![Log Gateway di gestione dati e PowerBIGateway](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Traccia di Fiddler
[Fiddler](http://www.telerik.com/fiddler) è uno strumento gratuito di Telerik che monitora il traffico HTTP. È possibile visualizzare la comunicazione con il servizio Power BI dal computer client. La comunicazione potrebbe visualizzare errori e altre informazioni correlate.

![Traccia di Fiddler](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Log di installazione
Se l'installazione del gateway (modalità personale) non riesce, viene visualizzato un collegamento al log di installazione. che potrebbe contenere i dettagli dell'errore. Si tratta di log di Windows Installer, chiamati anche log di MSI. Possono essere piuttosto complessi e difficili da leggere. In genere l'errore risultante si trova nella parte inferiore, ma stabilire la causa dell'errore non è immediato. Potrebbe essere il risultato di errori in un altro log. In alternativa, potrebbe dipendere da un errore precedente nel log.

![Collegamento al log di installazione](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

In alternativa, è possibile passare alla cartella temporanea (%temp%) e cercare i file che iniziano con *Power\_BI\_* .

> [!NOTE]
> Quando si passa a %temp%, si potrebbe accedere a una sottocartella della cartella temporanea. I file *Power\_BI\_* si trovano nella radice della directory temporanea. Potrebbe essere necessario salire di uno o due livelli.
> 
> 

![Cartella temporanea](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Passaggi successivi
- [Configurare le impostazioni proxy per il gateway dati locale](/data-integration/gateway/service-gateway-proxy)- [Aggiornamento dei dati](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [Risoluzione degli errori del riquadro](refresh-troubleshooting-tile-errors.md)  
- [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md) 
 
Altre domande? Provare a chiedere alla [community di Power BI](http://community.powerbi.com/).

