---
title: Power BI Gateway - Personal
description: Power BI Gateway - Personal
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Gateways
ms.openlocfilehash: 06ed973b3b16f5ac8ed8bef484d48af994a4e5f2
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
> [!NOTE]
> Questa è una nuova versione del gateway personale per Power BI, chiamato **gateway dati locale (modalità personale)**. Il seguente articolo descrive la versione precedente del gateway personale, chiamato **Power BI Gateway - Personal**, che verrà ritirato e cesserà di funzionare dopo il 31 luglio 2017. Per informazioni sulla nuova versione del gateway personale, comprese le istruzioni su come installare la nuova versione, vedere l'articolo [**Gateway dati locale (modalità personale)**](service-gateway-personal-mode.md).
> 
> 

**Power BI Gateway - Personal** funge da bridge per offrire un trasferimento dei dati rapido e sicuro tra il servizio Power BI e le origini dati locali che supportano l'[aggiornamento](refresh-data.md). L'obiettivo di questo articolo è fornire informazioni approfondite sul funzionamento del gateway e aiutare a determinare se è necessario installarne uno. È anche disponibile questo [video utile](https://www.youtube.com/watch?v=de58vROLqZI) sul gateway personale. 

Il gateway viene installato ed eseguito come servizio nel computer. Come servizio, viene eseguito con un account di Windows specificato durante la configurazione. In alcuni casi, il gateway viene eseguito come applicazione. Questi aspetti verranno approfonditi più avanti.

Quando Power BI aggiorna i dati provenienti da un'origine dati locale, il gateway verifica che l'account di Power BI abbia le autorizzazioni corrette per connettersi ai dati dell'origine ed eseguire query su questi dati.

Il trasferimento dei dati tra Power BI e il gateway viene protetto con il [bus di servizio di Azure](http://azure.microsoft.com/documentation/services/service-bus/). Il bus di servizio crea un canale sicuro tra il servizio Power BI e il computer. Dato che il gateway fornisce questa connessione sicura, in genere non è necessario aprire una porta nel firewall.

Prima di esplorare in dettaglio il gateway, ecco alcuni termini usati in Power BI:

Un *set di dati* è costituito dai dati caricati nel servizio Power BI da un'origine dati online o locale. Un set di dati viene creato quando si usa Recupera dati per connettersi ai dati e caricarli. I set di dati sono visualizzati nel riquadro Area di lavoro personale dell'area di lavoro di Power BI nel browser. Quando si creano report e si aggiungono sezioni ai dashboard, i dati vengono visualizzati dai set di dati.

Un'*origine dati* è l'elemento da cui provengono effettivamente i dati caricati in un set di dati. Può trattarsi di un database, un foglio di lavoro di Excel, un servizio Web o altro. Con le cartelle di lavoro di Excel è possibile creare un semplice foglio di lavoro con righe di dati, che viene considerato un'origine dati. È anche possibile usare Power Query o Power Pivot in Excel per connettersi a dati di origini dati online e locali ed eseguire query su questi dati, tutto nella stessa cartella di lavoro. Con Power BI Desktop è possibile usare Recupera dati per connettersi ai dati di origini dati online e locali ed eseguire query su questi dati.

Il gateway personale viene installato tramite il gateway dati locale. È possibile scaricarlo alla [pagina Power BI Gateway](https://powerbi.microsoft.com/gateway/).

## <a name="do-i-need-a-gateway"></a>È necessario un gateway?
Prima di installare un gateway, è importante determinare se sia davvero necessario. La risposta dipende dalle origini dati:

### <a name="on-premises-data-sources"></a>Origini dati locali
Un gateway personale *è necessario* per aggiornare i set di dati che recuperano dati da un'origine dati locale supportata nell'organizzazione.

Con un gateway, le opzioni AGGIORNA ORA e PIANIFICA AGGIORNAMENTI sono supportate per i set di dati caricati da:

* Cartelle di lavoro di Microsoft Excel 2013 (o versioni successive) in cui viene usato Power Query o Power Pivot per connettersi ai dati provenienti da un'origine dati locale supportata ed eseguire query su questi dati. Tutte le origini dati visualizzate in Recupera dati esterni in Power Query o Power Pivot supportano l'aggiornamento, ad eccezione del file Hadoop (HDFS) e di Microsoft Exchange.
* File di Microsoft Power BI Desktop in cui viene usato Recupera dati per connettersi ai dati provenienti da un'origine dati locale supportata ed eseguire query su questi dati. Tutte le origini dati visualizzate in Recupera dati supportano l'aggiornamento, ad eccezione del file Hadoop (HDFS) e di Microsoft Exchange.

### <a name="online-data-sources"></a>Origini dati online
Un gateway *è richiesto solo* se si usa la funzione [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx). In altri casi, un gateway *non* è necessario per aggiornare i set di dati che recuperano dati solo da un'origine dati online.

> [!NOTE]
> Se si usa la funzione [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), è necessario un gateway se il set di dati o il report è stato ripubblicato dopo il 18 novembre 2016.
> 
> 

Le opzioni AGGIORNA ORA e PIANIFICA AGGIORNAMENTI sono supportate senza un gateway per i set di dati caricati da:

* Pacchetti di contenuto da origini dati online (pacchetti di contenuto\\per servizi). Per impostazione predefinita, i set di dati provenienti da pacchetti di contenuto vengono automaticamente aggiornati una volta al giorno, ma è possibile aggiornarli anche manualmente o configurare una pianificazione degli aggiornamenti.
* Cartelle di lavoro di Microsoft Excel 2013 (o versioni successive) in cui viene usato Power Query o Power Pivot per connettersi ai dati provenienti da un'origine dati online ed eseguire query su questi dati.
* File di Microsoft Power BI Desktop in cui viene usato Recupera dati per connettersi ai dati provenienti da un'origine dati online ed eseguire query su questi dati.

**Domanda:** Cosa succede se la cartella di lavoro di Excel o il file di Power BI Desktop recupera dati da origini dati sia online sia locali?

**Risposta:** *è* necessario un gateway. Occorre installare e configurare un gateway per poter aggiornare i dati provenienti da origini dati locali.

**Domanda:** Cosa succede se la cartella di lavoro di Excel contiene solo righe di dati immessi manualmente?**

**Risposta:** *non è* necessario un gateway. Occorre installare e configurare un gateway solo se la cartella di lavoro usa Power Query o Power Pivot per eseguire query sui dati e caricarli nel modello di dati da un'origine dati locale supportata.

## <a name="setting-up-a-gateway-for-the-first-time"></a>Configurazione di un gateway per la prima volta
La configurazione di un gateway per la prima volta è un processo in tre passaggi:

1. Download e installazione di un gateway
2. Configurazione del gateway
3. Accesso alle origini dati in Power BI

Di seguito viene descritto ogni passaggio.

### <a name="download-and-install-a-gateway"></a>Download e installazione di un gateway
> [!NOTE]
> Questa è una nuova versione del gateway personale per Power BI, chiamato **gateway dati locale (modalità personale)**. Il seguente articolo descrive la versione precedente del gateway personale, chiamato **Power BI Gateway - Personal**, che verrà ritirato e cesserà di funzionare dopo il 31 luglio 2017. Per informazioni sulla nuova versione del gateway personale, comprese le istruzioni su come installare la nuova versione, vedere l'articolo [**Gateway dati locale (modalità personale)**](service-gateway-personal-mode.md).
> 
> 

Quando si fa clic per la prima volta su AGGIORNA ORA o PIANIFICA AGGIORNAMENTI, viene richiesto di installare un gateway. In alternativa, per scaricare il gateway, selezionare **Gateway dati** nel menu Download. Scaricare il [gateway dati locale](http://go.microsoft.com/fwlink/?LinkID=820925).

Sarà opportuno selezionare **Gateway personale** invece di **Gateway dati locale** per avere un gateway personale.

L'installazione di un gateway è piuttosto semplice. Basta selezionare un percorso di installazione e quindi leggere e accettare il contratto di licenza come per ogni altra applicazione. È comunque necessario tenere presenti alcuni aspetti. In particolare, il tipo di computer in cui si installa il gateway e il tipo di account con cui si è connessi a Windows nel computer.

> [!NOTE]
> Il gateway deve poter accedere all'origine dati. Se il computer non può connettersi all'origine dati, provare a installare un [gateway dati locale](service-gateway-onprem.md) in un computer che abbia accesso all'origine dati. Un esempio può essere SQL Server installato in una macchina virtuale (VM) ospitata in Azure. Il computer può non avere accesso alla macchina virtuale. È possibile invece installare il gateway dati locale nella macchina virtuale e configurare l'origine dati all'interno del servizio Power BI.
> 
> 

### <a name="computer-type"></a>Tipo di computer
Il tipo di computer in cui viene installato il gateway è importante.

> [!NOTE]
> Il gateway personale è supportato solo nei sistemi operativi Windows a 64 bit.
> 
> 

Computer portatile: perché venga eseguito un aggiornamento pianificato, il gateway deve essere operativo. I computer portatili sono in genere spenti o in modalità di sospensione per la maggior parte del tempo. Se si installa il gateway in un portatile, assicurarsi di impostare gli orari di aggiornamento pianificati nei momenti in cui il portatile è operativo. In caso contrario, l'aggiornamento non verrà provato di nuovo fino al momento del successivo aggiornamento pianificato.

Computer desktop: nessun problema di rilievo. È sufficiente assicurarsi che il computer e il gateway siano operativi negli orari definiti per gli aggiornamenti pianificati. Molti computer desktop entrano in modalità di sospensione, ma in questo caso l'aggiornamento pianificato non può essere eseguito.

Una volta installato un gateway, non è necessario installarne un altro. Un gateway è sufficiente per qualsiasi numero di set di dati supportati. Inoltre, non è necessario installare il gateway nello stesso computer da cui vengono caricati la cartella di lavoro e i file di Power BI Desktop. Ecco un esempio: si potrebbe avere una cartella di lavoro di Excel connessa a un'origine dati SQL Server nell'organizzazione. È stato usato Recupera dati in Power BI per caricare la cartella di lavoro dal computer portatile. È disponibile anche un computer desktop che viene lasciato sempre operativo e in cui è stato installato e configurato un gateway. In Power BI è stato effettuato l'accesso alle origini dati ed è stata configurata una pianificazione dell'aggiornamento per il set di dati.  Al momento di un aggiornamento pianificato, Power BI stabilisce una connessione sicura al gateway installato nel computer desktop. Si connette quindi in modo sicuro alle origini dati per ottenere gli aggiornamenti. Per l'aggiornamento, non vi è comunicazione con la cartella di lavoro originale caricata dal computer portatile.

> [!NOTE]
> È possibile installare il gateway personale e il gateway aziendale nello stesso computer.
> 
> 

### <a name="windows-account"></a>Account di Windows
Quando si installa il gateway, per l'accesso al computer viene usato l'account di Windows. Il tipo di autorizzazioni dell'account di Windows influisce sul modo in cui il gateway viene installato ed eseguito in Windows.

Quando si è connessi a Windows:

|  | Con autorizzazioni di amministratore | Senza autorizzazioni di amministratore |
| --- | --- | --- |
| **Power BI Gateway - Personal viene eseguito come** |Servizio |Applicazione |
| **Aggiornamento pianificato** |Se il computer è acceso e il servizio gateway è in esecuzione, non è necessario avere effettuato l'accesso all'ora dell'aggiornamento pianificato. |È necessario avere effettuato l'accesso al computer all'ora dell'aggiornamento pianificato. |
| **Modifica della password dell'account di Windows** |È necessario modificare la password nel servizio gateway. Se la password dell'account usata dal gateway non è più valida, l'aggiornamento avrà esito negativo. |Il gateway viene sempre eseguito con l'account e la password usati per l'accesso. Se non è stato effettuato l'accesso a Windows, il gateway non sarà in esecuzione e l'aggiornamento non riuscirà. |

### <a name="configure-the-gateway"></a>Configurazione del gateway
Al termine dell'Installazione guidata, viene richiesto di avviare la Configurazione guidata. La configurazione di un gateway è piuttosto semplice. È necessario accedere a Power BI dalla procedura guidata. Questa operazione è necessaria perché la procedura guidata possa stabilire una connessione con l'account Power BI nel servizio Power BI.

Se per l'accesso a Windows è stato usato un account con autorizzazioni di amministratore, verrà richiesto di immettere le credenziali dell'account di Windows. È possibile specificare un account di Windows diverso, ma tenere presente che le autorizzazioni determinano il modo in cui il gateway viene eseguito. Il servizio del gateway verrà eseguito usando questo account.

### <a name="sign-in-to-data-sources"></a>Accesso alle origini dati in Power BI
Al termine della Configurazione guidata e quando il gateway è operativo, è necessario specificare un tipo di autenticazione e accedere a ognuna delle origini dati del set di dati. Questo passaggio deve essere completato in Power BI.

![](media/personal-gateway/pg_dataset_settings_signin.png)

È sufficiente specificare un tipo di autenticazione e accedere a un'origine dati una sola volta. Accedere dalla sezione **Gestisci origini dati** nella schermata Impostazioni di un set di dati. In caso di più origini dati, è necessario accedere a ognuna. Il gateway determina un tipo di autenticazione predefinito a seconda dell'origine dati. Benché nella maggior parte dei casi si tratti dell'autenticazione di Windows, a volte l'origine dati potrebbe richiedere un tipo di autenticazione diverso. In caso di dubbi, rivolgersi all'amministratore dell'origine dati.

## <a name="up-and-running"></a>Il gateway è operativo
Quando il gateway è operativo, è possibile fare clic su PIANIFICA AGGIORNAMENTI per un set di dati, per il quale viene quindi visualizzata la pagina Impostazioni.

![](media/personal-gateway/pg_awintsales_settings.png)

La pagina mostra le opzioni seguenti:

1. Stato aggiornamento: indica se l'aggiornamento è riuscito e la data e l'ora del successivo aggiornamento pianificato.
2. **Gateway**: indica se un gateway è installato e online. Se un gateway è installato ma non è online, le impostazioni Gestisci origini dati e Pianifica aggiornamenti sono disabilitate.
3. **Gestisci origini dati** : mostra le origini dati a cui si connette il set di dati. È possibile accedere o modificare il tipo di autenticazione. È necessario accedere a ogni origine dati solo una volta.
4. **Pianifica aggiornamento** : qui è possibile configurare le impostazioni di pianificazione di un aggiornamento. Se il gateway non è online, queste impostazioni saranno disabilitate.
5. Inviami il messaggio di notifica di aggiornamento non riuscito: questa opzione, selezionata per impostazione predefinita, invia un messaggio di posta elettronica se un aggiornamento pianificato non riesce.

## <a name="updating-your-windows-account-password"></a>Aggiornamento della password dell'account di Windows
Se durante l'installazione del gateway per accedere è stato usato un account di Windows con privilegi di amministratore, il gateway viene eseguito come servizio usando l'account di Windows specificato nella Configurazione guidata. Nella maggior parte dei casi, si tratta dello stesso account di Windows usato per accedere al computer. Quando si modifica la password dell'account di Windows, è necessario modificarla anche nel gateway, altrimenti il servizio potrebbe non essere eseguito e l'aggiornamento non riesce. Per modificare la password dell'account di Windows per il gateway, selezionare l'icona del gateway personale sulla barra delle applicazioni del desktop oppure in App.

![](media/personal-gateway/pg_programicon.png)

Da qui è possibile aggiornare la password e verificare lo stato di connessione del gateway.

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>Porte
Il gateway comunica sulle porte in uscita: TCP 443 (predefinita), 5671, 5672, da 9350 a 9354.  Il gateway non richiede porte in entrata.

| Nomi di dominio | Porte in uscita | Descrizione |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Listener in Inoltro del bus di servizio su TCP (è richiesta la porta 443 per l'acquisizione del token di Controllo di accesso) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| login.windows.net |443 |HTTPS |

Per creare un elenco di indirizzi IP consentiti anziché di domini, è possibile scaricare e usare l'elenco di intervalli IP del data center di Microsoft Azure. [Download](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>Passaggi successivi
[Gateway dati locale (modalità personale) - La nuova versione del gateway personale](service-gateway-personal-mode.md)
[Configurazione delle impostazioni proxy per il gateway dati locale](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

