---
title: Ottenere Power BI Desktop
description: Scaricare e installare Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 08/15/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: davidi
ms.openlocfilehash: 213e3f8665c6e034719130d6b12a37877377266a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="get-power-bi-desktop"></a>Ottenere Power BI Desktop
**Power BI Desktop** consente di creare query, modelli e report avanzati per la visualizzazione dei dati. Con **Power BI Desktop**, è possibile creare modelli di dati, creare report e condividere il proprio lavoro pubblicandolo nel servizio Power BI.  Il download di **Power BI Desktop** è gratuito.

È possibile ottenere **Power BI Desktop** in due modi, ognuno dei quali viene descritto nelle sezioni seguenti:

* **Download** diretto (pacchetto MSI da scaricare e installare in questo computer)
* Installazione come app da **Windows Store**

Con entrambi gli approcci si otterrà la versione più recente di **Power BI Desktop** nel computer, ma esistono alcune differenze che vale la pena osservare e che vengono descritte nelle sezioni seguenti.

## <a name="download-power-bi-desktop"></a>Scarica Power BI Desktop
Per scaricare la versione più recente di **Power BI Desktop** è possibile selezionare l'icona di download nell'angolo in alto a destra del servizio Power BI e selezionare **Power BI Desktop**.

![](media/desktop-get-the-desktop/getpbid_downloads.png)

È anche possibile scaricare la versione più recente di Power BI Desktop dalla seguente pagina di download:

* [**Download di Power BI Desktop** (entrambe le versioni a 32 e a 64 bit)](https://powerbi.microsoft.com/desktop).
  
  [![](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Indipendentemente dal download scelto, dopo aver scaricato **Power BI Desktop** verrà chiesto di eseguire il file di installazione:

![](media/desktop-get-the-desktop/getpbid_3.png)

**Power BI Desktop** viene installato come applicazione ed eseguito sul desktop.

![](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> L'installazione della versione scaricata (MSI) e della versione presente in **Windows Store** di **Power BI Desktop** nello stesso computer (anche detta installazione *side-by-side*) non è supportata.
> 
> 

## <a name="install-as-an-app-from-the-windows-store"></a>Installazione come app da Windows Store
È possibile ottenere **Power BI Desktop** anche da Windows Store usando il collegamento seguente:

* [Installare **Power BI Desktop** da **Windows Store**](http://aka.ms/pbidesktopstore)

![](media/desktop-get-the-desktop/getpbid_04.png)

Esistono alcuni vantaggi nell'ottenere **Power BI Desktop** da Windows Store:

* **Aggiornamenti automatici**: Windows scarica la versione più recente automaticamente in background non appena è disponibile, per cui la versione usata è sempre aggiornata.
* **Download più piccoli**: **Windows Store** assicura che vengano scaricati nel computer solo i componenti modificati in ogni aggiornamento, in modo da ottenere download più piccoli per ogni aggiornamento.
* **Non sono necessari privilegi di amministratore**: per scaricare direttamente il pacchetto MSI e installarlo, è necessario essere un amministratore affinché l'installazione venga completata correttamente. Quando si ottiene **Power BI Desktop** da Windows Store, il privilegio di amministratore *non* è necessario.
* **Roll-out IT abilitato**: la versione di **Windows Store** può essere distribuita (*roll-out*) più facilmente a tutti gli utenti dell'organizzazione ed è possibile rendere disponibile **Power BI Desktop** tramite **Microsoft Store per le aziende**.
* **Rilevamento lingua**: la versione di **Windows Store** include tutte le lingue supportate e controlla la lingua usata nel computer a ogni avvio. Questo influisce anche sulla localizzazione dei modelli creati in **Power BI Desktop**. Ad esempio, le gerarchie di date predefinite corrisponderanno alla lingua usata da **Power BI Desktop** quando viene creato il file con estensione pbix.

Esistono alcune considerazioni e limitazioni per l'installazione di **Power BI Desktop** da Windows Store, che includono quanto segue:

* Se si usa il connettore SAP, potrebbe essere necessario spostare i file del driver SAP per la cartella *Windows\System32*.

> [!NOTE]
> L'installazione della versione scaricata (MSI) e della versione presente in **Windows Store** di **Power BI Desktop** nello stesso computer (anche detta installazione *side-by-side*) non è supportata.
> 
> [!NOTE]
> La versione Server di report di Power BI di **Power BI Desktop** è un'installazione separata e diversa rispetto alle versioni illustrate in questo articolo. Per informazioni sulla versione Server di report di **Power BI Desktop**, vedere l'articolo [Avvio rapido: Creare un report di Power BI per il Server di report di Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Uso di Power BI Desktop
Quando si avvia **Power BI Desktop** viene visualizzata una *schermata iniziale*.

![](media/desktop-get-the-desktop/getpbid_05.png)

Se si usa per la prima volta **Power BI Desktop**, ovvero se l'installazione non è un aggiornamento, verrà richiesta la compilazione di un modulo e la risposta ad alcune domande o sarà necessario accedere al **servizio Power BI** per poter continuare.

Da qui è possibile iniziare a creare modelli di dati o report, quindi condividerli con altri utenti nel servizio Power BI. Vedere i collegamenti **Altre informazioni** alla fine di questo articolo per i collegamenti a guide sulle attività iniziali in **Power BI Desktop**.

## <a name="minimum-requirements"></a>Requisiti minimi
Di seguito sono elencati i requisiti minimi per l'esecuzione di **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 o versioni successive
* .NET 4.5
* Internet Explorer 9 o versioni successive
* **Memoria (RAM):** almeno 1 GB disponibile, 1,5 GB o più consigliati.
* **Visualizzazione:** almeno 1440 x 900 o 1600 x 900 (16:9) consigliato. Risoluzioni inferiori, ad esempio 1024 x 768 o 1280 x 800 non sono consigliate, perché alcuni controlli (ad esempio la chiusura della schermata iniziale) vengono visualizzati oltre tali risoluzioni.
* **Impostazioni dello schermo di Windows:** se le impostazioni di visualizzazione sono configurate per la modifica delle dimensioni di testo, app e altri elementi fino a un valore superiore al 100%, è possibile che non si riesca a visualizzare alcune finestre di dialogo che devono essere chiuse o a cui occorre rispondere per poter continuare a usare **Power BI Desktop**. Se si verifica questo problema, controllare le **Impostazioni dello schermo** passando a **Impostazioni > Sistema > Schermo** in Windows, quindi usare il dispositivo di scorrimento per ripristinare il valore 100% per le impostazioni di visualizzazione.
* **CPU:** 1 gigahertz (GHz) o più veloce processore x86o x 64 bit consigliato.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver installato **Power BI Desktop**, il contenuto seguente consente di svolgere rapidamente le attività iniziali:

* [Introduzione a Power BI Desktop](desktop-getting-started.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)   

