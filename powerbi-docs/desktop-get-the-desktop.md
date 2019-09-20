---
title: Ottenere Power BI Desktop
description: Scaricare e installare Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: e7a96186fe68ed0d70de7a502e81da4f24f4d802
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903592"
---
# <a name="get-power-bi-desktop"></a>Ottenere Power BI Desktop
**Power BI Desktop** consente di creare query, modelli e report avanzati per la visualizzazione dei dati. Con **Power BI Desktop**, è possibile creare modelli di dati, creare report e condividere il proprio lavoro pubblicandolo nel servizio Power BI.  Il download di **Power BI Desktop** è gratuito.

È possibile ottenere **Power BI Desktop** in due modi, ognuno dei quali viene descritto nelle sezioni seguenti:

* **Download** diretto (pacchetto da scaricare e installare nel computer)
* Installazione come app da **Microsoft Store**

Con entrambi gli approcci si otterrà la versione più recente di **Power BI Desktop** nel computer, ma esistono alcune differenze che vale la pena osservare e che vengono descritte nelle sezioni seguenti.

## <a name="download-power-bi-desktop"></a>Scarica Power BI Desktop
Per scaricare la versione più recente di **Power BI Desktop** è possibile selezionare l'icona di download nell'angolo in alto a destra del servizio Power BI e selezionare **Power BI Desktop**.

![Scaricare la versione più recente di Power BI Desktop](media/desktop-get-the-desktop/getpbid_downloads.png)

È anche possibile scaricare la versione più recente di Power BI Desktop dalla seguente pagina di download:

* [**Download di Power BI Desktop** (entrambe le versioni a 32 e a 64 bit)](https://powerbi.microsoft.com/desktop).
  
  [![Download della versione più recente di Power BI Desktop](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Indipendentemente dal download scelto, dopo aver scaricato **Power BI Desktop** verrà chiesto di eseguire il file di installazione:

![Eseguire il file di installazione di Power BI Desktop](media/desktop-get-the-desktop/download-desktop-exe.png)

A partire dalla versione di luglio 2019, **Power BI Desktop** viene distribuito come singolo pacchetto di installazione con estensione exe che contiene tutte le lingue supportate. Sono disponibili file con estensione exe distinti per le versioni a 32 bit e a 64 bit. I pacchetti con estensione msi sono stati sospesi a partire dalla versione di settembre 2019 che richiede l'eseguibile con estensione exe per l'installazione. Questo approccio consente (soprattutto agli amministratori) di eseguire la distribuzione, gli aggiornamenti e l'installazione in modo molto più semplice e conveniente. È anche possibile usare i parametri della riga di comando per personalizzare il processo di installazione, come descritto nella sezione [Uso delle opzioni da riga di comando durante l'installazione](#using-command-line-options-during-installation) più avanti in questo articolo.

Dopo l'avvio del pacchetto di installazione, **Power BI Desktop** viene installato come applicazione ed eseguito sul desktop.

![Applicazione Power BI Desktop in esecuzione sul desktop](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> L'installazione della versione scaricata (MSI) e della versione in **Microsoft Store** di **Power BI Desktop** nello stesso computer (anche detta installazione *side-by-side*) non è supportata.
> 
> 

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installazione come app da Microsoft Store
È possibile ottenere **Power BI Desktop** anche da Microsoft Store usando il collegamento seguente:

* [Installare **Power BI Desktop** da **Microsoft Store**](http://aka.ms/pbidesktopstore)

  ![Ottenere Power BI Desktop da Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Esistono alcuni vantaggi nell'ottenere **Power BI Desktop** da Microsoft Store:

* **Aggiornamenti automatici**: Windows scarica la versione più recente automaticamente in background non appena è disponibile, in modo che la versione in uso sia sempre aggiornata.
* **Download più piccoli**: **Microsoft Store** assicura che vengano scaricati nel computer solo i componenti modificati in ogni aggiornamento, in modo da ottenere download più piccoli per ogni aggiornamento.
* **Privilegi di amministratore non necessari**: per scaricare direttamente il pacchetto e installarlo, è necessario essere un amministratore affinché l'installazione venga completata correttamente. Se si ottiene **Power BI Desktop** da Microsoft Store, il privilegio di amministratore *non* è necessario.
* **Abilitazione dell'implementazione IT**: la versione di **Microsoft Store** può essere distribuita (*implementata*) più facilmente per tutti gli utenti dell'organizzazione ed è possibile rendere disponibile **Power BI Desktop** tramite **Microsoft Store per le aziende**.
* **Rilevamento della lingua**: la versione di **Microsoft Store** include tutte le lingue supportate e controlla la lingua usata nel computer a ogni avvio. Questo influisce anche sulla localizzazione dei modelli creati in **Power BI Desktop**. Ad esempio, le gerarchie di date predefinite corrisponderanno alla lingua usata da **Power BI Desktop** quando viene creato il file con estensione pbix.

Esistono alcune considerazioni e limitazioni per l'installazione di **Power BI Desktop** da Microsoft Store, che includono quanto segue:

* Se si usa il connettore SAP, potrebbe essere necessario spostare i file del driver SAP per la cartella *Windows\System32*.
* L'installazione di **Power BI Desktop** da Microsoft Store non copia le impostazioni utente dalla versione con estensione exe. Potrebbe essere necessario ristabilire la connessione alle origini dati recenti e immettere nuovamente le credenziali dell'origine dati. 

> [!NOTE]
> L'installazione della versione scaricata (MSI) e della versione in **Microsoft Store** di **Power BI Desktop** nello stesso computer (anche detta installazione *side-by-side*) non è supportata. È necessario disinstallare manualmente **Power BI Desktop** prima di scaricarlo da **Microsoft Store**
> 
> [!NOTE]
> La versione Server di report di Power BI di **Power BI Desktop** è un'installazione separata e diversa rispetto alle versioni illustrate in questo articolo. Per informazioni sulla versione Server di report di **Power BI Desktop**, vedere [Creare un report di Power BI per il Server di report di Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Uso di Power BI Desktop
Quando si avvia **Power BI Desktop** viene visualizzata una *schermata iniziale*.

![Schermata di benvenuto in Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Se si usa per la prima volta **Power BI Desktop**, ovvero se l'installazione non è un aggiornamento, verrà richiesta la compilazione di un modulo e la risposta ad alcune domande o sarà necessario accedere al **servizio Power BI** per poter continuare.

Da qui è possibile iniziare a creare modelli di dati o report, quindi condividerli con altri utenti nel servizio Power BI. Vedere i collegamenti **Altre informazioni** alla fine di questo articolo per i collegamenti a guide sulle attività iniziali in **Power BI Desktop**.

## <a name="minimum-requirements"></a>Requisiti minimi
Di seguito sono elencati i requisiti minimi per l'esecuzione di **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 o versioni successive
* .NET 4.5
* Internet Explorer 10 o versioni successive
* **Memoria (RAM):** almeno 1 GB disponibile, 1,5 GB o più consigliati.
* **Schermo:** almeno 1440x900 o 1600x900 (16:9) consigliato. Risoluzioni inferiori, ad esempio 1024 x 768 o 1280 x 800 non sono consigliate, perché alcuni controlli (ad esempio la chiusura della schermata iniziale) vengono visualizzati oltre tali risoluzioni.
* **Impostazioni dello schermo di Windows:** se le impostazioni di visualizzazione sono configurate per la modifica delle dimensioni di testo, app e altri elementi fino a un valore superiore al 100%, è possibile che non si riesca a visualizzare alcune finestre di dialogo che devono essere chiuse o a cui occorre rispondere per poter continuare a usare **Power BI Desktop**. Se si verifica questo problema, controllare le **Impostazioni dello schermo** passando a **Impostazioni > Sistema > Schermo** in Windows, quindi usare il dispositivo di scorrimento per ripristinare il valore 100% per le impostazioni di visualizzazione.
* **CPU:** 1 gigahertz (GHz) o più veloce, consigliato processore x86 o x64 bit.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

Microsoft desidera offrire un'esperienza straordinaria con Power BI Desktop. In alcuni casi potrebbe verificarsi un problema con Power BI Desktop, quindi in questa sezione vengono indicate le soluzioni o forniti suggerimenti per risolvere i problemi che potrebbero verificarsi. 

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Installazione di Power BI Desktop su computer remoti

Se si distribuisce Power BI Desktop agli utenti con uno strumento che richiede un file di installazione Windows (file con estensione msi), è possibile estrarre il file con estensione msi dal file di installazione con estensione exe di Power BI Desktop. A tale scopo è possibile usare strumenti di terze parti, ad esempio WiX Toolset.

> [!NOTE]
> In quanto prodotto di terze parti, le opzioni di WiX Toolset possono subire modifiche senza preavviso. Per informazioni aggiornate, consultare la documentazione del prodotto e contattare la lista di distribuzione per assistenza.

* Nel computer in cui è stato scaricato il programma di installazione di Power BI Desktop scaricare e installare la versione più recente di WiX Toolset dal sito Web WiX all'indirizzo https://wixtoolset.org/.
* Aprire una finestra della riga di comando come amministratore e passare alla cartella in cui è stato installato WiX Toolset.
* Eseguire il comando seguente: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Ad esempio, eseguire:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

* La cartella di output conterrà una cartella denominata *AttachedContainer* che include i file con estensione msi.




### <a name="using-command-line-options-during-installation"></a>Uso delle opzioni da riga di comando durante l'installazione 

Quando si installa Power BI Desktop, è possibile impostare le proprietà e le opzioni usando le opzioni da riga di comando. Questa modalità è particolarmente utile per gli amministratori che gestiscono o facilitano l'installazione di Power BI Desktop in più organizzazioni. Queste opzioni si applicano alle installazioni di pacchetti con estensione msi ed exe. 


|Opzione da riga di comando  |Comportamento  |
|---------|---------|
|-q, -quiet, -s, -silent     |esegue l'installazione in modo invisibile all'utente         |
|-passive     |visualizza solo l'indicatore di stato durante l'installazione         |
|-norestart     |disattiva il requisito di riavvio del computer         |
|-forcerestart     |riavvia il computer dopo l'installazione senza chiedere conferma         |
|-promptrestart     |chiede conferma all'utente se è necessario riavviare il computer (impostazione predefinita)         |
|-l<>, -log<>     |registra l'installazione in un file specifico, con il file definito in <>         |
|-uninstall     |disinstalla Power BI Desktop         |
|-repair     |ripristina l'installazione (o esegue l'installazione se il pacchetto non è installato)         |
|-package, -update     |installa Power BI Desktop (impostazione predefinita, purché l'opzione -uninstall o -repair non sia specificata)         |

È anche possibile usare i **parametri di sintassi** seguenti, che sono specificati con la sintassi "PROPERTY=VALUE":


|Parametro  |Significato  |
|---------|---------|
|ACCEPT_EULA     |Richiede un valore pari a 1 per accettare automaticamente le condizioni di licenza         |
|ENABLECXP     |Il valore 1 viene registrato nel programma di analisi dell'utilizzo che acquisisce i dati di telemetria sull'utilizzo del prodotto         |
|INSTALLDESKTOPSHORTCUT     |Il valore 1 aggiunge un collegamento al desktop         |
|INSTALLLOCATION     |Percorso file in cui si vuole eseguire l'installazione         |
|LANGUAGE     |Codice impostazioni locali, ad esempio en-US, de-DE, pr-BR, per forzare la lingua predefinita dell'applicazione. Se non viene specificata una lingua, Power BI Desktop visualizza la lingua del sistema operativo Windows. Questa impostazione può essere modificata dall'utente nella finestra di dialogo Opzioni.         |
|REG_SHOWLEADGENDIALOG     |Il valore 0 disabilita la visualizzazione della finestra di dialogo visualizzata prima dell'accesso a Power BI Desktop         |




Ad esempio, è possibile usare il parametro con la sintassi seguente per eseguire l'installazione senza alcuna interfaccia utente usando la lingua tedesca: 

```“-quiet LANG=de-DE ACCEPT_EULA=1”```


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemi nell'uso delle versioni precedenti di Power BI Desktop

Alcuni utenti rilevano un errore simile al seguente quando usano una versione obsoleta di **Power BI Desktop**: 

    "We weren't able to restore the saved database to the model" 

In genere l'aggiornamento alla versione corrente di Power BI Desktop risolve il problema.

### <a name="disabling-notifications"></a>Disabilitazione delle notifiche
È consigliabile eseguire l'aggiornamento alla versione più recente di Power BI Desktop per sfruttare i miglioramenti apportati alle funzionalità, alle prestazioni e alla stabilità e le altre novità. Alcune organizzazioni potrebbero preferire che gli utenti non eseguano l'aggiornamento a ogni nuova versione. È possibile disabilitare le notifiche modificando il Registro di sistema seguendo questa procedura:

1. Nell'editor del Registro di sistema passare a *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop*
2. Creare una nuova voce con le impostazioni seguenti: *REG_DWORD: DisableUpdateNotification*
3. Impostare il valore della nuova voce su **1**.

Per rendere effettiva la modifica, sarà necessario riavviare il computer.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop viene caricato con una schermata parziale

In alcune circostanze, tra cui determinate configurazioni di risoluzione dello schermo, Power BI Desktop potrebbe eseguire il rendering del contenuto con grandi aree nere. Ciò è in genere dovuto ad aggiornamenti recenti del sistema operativo che influiscono sulla modalità di rendering degli elementi e non è un risultato diretto del modo in cui Power BI Desktop presenta il contenuto. Le grandi aree nere non sono comunque oggetti visivi piacevoli, quindi per risolvere questo problema, eseguire questa procedura:

1. Fare clic su Start e digitare *sfocate* nella barra di ricerca che viene visualizzata.
2. Nella finestra di dialogo visualizzata selezionare l'opzione *Risolvere i problemi delle app che sono sfocate.*
3. Riavviare Power BI Desktop.

Questo problema potrebbe risolversi dopo il rilascio degli aggiornamenti successivi di Windows. 
 

## <a name="next-steps"></a>Passaggi successivi
Dopo aver installato **Power BI Desktop**, il contenuto seguente consente di svolgere rapidamente le attività iniziali:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)   

