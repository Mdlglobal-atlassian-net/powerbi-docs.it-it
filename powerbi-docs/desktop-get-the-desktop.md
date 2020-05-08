---
title: Ottenere Power BI Desktop
description: Scaricare e installare Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 1d61723b08c26197d94b53188b741fd01d47a620
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78401187"
---
# <a name="get-power-bi-desktop"></a>Ottenere Power BI Desktop
Power BI Desktop consente di creare query, modelli e report avanzati per la visualizzazione dei dati. Con Power BI Desktop, è possibile creare modelli di dati e report, nonché condividere il proprio lavoro pubblicandolo nel servizio Power BI. Il download di Power BI Desktop è gratuito.

È possibile ottenere Power BI Desktop in due modi, ognuno dei quali viene descritto nelle sezioni seguenti:

* [Installazione come app da Microsoft Store](#install-as-an-app-from-the-microsoft-store).
* [Download diretto, come eseguibile da scaricare e installare nel computer](#download-power-bi-desktop-directly).

Entrambi gli approcci consentono di installare la versione più recente di Power BI Desktop nel computer, ma vi sono alcune differenze che vale la pena osservare, come descritto nelle sezioni seguenti.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installazione come app da Microsoft Store
È possibile accedere alla versione più recente di Power BI Desktop da Microsoft Store in diversi modi. 

1. Per aprire la pagina di **Power BI Desktop** di Microsoft Store, usare una delle opzioni seguenti:

   - Aprire un browser e passare direttamente alla [pagina Power BI Desktop](https://aka.ms/pbidesktopstore) di Microsoft Store.

    - Dal [servizio Power BI](https://docs.microsoft.com/power-bi/service-get-started) selezionare l'icona **Download** nell'angolo in alto a destra e quindi selezionare **Power BI Desktop**.

      ![Scaricare Power BI Desktop dal servizio Power BI](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Passare alla [pagina del prodotto Power BI Desktop](https://powerbi.microsoft.com/desktop/) e quindi selezionare **Scarica gratis**.
  
2. Quando viene visualizzata la pagina **Power BI Desktop** di Microsoft Store, selezionare **Installa**.

     ![Ottenere Power BI Desktop da Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Il download di Power BI Desktop da Microsoft Store presenta alcuni vantaggi:

* **Aggiornamenti automatici**: Windows scarica la versione più recente automaticamente in background non appena è disponibile, in modo che la versione in uso sia sempre aggiornata.
* **Download più piccoli**: Microsoft Store assicura che vengano scaricati nel computer solo i componenti modificati in ogni aggiornamento, in modo da ottenere download più piccoli per ogni aggiornamento.
* **Privilegi di amministratore non necessari**: quando si scarica direttamente il pacchetto, per la corretta installazione è necessario essere un amministratore. Se si ottiene Power BI Desktop da Microsoft Store, i privilegi di amministratore *non* sono necessari.
* **Abilitazione dell'implementazione IT**: con Microsoft Store per le aziende è possibile distribuire, o *implementare*, più facilmente Power BI Desktop per tutti gli utenti dell'organizzazione

* **Rilevamento della lingua**: la versione di Microsoft Store include tutte le lingue supportate e controlla la lingua usata nel computer a ogni avvio. Questo supporto per le lingue influisce anche sulla localizzazione dei modelli creati in Power BI Desktop. Ad esempio, le gerarchie di date predefinite corrispondono alla lingua utilizzata da Power BI Desktop al momento della creazione del file con estensione pbix.

All'installazione di Power BI Desktop da Microsoft Store si applicano le considerazioni e limitazioni seguenti:

* Se si usa il connettore SAP, potrebbe essere necessario spostare i file del driver SAP per la cartella *Windows\System32*.
* L'installazione di Power BI Desktop da Microsoft Store non copia le impostazioni utente dalla versione con estensione exe. Potrebbe essere necessario ristabilire la connessione alle origini dati recenti e immettere nuovamente le credenziali dell'origine dati. 

> [!NOTE]
> La versione Server di report di Power BI di Power BI Desktop è un'installazione separata e diversa rispetto alle versioni illustrate in questo articolo. Per informazioni sulla versione Server di report di Power BI Desktop, vedere [Creare un report di Power BI per Server di report di Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Download diretto di Power BI Desktop
  
  Per scaricare il file eseguibile di Power BI Desktop dall'Area download, selezionare **Scarica** dalla [pagina dell'Area download](https://www.microsoft.com/download/details.aspx?id=58494). Specificare quindi un file di installazione a 32 o 64 bit da scaricare.

  ![Specificare il file di installazione di Power BI Desktop](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Installare Power BI Desktop dopo il download
Al termine del download viene chiesto di eseguire il file di installazione.

A partire dalla versione di luglio 2019, Power BI Desktop viene fornito come singolo pacchetto di installazione con estensione exe contenente tutte le lingue supportate, con un file .exe separato per le versioni a 32 e 64 bit. I pacchetti con estensione msi sono stati sospesi a partire dalla versione di settembre 2019, che richiede il file .exe per l'installazione. Questo approccio consente (soprattutto agli amministratori) di eseguire la distribuzione, gli aggiornamenti e l'installazione in modo molto più semplice e conveniente. È anche possibile usare i parametri della riga di comando per personalizzare il processo di installazione, come descritto in [Uso delle opzioni da riga di comando durante l'installazione](#using-command-line-options-during-installation).

Dopo l'avvio del pacchetto di installazione, Power BI Desktop viene installato come applicazione ed eseguito sul desktop.

![Eseguire l'installazione di Power BI Desktop](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> L'installazione della versione scaricata (con estensione msi) e della versione in Microsoft Store di Power BI Desktop nello stesso computer (talvolta definita installazione *side-by-side*) non è supportata. Disinstallare manualmente Power BI Desktop prima di scaricarlo da Microsoft Store.
> 

## <a name="using-power-bi-desktop"></a>Uso di Power BI Desktop
Quando si avvia Power BI Desktop, viene visualizzata una schermata iniziale.

![Schermata di benvenuto in Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Se si usa Power BI Desktop per la prima volta, ovvero l'installazione non è un aggiornamento, viene chiesto di compilare un modulo o di accedere al servizio Power BI prima di poter continuare.

Da qui è possibile iniziare a creare modelli di dati o report, quindi condividerli con altri utenti nel servizio Power BI. Vedere la sezione [Passaggi successivi](#next-steps) per i collegamenti alle guide contenenti informazioni utili per iniziare a usare Power BI Desktop.

## <a name="minimum-requirements"></a>Requisiti minimi
Di seguito sono elencati i requisiti minimi per l'esecuzione di Power BI Desktop:

* Windows 7 / Windows Server 2008 R2 o versioni successive
* .NET 4.5
* Internet Explorer 10 o versioni successive
* Memoria (RAM): almeno 1 GB disponibile, 1,5 GB o più consigliati.
* Visualizzazione: almeno 1440x900 o 1600x900 (16:9) consigliato. Le risoluzioni più basse come 1024x768 o 1280x800 non sono consigliate perché alcuni controlli (ad esempio la chiusura della schermata iniziale) vengono visualizzati con risoluzioni più alte.
* Impostazioni di visualizzazione di Windows: se si configurano le impostazioni di visualizzazione per la modifica delle dimensioni di testo, app e altri elementi fino a un valore superiore al 100%, potrebbe non essere possibile visualizzare alcune finestre di dialogo con cui si deve interagire per continuare a usare Power BI Desktop. Se si verifica questo problema, controllare le impostazioni dello schermo passando a **Impostazioni** > **Sistema** > **Schermo** in Windows, quindi usare il dispositivo di scorrimento per ripristinare il valore 100% per le impostazioni di visualizzazione.
* CPU: 1 gigahertz (GHz) o più veloce. È consigliato un processore x86 a 32 o 64 bit.

## <a name="considerations-and-limitations"></a>Considerazioni e limiti

Microsoft intende offrire un'esperienza straordinaria con Power BI Desktop. Poiché in alcuni casi potrebbe verificarsi un problema relativo a Power BI Desktop, questa sezione contiene soluzioni o suggerimenti per risolvere gli eventuali problemi riscontrati. 

### <a name="using-command-line-options-during-installation"></a>Uso delle opzioni da riga di comando durante l'installazione 

Quando si installa Power BI Desktop, è possibile impostare le proprietà e le opzioni usando le opzioni da riga di comando. Queste impostazioni sono particolarmente utili per gli amministratori che gestiscono o facilitano l'installazione di Power BI Desktop in più organizzazioni. Queste opzioni si applicano alle installazioni di pacchetti con estensione msi ed exe. 


|Opzione da riga di comando  |Comportamento  |
|---------|---------|
|-q, -quiet, -s, -silent     |Installazione invisibile all'utente         |
|-passive     |Visualizza solo l'indicatore di stato durante l'installazione         |
|-norestart     |Disattiva il requisito di riavvio del computer         |
|-forcerestart     |Riavvia il computer dopo l'installazione senza chiedere conferma         |
|-promptrestart     |Chiede conferma all'utente se è necessario riavviare il computer (impostazione predefinita)         |
|-l<>, -log<>     |Registra l'installazione in un file specifico, con il file definito in <>         |
|-uninstall     |Disinstalla Power BI Desktop         |
|-repair     |Ripristina l'installazione (o esegue l'installazione se il pacchetto non è installato)         |
|-package, -update     |Installa Power BI Desktop (impostazione predefinita, purché l'opzione -uninstall o -repair non sia specificata)         |

È anche possibile usare i parametri seguenti, specificati con la sintassi *proprietà = valore*:

|Parametro  |Significato  |
|---------|---------|
|ACCEPT_EULA     |Richiede un valore pari a 1 per accettare automaticamente le condizioni di licenza         |
|ENABLECXP     |Con il valore 1 si esegue la registrazione ad Analisi utilizzo software, il programma per l'acquisizione dei dati di telemetria sull'utilizzo del prodotto         |
|INSTALLDESKTOPSHORTCUT     |Il valore 1 aggiunge un collegamento al desktop         |
|INSTALLLOCATION     |Percorso file in cui si vuole eseguire l'installazione         |
|LANGUAGE     |Codice delle impostazioni locali, ad esempio en-US, de-DE, pr-BR, per forzare la lingua predefinita dell'applicazione. Se non si specifica la lingua, Power BI Desktop visualizza quella del sistema operativo Windows. È possibile modificare questa impostazione nella finestra di dialogo **Opzioni**.         |
|REG_SHOWLEADGENDIALOG     |Il valore 0 disabilita la visualizzazione della finestra di dialogo che appare prima dell'accesso a Power BI Desktop.         |
|DISABLE_UPDATE_NOTIFICATION     |Il valore 1 disabilita le notifiche di aggiornamento.         |


È ad esempio possibile eseguire Power BI Desktop con le opzioni e i parametri seguenti per l'installazione senza interfaccia utente in lingua tedesca: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Installazione di Power BI Desktop su computer remoti

Se si distribuisce Power BI Desktop agli utenti con uno strumento che richiede un file di installazione Windows (con estensione msi), è possibile estrarre quest'ultimo dal file di installazione con estensione exe di Power BI Desktop. Usare uno strumento di terze parti, ad esempio WiX Toolset.

> [!NOTE]
> In quanto prodotto di terze parti, le opzioni di WiX Toolset possono subire modifiche senza preavviso. Per informazioni aggiornate, consultare la documentazione del prodotto e contattare la lista di distribuzione degli utenti per assistenza.

1. Nel computer in cui è stato scaricato il programma di installazione di Power BI Desktop, installare la versione più recente di [WiX Toolset](https://wixtoolset.org/).
2. Aprire una finestra della riga di comando come amministratore e passare alla cartella in cui è stato installato WiX Toolset.
3. Eseguire il comando seguente: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Ad esempio:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    La cartella di output contiene una cartella denominata *AttachedContainer* che include i file con estensione msi.

L'aggiornamento di un'installazione da un file con estensione exe a un file con estensione msi estratto da un file con estensione exe non è supportato.   Per eseguire l'aggiornamento, è prima necessario disinstallare la versione precedente di Power BI Desktop in uso.

### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemi nell'uso delle versioni precedenti di Power BI Desktop

Se si usa una versione obsoleta di Power BI Desktop, è possibile che venga restituito un messaggio di errore simile al seguente: 

*Non è stato possibile ripristinare il database salvato nel modello* 

In genere l'aggiornamento alla versione corrente di Power BI Desktop risolve il problema.

### <a name="disabling-notifications"></a>Disabilitazione delle notifiche
È consigliabile eseguire l'aggiornamento alla versione più recente di Power BI Desktop per sfruttare i miglioramenti apportati alle funzionalità, alle prestazioni e alla stabilità e le altre novità. Alcune organizzazioni potrebbero preferire che gli utenti non eseguano l'aggiornamento a ogni nuova versione. È possibile disabilitare le notifiche modificando il Registro di sistema seguendo questa procedura:

1. Nell'editor del Registro di sistema passare alla chiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Creare una nuova voce **REG_DWORD** nella chiave con il nome seguente: **DisableUpdateNotification**.
3. Impostare il valore della nuova voce su **1**.
4. Riavviare il computer per rendere effettiva questa modifica.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop viene caricato con una schermata parziale

In alcune circostanze, tra cui determinate configurazioni di risoluzione dello schermo, Power BI Desktop potrebbe eseguire il rendering del contenuto con grandi aree nere. Questo problema è in genere dovuto ad aggiornamenti recenti del sistema operativo che influiscono sulla modalità di rendering degli elementi e non è un risultato diretto del modo in cui Power BI Desktop presenta il contenuto. Per risolverlo, seguire questa procedura:

1. Fare clic su **Start** e digitare *sfocate* nella barra di ricerca visualizzata.
2. Nella finestra di dialogo visualizzata selezionare l'opzione **Risolvere i problemi delle app che sono sfocate.**
3. Riavviare Power BI Desktop.

È possibile che questo problema venga risolto dopo il rilascio degli aggiornamenti successivi di Windows. 
 

## <a name="next-steps"></a>Passaggi successivi
Dopo aver installato Power BI Desktop, vedere i contenuti seguenti per imparare a svolgere rapidamente le attività iniziali:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query in Power BI Desktop](desktop-query-overview.md)
* [Origini di dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Data shaping e combinazione di dati in Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)   

