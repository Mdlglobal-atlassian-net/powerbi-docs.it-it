---
title: Configurare l'aggiornamento pianificato
description: Questo articolo descrive la procedura per selezionare un gateway e configurare l'aggiornamento pianificato.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 7eb09f92be6c49756513b095afbdb9f451753d30
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54289419"
---
# <a name="configuring-scheduled-refresh"></a>Configurazione dell'aggiornamento pianificato

>[!NOTE]
>Dopo due mesi di inattività, l'aggiornamento pianificato sul set di dati viene messo in pausa. Vedere la sezione [*Pianifica aggiornamento*](#schedule-refresh) presente più avanti in questo articolo per saperne di più.
> 
> 

Se il set di dati supporta l'aggiornamento pianificato usando i comandi Aggiorna ora e Pianifica aggiornamenti, ci sono alcuni requisiti e impostazioni importanti per la corretta esecuzione dell'aggiornamento. Si tratta delle opzioni **Connessione gateway**, **Credenziali origine dati** e **Pianifica aggiornamenti**, che verranno ora analizzate più in dettaglio.

Verranno descritte le opzioni disponibili sia per [Power BI Gateway - Personal](service-gateway-personal-mode.md) che per il [gateway dati locale](service-gateway-onprem.md).

Per visualizzare la schermata Pianifica aggiornamenti, è possibile eseguire le operazioni seguenti.

1. Selezionare i **puntini di sospensione (...)** accanto a un set di dati elencato in **Set di dati**.
2. Selezionare **Pianifica aggiornamenti**.
   
    ![](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Connessione gateway
Le opzioni visualizzate variano a seconda del fatto che il gateway online e disponibile sia personale o aziendale.

Se non è disponibile alcun gateway, l'opzione **Impostazioni gateway** è disabilitata. Verrà anche visualizzato un messaggio che indica come installare il gateway personale.

![](media/refresh-scheduled-refresh/gateway-not-configured.png)

Se è stato configurato un gateway personale, sarà possibile selezionarlo, se è online. Se non è disponibile, risulterà offline.

![](media/refresh-scheduled-refresh/gateway-connection.png)

Si può anche selezionare il gateway aziendale, se disponibile. Un gateway aziendale è disponibile solo il proprio account è elencato nella scheda Utenti dell'origine dati configurata per un determinato gateway.

## <a name="data-source-credentials"></a>Credenziali origine dati
### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
Se si usa il gateway personale per aggiornare i dati, è necessario specificare le credenziali usate per connettersi all'origine dati back-end. Se si è connessi a un pacchetto di contenuto da un servizio online, le credenziali immesse per la connessione verranno usate anche per l'aggiornamento pianificato.

![](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

L'accesso alle origini dati viene richiesto solo al primo aggiornamento del set di dati. Una volta immesse, le credenziali vengono mantenute con il set di dati.

> [!NOTE]
> Se per alcuni metodi di autenticazione la password usata per accedere a un'origine dati scade o viene modificata, è necessario modificarla anche per l'origine dati in Credenziali origine dati.
> 
> 

In caso di errori, il problema in genere è dovuto al fatto che il gateway è offline perché non è stato in grado di accedere a Windows e avviare il servizio oppure Power BI non è stato in grado di accedere alle origini dati per eseguire una query per i dati aggiornati. Se l'aggiornamento non riesce, controllare le impostazioni del set di dati. Se il servizio gateway è offline, l'errore viene visualizzato nello stato del gateway. Se Power BI non può accedere alle origini dati, l'errore viene visualizzato in Credenziali origine dati.

### <a name="on-premises-data-gateway"></a>Gateway dati locale
Se si usa il gateway dati locale per aggiornare i dati, non è necessario specificare le credenziali poiché vengono definite per l'origine dati dall'amministratore del gateway.

![](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Quando ci si connette a SharePoint locale per l'aggiornamento dei dati, Power BI supporta solo i meccanismi di autenticazione *Anonymous* (Anonimo), *Basic* (Di base) e *Windows (NTLM/Kerberos)*. Power BI non supporta *ADFS* o qualsiasi meccanismo di *autenticazione basata su form* per l'aggiornamento dei dati di origini dati di SharePoint locale.
> 
> 

## <a name="schedule-refresh"></a>Pianifica aggiornamenti
La sezione relativa all'aggiornamento pianificato viene usata per definire la frequenza e gli orari per l'aggiornamento del set di dati. Alcune origini dati non richiedono che sia presente un gateway per essere disponibili per la configurazione. Altre, invece, lo richiedono.

Per configurare le impostazioni, è necessario impostare il dispositivo di scorrimento **Mantieni aggiornati i dati** su **Sì**.

> [!NOTE]
> Il servizio Power BI mira ad avviare l'aggiornamento dei dati entro **15 minuti** dall'orario di aggiornamento programmato.
> 
> 

![](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Dopo due mesi di inattività, l'aggiornamento pianificato sul set di dati viene messo in pausa. Un set di dati viene considerato inattivo quando nessun utente ha visitato un qualsiasi dashboard o report integrato nel set di dati. A quel punto, al proprietario del set di dati viene inviata un'e-mail in cui viene indicato che l'aggiornamento pianificato è stato messo in pausa e la pianificazione dell'aggiornamento per il set di dati viene visualizzata come **disabilitata**. Per riprendere la pianificazione dell'aggiornamento, è sufficiente accedere a un qualsiasi dashboard o report integrato nel set di dati.
> 
> 

## <a name="whats-supported"></a>Che cosa è supportato?
Alcuni set di dati sono supportati in gateway diversi per l'aggiornamento pianificato. Ecco un riferimento per comprendere cosa è disponibile.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
**Power BI Desktop**

* Tutte le origini dati online visualizzate in Recupera dati ed Editor di query di Power BI Desktop.
* Tutte le origini dati locali visualizzate in Recupera dati ed Editor di query di Power BI Desktop, tranne il file Hadoop (HDFS) e Microsoft Exchange.

**Excel**

> [!NOTE]
> In Excel 2016 e versioni successive Power Query viene elencato nella sezione Dati della barra multifunzione in Recupera e trasforma.
> 
> 

* Tutte le origini dati online visualizzate in Power Query.
* Tutte le origini dati locali visualizzate in Power Query, ad eccezione del file Hadoop (HDFS) e di Microsoft Exchange.
* Tutte le origini dati online visualizzate in Power Pivot.\*
* Tutte le origini dati locali visualizzate in Power Pivot, ad eccezione del file Hadoop (HDFS) e di Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>Risoluzione dei problemi
A volte, l'aggiornamento dei dati non funziona come previsto. In genere si tratta di un problema relativo al gateway. Consultare gli articoli sulla risoluzione dei problemi del gateway per individuare gli strumenti utili e i problemi noti.

[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)

[Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Passaggi successivi
[Aggiornamento dei dati in Power BI](refresh-data.md)  
[Power BI Gateway - Personale](service-gateway-personal-mode.md)  
[Gateway dati locale](service-gateway-onprem.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

